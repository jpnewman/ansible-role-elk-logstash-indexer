# jpnewman.elk-logstash-indexer

[![Ansible Role](https://img.shields.io/ansible/role/9590.svg?maxAge=2592000)](https://galaxy.ansible.com/jpnewman/elk-logstash-indexer/)
[![Build Status](https://travis-ci.org/jpnewman/ansible-role-elk-logstash-indexer.svg?branch=master)](https://travis-ci.org/jpnewman/ansible-role-elk-logstash-indexer)

This is a Ansible role to installs [logstash](https://www.elastic.co/products/logstash) indexer

This role is based on role ```logstash``` <https://github.com/rueian/ansible-elk-example> by Rueian

The logstash indexer creates the following logstash configuration files: -

- 01-redis-input.conf
- 02-topbeat-input.conf
- 30-elasticsearch-output.conf
- 31-stdout-output.conf

## Requirements

Ansible 2.x

## Role Variables

|Variable|Description|Default|
|---|---|---|
|```logstash_repo_version```||5.x|
|```elasticsearch_gpg_key_url```||https://artifacts.elastic.co/GPG-KEY-elasticsearch|
|```logstash_apt_repository```||```deb https://artifacts.elastic.co/packages/{{ logstash_repo_version }}/apt stable main```|
|```logstash_listen_port```||5043|
|```logstash_redis_host```||localhost|
|```logstash_redis_port```||6379|
|```logstash_redis_db```||0|
|```logstash_redis_key```||logstash|
|```logstash_redis_data_type```||channel|
|```logstash_redis_batch_count```||10|
|```logstash_redis_threads```||1|
|```logstash_debug```||false|
|```topbeat_redis_host```||localhost|
|```topbeat_redis_port```||6379|
|```topbeat_redis_db```||0|
|```topbeat_redis_key```||topbeat|
|```topbeat_redis_data_type```||list|
|```logstash_ls_heap_size```||1g|
|```logstash_ls_open_files```||16384|
|```logstash_elasticsearch_hosts```||'["localhost:9200"]'|
|```logstash_elasticsearch_index```||'logstash-%{+YYYY.MM.dd}'|
|```ssl_cert_local_directory```||files/certs|
|```ssl_cert_directory```||/etc/pki/tls/certs|
|```ssl_cert```||logstash-forwarder.crt|
|```ssl_key```||logstash-forwarder.key|
|```apt_cache_valid_time```||600|
|```check_logstash_config```||false|

## Dependencies

none

## Example Playbook

    - hosts: servers
      roles:
         - { role: jpnewman.elk-logstash-indexer, tags: ["logstash-indexer"] }

## License

MIT / BSD

## Author Information

John Paul Newman
