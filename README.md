### Please note: This repo is inactive and no longer mantained. For a newer Logstash role see [Ansible Logstash role](https://github.com/valentinogagliardi/logstash-role)

#### Ansible Playbook to automate the setup of an ELK stack (centralized logging server with Logstash, Elasticsearch, Redis and Kibana)

[![Build Status](https://travis-ci.org/valentinogagliardi/ansible-logstash.png?branch=master)](https://travis-ci.org/valentinogagliardi/ansible-logstash)

This playbook is intended to be run against a clean server (not clients) that will be used as a central logger. After the setup of the server, clients cat be instructed to redirect all logs to the central location.

**Platform**: Tested on **Debian 7 x64** / **CentOS 6.x x64** / **Ubuntu Precise**

**Disclaimer**: do not run this Playbook on a live production system!! Use a dedicated instance instead.

**Prerequisites**: At least 1GB Ram required. 2GB is better

**Logging Logic**: Clients => Rsyslog Tcp 514 => Logstash => Redis => Logstash => Elasticsearch => Kibana

![Picture](http://www.servermanaged.it/wp-content/uploads/2013/10/Setup-Logstash-Elasticsearch-Kibana.png)

### Preparation

1. Setup your target host in hosts

2. Add your custom domain in /etc/hosts on your local box. Example: 11.11.11.11 logger

### Variables

**usname** : username of the vhost user 

**domain** : domain name of Nginx vhost. Example: logger

**pass** : password for Nginx auth

### Use

`ansible-playbook site.yml `

Wait some minutes, et voila, your centralized logging server is up and running!

Browse **http://domain/index.html#/dashboard/file/logstash.json** and happy logging!

See central-logs.yml for all tags available. Please note that tags must be launched in appearance order.

This is what the Playbook do:

1. Setup and configure Rsyslog to listen on tcp 514

2. Setup and configure Redis

3. Setup and configure Logstash

4. Setup and configure Elasticsearch, Install Open-Jdk

5. Setup and configure Nginx and Kibana 3 with simple HTTP authentication

### TODO

Rsyslog-server role can be extended with TLS support. See http://www.rsyslog.com/doc/rsyslog_tls.html

### Credits

Ansible Logstash Playbook by <a href="https://plus.google.com/+ValentinoGagliardi?rel=author">Valentino Gagliardi </a>

[Ansible](http://www.ansible.com/)

[Logstash](http://www.logstash.net/)

[Elasticsearch](http://www.elasticsearch.org/)

[Kibana](http://www.elasticsearch.org/overview/kibana/)

[Redis](http://redis.io/)

[Ansible Fan Community](https://plus.google.com/u/0/communities/108222183653550371543)
