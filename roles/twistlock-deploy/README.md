Role Name
=========

Ansible role for install/update twistlock defender on Openshift Clusters.

Requirements
------------

- Custom credential type must be created on Ansible Platform for twistlock credential.
- Multiple select survey must be created on Ansible Template. Openshift cluster names in vars and survey names must match.
- Openshift clusters must be defined as variables. Api endpoint and sa token must be added also.

Role Variables
--------------

vars/main.yml

Dependencies
------------

- redhat.openshift
- ansible.builtin

Example Playbook
----------------


    - hosts: localhost
      roles:
         - { role: username.rolename, x: 42 }

License
-------

BSD

Author Information
------------------

Prepared by QUASYS Digital Technology Solutions <automation@quasys.com.tr> .
