# Ansible Role: DDClient
[![Build Status](https://travis-ci.com/mivek/ansible-role-ddclient.svg?token=Nxd1CoxuZDnwzK6Yq6sV&branch=master)](https://travis-ci.com/mivek/ansible-role-ddclient)
=========

This role installs and launches a [ddclient](https://ddclient.net/) service.

## Requirements
------------

None

## Role Variables
--------------
Variables are from [ddclient configuration](https://ddclient.net/usage.html#usage)

### Default variables

```(yaml)
ddclient_version: 3.9.1 # Only when installing from source
ddclient_configuration_template: templates/ddclient.conf.j2
ddclient_service_template: templates/ddclient.service.j2
ddclient_daemon: 300
ddclient_install_from_source: false
ddclient_ssl: 'yes'

ddclient_configs:
  -
    protocol: dnspark
    use: null
    server: null
    backupmx: null
    mx: null
    mxpri: null
    wildcard: null
    login: login
    password: password
    hosts:
      - host

```
### Vars variable

```(yaml)
__ddclient_configuration_directory: /etc/ddclient
__ddclient_configuration_location: "{{ __ddclient_configuration_directory }}/ddclient.conf"
__ddclient_download_url: https://github.com/ddclient/ddclient/archive/refs/tags/v{{ ddclient_version }}.tar.gz
__ddclient_download_location: /tmp/ddclient-{{ ddclient_version }}.tar.gz
__ddclient_unarchive_location: /tmp

__ddclient_service_file: /etc/systemd/system/ddclient.service
__ddclient_prerequisite:
  - g++
  - perl
  - make
```

## Dependencies
------------

None

## Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: servers
      become: true
      tasks:
        - import_role:
            name: ddclient
          vars:
            daemon: 60
            configs:
              -
                protocol: dyndns2
                login: myLogin
                password: myPassword
                use: web
                server: null
                backupmx: null
                mx: null
                mxpri: null
                wildcard: null
                hosts:
                  - myhost.dyndns.org
## License
-------

MIT


