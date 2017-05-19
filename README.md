Ansible Role: MariaDB
=========

[![Build Status](https://travis-ci.org/CarlosLongarela/ansible-role-mariadb.svg?branch=master)](https://travis-ci.org/CarlosLongarela/ansible-role-mariadb)

Install MariaDB, basic security options and utils for databse tuning and backups with cron tasks.

Requirements
------------

None.

Role Variables
--------------

    mariadb_version: 10.1.22

    mariadb_service_name: mysql
    mariadb_secure_installation: True

    mariadb_root_password:

    server_path_utiles: /root/utiles

    mariadb_path_backups: /home/db_backups/

    mariadb_databases:

    mariadb_options:
      bind_address: '127.0.0.1'
      performance_schema: on
      skip_name_resolve: 1
      max_connections: 100
      connect_timeout: 2
      max_allowed_packet: 10M
      innodb_buffer_pool_size: 100M
      table_cache: 1000
      tmp_table_size: 50M
      max_heap_table_size: 50M
      query_cache_limit: 256K
      query_cache_size: 20M
      query_cache_min_res_unit: 2k
      join_buffer_size: 2M
      sort_buffer_size: 256K
      read_buffer_size: 128K
      read_rnd_buffer_size: 4M
      key_buffer: 500M

    cron_backup_db:
      minute: "15"
      hour: "3"
      day: "*"
      weekday: "*"

    cron_optimiza_db:
      minute: "1"
      hour: "3"
      day: "*"
      weekday: "0"


Dependencies
------------

None.

Example Playbook
----------------

    - hosts: servers

      gather_facts: no
      become: true

    mariadb_databases:
      - mydatabase

    utiles_bd: true

      roles:
         - { role: CarlosLongarela.mariadb }

License
-------

GPLv2

Author Information
------------------

This role was created in 2017, May by [Carlos Longarela](mailto:carlos@longarela.eu), from [Taberna WordPress](https://tabernawp.com/).
