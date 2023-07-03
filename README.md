# Mosquitto Ansible Role


An open source [MQTT](https://en.wikipedia.org/wiki/MQTT) broker. This role helps you to set up mosquitto:

- with everything run in [Docker](https://www.docker.com/) containers
- powered by [the official mosquitto container image](https://hub.docker.com/r/_/mosquitto/)


## Installing

To configure and install mosquitto on your own server(s), you should use a playbook like [Mother of all self-hosting](https://github.com/mother-of-all-self-hosting/mash-playbook) or write your own.

## Configuring this role for your playbook

```yaml
mosquitto_enabled: true
```

## Usage

After installation, you can use `just run-tags mosquitto-add-user --extra-vars=username=<username> --extra-vars=password=<password>"` to create a user.


## Support

- Github issues: [mother-of-all-self-hosting/ansible-role-mosquitto/issues](https://github.com/mother-of-all-self-hosting/ansible-role-mosquitto/issues)