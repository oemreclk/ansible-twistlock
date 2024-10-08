twistlock-deploy
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

    openshift_clusters:   # Predefined clusters for twistlock deployment.
      ocp_cluster1:  # Cluster names must match with survey cluster names
        api_endpoint: #Api endpoint for ocp cluster
        sa_token:  #ServiceAccount Token for OCP Cluster. It's used from credential named OCP_SA in role.
      ocp_cluster2: # Cluster names must match with survey cluster names
        api_endpoint: #Api endpoint for ocp cluster
        sa_token: #ServiceAccount Token for OCP Cluster. It's used from credential named OCP_SA in role.
    twistlock:
      username: "{{ lookup('ansible.builtin.env', 'TWISTLOCK_USERNAME') }}"  # Twistlock credential stored in Ansible Platform Credentials.
      password: "{{ lookup('ansible.builtin.env', 'TWISTLOCK_PASSWORD') }}"  # Twistlock credential stored in Ansible Platform Credentials.
    twistlock_console: "ec2-34-203-144-89.compute-1.amazonaws.com:8083" #Twistlock Console Address
    twistlock_defender: "ec2-34-203-144-89.compute-1.amazonaws.com:8084" #Twistlock Defender Address
    apiversion: "v1" #Apiversion
    namespace: "test-qua-twistlock"  #Namespace for the deployment.
    defender_version: "32"  #Defender version.
    repo: jfrog.xyz/defender #If not defined it uses paloalto container registry. If defined, pull required image from private container registry.

Dependencies
------------
Collections:
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
