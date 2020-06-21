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
daemon: 0 # The delay of the daemon.

ssl: yes # Whether ddclient should use ssl.

configs:              # List of configurations
  -
    protocol: dnspark # The protocol to use
    server: null      # The server of the protocol, update DNS information on 'host'
    use: null         # How the should IP address be obtained
    backupmx: null    # Indicates that DNSPark should be the secondary MX for this domain or host
    mx: null          # A host MX’ing for this host or domain
    mxpri: null       # MX priority.
    wildcard: null    # Add a DNS wildcard CNAME record that points to {host}
    login: login      # The user's login
    password: pwd     # The user's password
    hosts:            # List of hosts
      - hosts1
      - hosts2
```
### Vars variable

```(yaml)
_conf_location: /etc/ddclient.conf # The path of the ddclient configuration.
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


