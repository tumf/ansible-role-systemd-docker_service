[![Build Status](https://travis-ci.org/tumf/ansible-role-systemd-docker_service.svg?branch=master)](https://travis-ci.org/tumf/ansible-role-systemd-docker_service)

systemd-docker_service - Ansible role
=========

Register docker containers as systemd daemons.

Requirements
------------

Role Variables
--------------

|name|type|default|description
|----|----|-------|-----------
|systemd_docker_service_image*|String||image of container
|systemd_docker_service_command|String|""|command
|systemd_docker_service_ports|Array|[]|publish ports e.g.["80:80","443":"443"]

> * required

Dependencies
------------

* tumf.systemd-service

Example Playbook
----------------

    - hosts: 127.0.0.1
      connection: local
      tags:
        - swarm-manager
      vars:
        ansible_unit_test: True
      roles:
        - role: ../..
          systemd_service_name: "swarm-manager"
          systemd_service_envs:
              - "DOCKER_HOST=tcp://127.0.0.1:2375"
          systemd_docker_service_image: "swarm"
          systemd_docker_service_command: |
            manage --replication --advertise=127.0.0.1:2375
          systemd_docker_service_ports:
            - "2377:2375"

License
-------

MIT

Author Information
------------------

> @tumf

