# Apigee Edge All-in-One Installation

Ansible playbook to install all-in-one Apigee Edge and BaaS on your local PC.

## Prerequisites

- Install VirtualBox and Vagrant
- Install Ansible 2.0 ~
- Get apigee-edge-4.15.07.03.zip and save it in the same directory as the playbook
- Save a valid license file for Apigee Edge in the same directory as the playbook

## Installation

```
$ vagrant box add centos66 https://dl.dropbox.com/s/yr5xbz177heaav2/centos66.box
$ vagrant up edge
$ ansible-playbook edge-aio.yml
$ vagrant up baas
$ ansible-playbook baas-aio.yml
```

## Edge Management UI Access

- http://192.168.33.10:9000
- username: admin@example.com
- password: secret123
- organizatin: dev
- environment: test

## Edge API Access

- http://192.168.33.10:9001/{basePath}/{resourcePath}

## BaaS Portal Access

http://192.168.33.20:9000
username: admin@example.com
password: secret123

## BaaS API Access

http://192.168.33.10.8081/AppServices/{org}/{app}
