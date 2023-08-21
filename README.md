# ansible-rcb

[![quality](https://img.shields.io/ansible/quality/27910)](https://galaxy.ansible.com/vbotka/rcb)[![Build Status](https://travis-ci.org/vbotka/ansible-rcb.svg?branch=master)](https://travis-ci.org/vbotka/ansible-rcb)[![Documentation Status](https://readthedocs.org/projects/rcb/badge/?version=latest)](https://rcb.readthedocs.io/en/latest/)

[Ansible role.](https://galaxy.ansible.com/vbotka/rcb/) Install and configure [RCB (Rsync-Crypto-Backup)](https://github.com/vbotka/rcb).

[Documentation at readthedocs.io](http://rcb.readthedocs.io/)

Feel free to [share your feedback and report issues](https://github.com/vbotka/ansible-config-light/issues).

[Contributions are welcome](https://github.com/firstcontributions/first-contributions).


## Requirements and dependencies

### Collections

* community.crypto
* community.general


## Role Variables

1) Install the role and collections

```bash
shell> ansible-galaxy role install vbotka.rcb
shell> ansible-galaxy collections install community.crypto
shell> ansible-galaxy collections install community.general
```
Review the defaults and examples in vars.

2) Download the example of an Ansible project

Download the examples of the Ansible [playbooks, inventory and configuration](https://github.com/vbotka/rcb/tree/master/ansible)

```bash
shell> tree .
├── ansible.cfg
├── hosts
├── rcb-backup-server.yml
├── rcb-devel.yml
└── rcb.yml
```

3) Configure the project. Edit and change at least:

* In the playbook rcb.yml which will configure the clients, edit and
  change at least following variables:

  * rcb_bck_host; The backup server.

  * rcb_bck_dst; The directory at the backup server to store the backups.

  * rcb_root_public_keys_dir; The directory at the Ansible controller
    to store the public keys of the clients.

  * rcb_rcb_bck_root; The directory at the client which will be
    synchronized to rcb_bck_dst

  * rcb_rcb_rst_root; The directory at the client where the backup
    from the server will be eventually restored.

* In the playbook rcb-backup-server.yml which will configure the
  server, edit and change at least following variables:

  * rcb_bck_dst

  * rcb_root_public_keys_dir

  * rcb_bck_user; The owner of the directory rcb_bck_dst

  * rcb_bck_group; The group of the directory rcb_bck_dst

  * rcb_bck_shell; The login shell of rcb_bck_user

The following workflow was tested with Ubuntu 22.04 and 20.04
(localhost Backup-Client), and FreeBSD 10.3 (remote Backup-Server)

4) Create SSH keys at Backup-Clients

```bash
shell> ansible-playbook rcb.yml -t phase1
```

5) Configure the Backup-Server

```bash
shell> ansible-playbook rcb-backup-server.yml
```

6) Proceed with the Configuration of the Backup-Clients

```bash
shell> ansible-playbook rcb.yml -t phase2
```

7) Run tests and check /var/log/rcb.log for potential errors

```bash
shell> ansible-playbook rcb.yml -t testall
```    

8) Add backup directories to rsnapshot.conf and configure cron. [RCB
project](https://github.com/vbotka/rcb) provides
[crontab.example](https://github.com/vbotka/rcb/blob/master/crontab.example)


## Development

Copy local changes to Backup client

```bash
shell> ansible-playbook rcb-devel.yml
```

Test it

```bash
shell> ansible-playbook rcb.yml -t rcb_devel
```


## License

[![license](https://img.shields.io/badge/license-BSD-red.svg)](https://www.freebsd.org/doc/en/articles/bsdl-gpl/article.html)


## Author Information

[Vladimir Botka](https://botka.info)
