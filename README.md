# Ansible Role: crowd

[![Build Status](https://travis-ci.org/mimacom/ansible-role-crowd.svg?branch=master)](https://travis-ci.org/mimacom/ansible-role-crowd)

Installs Atlassian Crowd on Linux servers. This role will install OpenJDK by default.

## Requirements

None.


## Role Variables

Available variables are listed below, along with default values (see
`defaults/main.yml`):

    crowd_version: 3.1.3

Specify Crowd version to install

    crowd_fqdn: ""

Set tomcat proxy FQDN

    crowd_https: False

Set tomcat proxy protocol

    crowd_port: ""

Set tomcat proxy port

    crowd_include_jdk: True

Set False to disable OpenJDK installation.

    crowd_openjdk_version: 1.8.0

Which OpenJDK to install for running Crowd. Check Crowd's supported platforms and adjust this variable if necessary.

    crowd_user: crowd

Name of the user under which the service will run

    crowd_application_folder: "/opt/atlassian/crowd"

Path where to install the application

    crowd_data_folder: "/var/atlassian/application-data/crowd"

Path where application data will be stored

    crowd_jvm_memory: 1g

Java VM heap size

## Dependencies

None.

## Example Playbook

This installs Crowd and tells tomcat to expect a specific vHost and an
HTTPS connection (proxy settings).

    - hosts: servers
      become: yes
      roles:
        - role: mimacom.crowd

## Upgrade Crowd

To upgrade Crowd, simply change the version variable to a higher
version number. Old binary versions will be preserved but not further
used. You should delete them manually.

Please do a proper backup prior upgrading, as the Crowd data will not
work with older versions. If you set a lower version than installed, the
role will fail.

The current version is saved as ansible fact in /etc/ansible/facts.d/

## License

Apache License 2.0

## Author Information

This role was created by [Remo Wenger](http://www.remowenger.ch) ([mimacom](http://www.mimacom.com)).
