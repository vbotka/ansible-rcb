# ansible-rcb

[![quality](https://img.shields.io/ansible/quality/27910)](https://galaxy.ansible.com/vbotka/rcb)[![Build Status](https://travis-ci.org/vbotka/ansible-rcb.svg?branch=master)](https://travis-ci.org/vbotka/ansible-rcb)[![Documentation Status](https://readthedocs.org/projects/rcb/badge/?version=latest)](https://rcb.readthedocs.io/en/latest/)

[Ansible role.](https://galaxy.ansible.com/vbotka/rcb/) Install and configure [RCB (Rsync-Crypto-Backup)](https://github.com/vbotka/rcb).

[Documentation at readthedocs.io](http://rcb.readthedocs.io/)

Feel free to [share your feedback and report issues](https://github.com/vbotka/ansible-config-light/issues).

[Contributions are welcome](https://github.com/firstcontributions/first-contributions).


## Requirements and dependencies

### Collections

* ansible.posix
* community.crypto
* community.general


## Role Variables

Review the defaults and examples in vars.


## Examples

Examples of playbooks and variables are available in [RCB project](https://github.com/vbotka/rcb/tree/master/ansible).

1) Install the role and collections

```
shell> ansible-galaxy role install vbotka.rcb
shell> ansible-galaxy collections install ansible.posix
shell> ansible-galaxy collections install community.crypto
shell> ansible-galaxy collections install community.general
```

Edit and change at least:
- rcb_BCK_HOST and rcb_BCK_DST in vars/rcb.yml
- rcb_BCK_DST in vars/rcb-backup-server.yml
- hosts in playbooks/rcb.yml
- hosts in playbooks/rcb-backup-server.yml


Following workflow was tested with Ubuntu 18.04 and 20.04 (localhost Backup-Client), and FreeBSD 10.3 (remote Backup-Server)

2) Create SSH keys at Backup-Clients

```
shell> ansible-playbook ~/.ansible/playbooks/rcb.yml -t phase1
```

3) Configure the Backup-Server

```
shell> ansible-playbook ~/.ansible/playbooks/rcb-backup-server.yml
```

4) Configure the Backup-Clients

```
shell> ansible-playbook ~/.ansible/playbooks/rcb.yml -t phase2
```

5) Run tests and check /var/log/rcb.log for potential errors.

```
shell> ansible-playbook ~/.ansible/playbooks/rcb.yml -t testall
```    

6) Add backup directories to rsnapshot.conf and configure cron. [RCB project](https://github.com/vbotka/rcb) provides  [crontab.example](https://github.com/vbotka/rcb/blob/master/crontab.example)


## Development

Copy local changes to Backup client

```
shell> ansible-playbook ~/.ansible/playbooks/rcb-devel.yml
```

Test it

```
shell> ansible-playbook ~/.ansible/playbooks/rcb.yml -t rcb_devel
```


## License

[![license](https://img.shields.io/badge/license-BSD-red.svg)](https://www.freebsd.org/doc/en/articles/bsdl-gpl/article.html)


## Author Information

[Vladimir Botka](https://botka.link)
