<!--
SPDX-FileCopyrightText: 2020 - 2024 MDAD project contributors
SPDX-FileCopyrightText: 2020 - 2024 Slavi Pantaleev
SPDX-FileCopyrightText: 2020 Aaron Raimist
SPDX-FileCopyrightText: 2020 Chris van Dijk
SPDX-FileCopyrightText: 2020 Dominik Zajac
SPDX-FileCopyrightText: 2020 Mickaël Cornière
SPDX-FileCopyrightText: 2022 François Darveau
SPDX-FileCopyrightText: 2022 Julian Foad
SPDX-FileCopyrightText: 2022 Warren Bailey
SPDX-FileCopyrightText: 2023 Antonis Christofides
SPDX-FileCopyrightText: 2023 Felix Stupp
SPDX-FileCopyrightText: 2023 Julian-Samuel Gebühr
SPDX-FileCopyrightText: 2023 Pierre 'McFly' Marty
SPDX-FileCopyrightText: 2024 - 2025 Suguru Hirahara

SPDX-License-Identifier: AGPL-3.0-or-later
-->

# Setting up Mosquitto

This is an [Ansible](https://www.ansible.com/) role which installs [Mosquitto](https://mosquitto.org/) to run as a [Docker](https://www.docker.com/) container wrapped in a systemd service.

Mosquitto is an open source [MQTT](https://en.wikipedia.org/wiki/MQTT) broker.

See the project's [documentation](https://github.com/eclipse-mosquitto/mosquitto/blob/master/README.md) to learn what Mosquitto does and why it might be useful to you.

## Adjusting the playbook configuration

To enable Mosquitto with this role, add the following configuration to your `vars.yml` file.

```yaml
########################################################################
#                                                                      #
# mosquitto                                                            #
#                                                                      #
########################################################################

mosquitto_enabled: true

########################################################################
#                                                                      #
# /mosquitto                                                           #
#                                                                      #
########################################################################
```

### Change the MQTT port (optional)

If you need to change the MQTT port, add the following configuration to your `vars.yml` file (adapt to your needs).

```yaml
mosquitto_container_mqtt_host_bind_port: "1884"
```

## Installing

After configuring the playbook, run the installation command of your playbook as below:

```sh
ansible-playbook -i inventory/hosts setup.yml --tags=setup-all,start
```

If you use the MASH playbook, the shortcut commands with the [`just` program](https://github.com/mother-of-all-self-hosting/mash-playbook/blob/main/docs/just.md) are also available: `just install-all` or `just setup-all`

## Usage

After running the command for installation, you can start to send and subscribe to MQTT topics. Use port `1883` and the servers IP or any domain you configured to point at this server.

You can run the following command to create a user:

```sh
ansible-playbook -i inventory/hosts setup.yml --tags=mosquitto-add-user --extra-vars=username=<username> --extra-vars=password=<password>
```

For the setting to take effect, you need to restart the container.

## Troubleshooting

### Check the service's logs

You can find the logs in [systemd-journald](https://www.freedesktop.org/software/systemd/man/systemd-journald.service.html) by logging in to the server with SSH and running `journalctl -fu mosquitto` (or how you/your playbook named the service, e.g. `mash-mosquitto`).

## Alternatives

[rumqttd](https://github.com/bytebeamio/rumqtt) is another high performance, embeddable MQTT broker. The role for it is available at [this repository](https://github.com/mother-of-all-self-hosting/ansible-role-rumqttd).
