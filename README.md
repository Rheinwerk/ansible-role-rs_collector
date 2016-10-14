rs-collector
=========

This roles installs and configures rs-collector, the Rust based, scollector compatible telemetry collector for Bosun.

[![Build Status](https://travis-ci.org/Rheinwerk/ansible-role-rs_collector.svg?branch=master)](https://travis-ci.org/Rheinwerk/ansible-role-rs_collector)

Requirements
------------

None.

Role Variables
--------------

There are three variables that drive this role: `_rs_collector`, `RW_APT_CACHE_UPDATE`, and `RW_ENABLE_DOWNLOADS`. `_rs_collector` is a map that contains all configuration and settings for this role. `RW_APT_CACHE_UPDATE` and `RW_ENABLE_DOWNLOADS` may be specified as _extra variables_ on invocation of Ansible in order to force `apt-get update` or install the latest version of rs-configuration, respectively. Please see `defaults/main.yml` for details.

Dependencies
------------

None.

Example Playbook
----------------

The general contract of this role is to take the variables map `_rs_collector` from `defaults/main.yml` as a template for your configuration and pass that configuration as a parameter to this role.

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:
```
    - hosts: <HOST THAT IS ALLOWED TO MANAGE MYSQL>
      var:
        RW_APT_CACHE_UPDATE: yes
        RS_COLLECTOR:
          use_default_config: yes
          server:
            ip: localhost
            port: 8070
          hostname: "{{ ansible_hostname }}"
          domain:
          hostgroup: my-group
          common:
            tags:
              one_tag: one_value
          galera:
            - user: root
              password: toor
              socket: /var/lib/mysql.sock
          hasipaddr:
            ipv4:
              - "127.0.0.1"
              - "192.168.205.7"
          extra_lines: |
            # Mööp
      roles:
s        - { role: rs_collector, tags: [ 'rs_collector' ], _rs_collector: "{{ RS_COLLECTOR }}" }
```

License
-------

Please see LICENSE.

Author Information
------------------

Original author is [Lukas Pustina](https://github.com/lukaspustina) as member of the [Rheinwerk](https://github.com/Rheinwerk) project.
