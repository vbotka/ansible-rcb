ansible-rcb
===========

[![Build Status](https://travis-ci.org/vbotka/ansible-rcb.svg?branch=0.1.4)](https://travis-ci.org/vbotka/ansible-rcb) ![Build Status](https://readthedocs.org/projects/rcb/badge/?version=latest)

[Ansible role.](https://galaxy.ansible.com/vbotka/rcb/) Install and configure [RCB (Rsync-Crypto-Backup)](https://github.com/vbotka/rcb). Documentation is available at [ReadTheDoc](http://rcb.readthedocs.io/).


Requirements
------------

None


Role Variables
--------------

TBD


Dependencies
------------

None


Examples
----------------

Examples of playbooks and variables are available at [RCB project](https://github.com/vbotka/rcb/tree/master/ansible).

1) Install the role "ansible-galaxy install vbotka.rcb"

Edit and change at least:
- rcb_BCK_HOST and rcb_BCK_DST in vars/rcb.yml
- rcb_BCK_DST in vars/rcb-backup-server.yml
- hosts in playbooks/rcb.yml
- hosts in playbooks/rcb-backup-server.yml


Following workflow was tested with Ubuntu 18.04 (localhost Backup-Client) and FreeBSD 10.3 (remote Backup-Server)

2) Create SSH keys at Backup-Clients

```
 ansible-playbook ~/.ansible/playbooks/rcb.yml -t phase1
```

3) Configure the Backup-Server

```
ansible-playbook ~/.ansible/playbooks/rcb-backup-server.yml
```

4) Configure the Backup-Clients

```
ansible-playbook ~/.ansible/playbooks/rcb.yml -t phase2
```

5) Run tests and check /var/log/rcb.log for potential errors.

```
ansible-playbook ~/.ansible/playbooks/rcb.yml -t testall
```    

6) Add backup directories to rsnapshot.conf and configure cron. [RCB project](https://github.com/vbotka/rcb) provides  [crontab.example](https://github.com/vbotka/rcb/blob/master/crontab.example)


Development
-----------

Copy local changes to Backup client

```
ansible-playbook ~/.ansible/playbooks/rcb-devel.yml
```

Test it

```
ansible-playbook ~/.ansible/playbooks/rcb.yml -t rcb_devel
```


License
-------

[![license](https://img.shields.io/badge/license-BSD-red.svg)](https://www.freebsd.org/doc/en/articles/bsdl-gpl/article.html)


Author Information
------------------

[Vladimir Botka](https://botka.link)
