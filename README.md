ASBRL-MONGODB
=========

Deploy a single MongoDB node as a Docker container.

Requirements
------------

Need to be Docker engine installed.

Role Variables
--------------

- default_user: 'ubuntu'
- BUILD: '4.4.0'
- ROOT_USERNAME: 'root'
- ROOT_PASSWORD: 'Pa$$w0rd'
- WIREDTIGER_ENGINE_CACHESIZEGB: ''
- NET_PORT: '27017'
- NET_BINDIP: '127.0.0.1'
- SECURITY_AUTHORIZATION: 'enabled'

Dependencies
------------

None

Example Playbook
----------------

      - name: Deploy MongoDB
        include_role:
          name: asbrl-mongodb
        vars:
          ROOT_USERNAME: "{{ MONGO_ROOT_USERNAME }}"
          ROOT_PASSWORD: "{{ MONGO_ROOT_PASSWORD }}"
          SECURITY_AUTHORIZATION: "{{ MONGO_SECURITY_AUTHORIZATION }}"
          WIREDTIGER_ENGINE_CACHESIZEGB: "{{ MONGO_WIREDTIGER_ENGINE_CACHESIZEGB }}"
        tags:
          - mongo

License
-------

BSD

Author Information
------------------

Moegui.com