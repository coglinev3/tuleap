# Ansible Role: tuleap

Installs Tuleap Community Edition (TCE).
[Tuleap](https://www.tuleap.org/) is a all-in-one integrated Agil Management solution
capable of orchestrating everything from idea to release delivery.
Tuleap enables teams to plan, track, code, and collaborate on software products
and applications from a single tool for increased productivity.

## Requirements

A RHEL/CentOS Server 7.x (see [Installation Guide](https://docs.tuleap.org/installation-guide/full-installation.html) for details).

## Role Variables

Available variables are listed below, along with default values (see defaults/main.yml):

```yml
# The FQDN of the Tuleap server
# Default:  "{{ ansible_hostname }}"
tuleap_server_name: "tuleap.example.org"

# Tuleap packages to install
tuleap_packages:
  - rh-mysql57-mysql-server
  - tuleap
  - tuleap-theme-burningparrot
  - tuleap-theme-flamingparrot

# Tuleap package states: ( present ) | latest | absent
tuleap_packages_state: present

# Tuleap plugins
# You can install more plugins, see the whole list on
# https://docs.tuleap.org/installation-guide/install-plugins.html#install-plugins.
# However you don’t have to install all of them now. Start small and add them
# on the go.
tuleap_plugins:
  - tuleap-plugin-agiledashboard
  - tuleap-plugin-cardwall
  - tuleap-plugin-graphontrackers
  - tuleap-plugin-git
  - tuleap-plugin-pullrequest

# Tuleap plugins package states: ( present ) | latest | absent
tuleap_plugins_state: present

# The root password for the MySQL server
tuleap_mysql_password: password
```

## Dependencies

None.

## Example Inventory File

```dosini
# file: tests/inventory.ini

[local]
localhost   ansible_connection=local
```

## Example Playbook

```yml
---
# file: tests/tuleap.yml

- hosts: local
  become: true
  roles:
    - { role: coglinev3.tuleap }
```

## Version

Release: x.y.z

## License

BSD

## Author Information

This Ansible Role was created in 2020, by Cogline.v3.
