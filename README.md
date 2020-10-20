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
- CONTAINER_NAME: 'mongo'
- ROOT_USERNAME: 'root'
- ROOT_PASSWORD: 'Pa$$w0rd'
- SET_REPLICA_STANDALONE: false
- WIREDTIGER_ENGINE_CACHESIZEGB: ''
- NET_PORT: '27017'
- NET_BINDIP: '127.0.0.1'
- SECURITY_AUTHORIZATION: 'enabled'
- SECURITY_CLUSTER_AUTH_MODE: ''
- NET_SSL_MODE: ''
- NET_SSL_PEM_KEYFILE: '' 
- NET_SSL_CA_FILE: '' 
- NET_SSL_CLUSTER_FILE: '' 
- SECURITY_KEYFILE: ''
- REPLICATION_NAME: 'rs0' 
- INIT_USER_NAME: ''
- INIT_USER_PASS: ''
- INIT_USER_ROLE: 'readWrite'
- INIT_USER_DB: ''
- DOCKER_CPU_PERIOD: 0
- DOCKER_CPU_QUOTA: 0
- DOCKER_MEMORY: 0
- CONTAINER_STATE: 'started'
- VOLUME_STATE: 'present'

Dependencies
------------

None

Example Playbook
----------------

      - name: Deploy MongoDB with authorization enabled
        include_role:
          name: asbrl-mongodb
        vars:
          ROOT_USERNAME: "root"
          ROOT_PASSWORD: "Pa$$w0rd"
          SECURITY_AUTHORIZATION: "enabled"
          WIREDTIGER_ENGINE_CACHESIZEGB: "6"
        tags:
          - mongo

      - name: Deploy MongoDB with Replica Set Standalone
        include_role:
          name: asbrl-mongodb
        vars:
          ROOT_USERNAME: "root"
          ROOT_PASSWORD: "Pa$$w0rd"
          SECURITY_AUTHORIZATION: "enabled"
          REPLICATION_NAME: "rs0"
          SET_REPLICA_STANDALONE: true
        tags:
          - mongo

      - name: Deploy MongoDB with Replica Set Standalone and initialize user credentials
        include_role:
          name: asbrl-mongodb
        vars:
          ROOT_USERNAME: "root"
          ROOT_PASSWORD: "Pa$$w0rd"
          SECURITY_AUTHORIZATION: "enabled"
          REPLICATION_NAME: "rs0"
          SET_REPLICA_STANDALONE: true
          INIT_USER_NAME: "dummy_usr"
          INIT_USER_PASS: "1234"
          INIT_USER_DB: "dummy"
        tags:
          - mongo

License
-------

BSD

Author Information
------------------

Moegui.com