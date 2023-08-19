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

Review the defaults and examples in vars.


## Examples

Examples of playbooks and variables are available in [RCB project](https://github.com/vbotka/rcb/tree/master/ansible).

1) Install the role and collections

```bash
shell> ansible-galaxy role install vbotka.rcb
shell> ansible-galaxy collections install community.crypto
shell> ansible-galaxy collections install community.general
```

Edit and change at least:

- rcb_bck_host and rcb_bck_dst in vars/rcb.yml
- rcb_bck_dst in vars/rcb-backup-server.yml
- hosts in playbooks/rcb.yml
- hosts in playbooks/rcb-backup-server.yml


Following workflow was tested with Ubuntu 22.04 and 20.04 (localhost Backup-Client), and FreeBSD 10.3 (remote Backup-Server)

2) Create SSH keys at Backup-Clients

```bash
shell> ansible-playbook rcb.yml -t phase1
```

3) Configure the Backup-Server

```bash
shell> ansible-playbook rcb-backup-server.yml
```

4) Proceed with the Configuration of the Backup-Clients

```bash
shell> ansible-playbook rcb.yml -t phase2
```

5) Run tests and check /var/log/rcb.log for potential errors

```bash
shell> ansible-playbook rcb.yml -t testall
```    

6) Add backup directories to rsnapshot.conf and configure cron. [RCB project](https://github.com/vbotka/rcb) provides [crontab.example](https://github.com/vbotka/rcb/blob/master/crontab.example)


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
