ASBRL-MONGODB
=========

Deploy a single MongoDB node as a Docker container.

Requirements
------------

Need to be Docker engine installed.

Role Variables
--------------

- default_user: 'ubuntu'
- BUILD: '4.4.3'
- CONTAINER_NAME: 'mongo'
- ROOT_USERNAME: 'root'
- ROOT_PASSWORD: 'Pa$$w0rd'
- REPLICA: NONE (PRIMARY/SECONDARY)
- WIREDTIGER_ENGINE_CACHESIZEGB: ''
- SERVER_HOST: '172.17.0.1'
- NET_PORT: '27017'
- NET_BINDIP: '127.0.0.1'
- SECURITY_AUTHORIZATION: 'disabled' (enabled)
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
- MASTER_HOST: 
- MASTER_PORT: 27017
- MASTER_HOST: localhost
- MASTER_USERNAME: root
- MASTER_PASSWORD: secret

Dependencies
------------

None

Example Playbook
----------------

      - name: Deploy MongoDB 
        include_role:
          name: asbrl-mongodb
        vars:
          ROOT_USERNAME: root
          ROOT_PASSWORD: secret

      - name: Deploy MongoDB with Replica Set Standalone
        include_role:
          name: asbrl-mongodb
        vars:
          CONTAINER_NAME: mongo-master
          NET_PORT: 27017
          ROOT_USERNAME: root
          ROOT_PASSWORD: secret
          SECURITY_AUTHORIZATION: enabled
          REPLICA: master
          REPLICATION_NAME: rs0
          INIT_USER_DB: dbtest
          INIT_USER_NAME: testusr
          INIT_USER_PASS: test1234

      - name: Deploy MongoDB node as Secondary
        include_role:
          name: asbrl-mongodb
        vars:
          CONTAINER_NAME: mongo-slave
          NET_PORT: 27018
          ROOT_USERNAME: root
          ROOT_PASSWORD: secret2
          SECURITY_AUTHORIZATION: enabled
          REPLICA: secondary
          REPLICATION_NAME: rs0
          MASTER_HOST: localhost
          MASTER_PORT: 27017
          MASTER_USERNAME: root
          MASTER_PASSWORD: secret

License
-------

BSD

Author Information
------------------

Moegui.com