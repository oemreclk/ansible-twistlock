Role Name
=========

Ansible role for install/update twistlock defender on Openshift Clusters.

Requirements
------------

- Custom credential type must be created on Ansible Platform for twistlock credential.
Input Configuration:
fields:
  - id: twistlock_username
    type: string
    label: twistlock_username
  - id: twistlock_password
    type: string
    label: twistlock_password
    secret: true
required:
  - twistlock_username
  - twistlock_password
Injector configuration:
env:
  TWISTLOCK_PASSWORD: '{{ twistlock_password }}'
  TWISTLOCK_USERNAME: '{{ twistlock_username }}'

- Multiple select survey must be created on Ansible Template. Openshift cluster names in vars and survey names must match.
![image](https://github.com/user-attachments/assets/dcd6d264-95b9-432c-b999-4a689f885f99)

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



- name: Install/Update Twistlock Defender Job Template
  hosts: localhost
  roles:
    - twistlock-deploy

License
-------

BSD

Author Information
------------------

Prepared by QUASYS Digital Technology Solutions <automation@quasys.com.tr> .
