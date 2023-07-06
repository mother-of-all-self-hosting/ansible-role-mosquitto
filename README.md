# Mosquitto Ansible Role


[Mosquitto](https://mosquitto.org/) is an open source [MQTT](https://en.wikipedia.org/wiki/MQTT) broker. This role helps you to set up mosquitto:

- with everything run in [Docker](https://www.docker.com/) containers
- powered by [the official mosquitto container image](https://hub.docker.com/r/_/eclipse-mosquitto/)


## Installing

To configure and install mosquitto on your own server(s), you should use a playbook like [Mother of all self-hosting](https://github.com/mother-of-all-self-hosting/mash-playbook) or write your own.

## Configuring this role for your playbook

```yaml
mosquitto_enabled: true


# If you need to change the MQTT port you can uncomment and adjust
# mosquitto_container_mqtt_host_bind_port: "1884"
```

## Usage

After installation, you can use `just run-tags mosquitto-add-user --extra-vars=username=<username> --extra-vars=password=<password>"` to create a user. For the setting to take effect, you must restart the container.


## Support

- Github issues: [mother-of-all-self-hosting/ansible-role-mosquitto/issues](https://github.com/mother-of-all-self-hosting/ansible-role-mosquitto/issues)
