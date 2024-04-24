# rcb

[![quality](https://img.shields.io/ansible/quality/27910)](https://galaxy.ansible.com/vbotka/rcb)[![Build Status](https://travis-ci.org/vbotka/ansible-rcb.svg?branch=master)](https://travis-ci.org/vbotka/ansible-rcb)[![Documentation Status](https://readthedocs.org/projects/rcb/badge/?version=latest)](https://rcb.readthedocs.io/en/latest/)[![GitHub tag](https://img.shields.io/github/v/tag/vbotka/ansible-rcb)](https://github.com/vbotka/ansible-rcb/tags)

[Ansible role.](https://galaxy.ansible.com/ui/standalone/roles/vbotka/rcb/) Install and configure [RCB (Rsync-Crypto-Backup)](https://github.com/vbotka/rcb).

[Documentation at readthedocs.io](http://rcb.readthedocs.io/)

Feel free to [share your feedback and report issues](https://github.com/vbotka/ansible-config-light/issues).

[Contributions are welcome](https://github.com/firstcontributions/first-contributions).


## Requirements and dependencies

### Roles

* vbotka.ansible_lib

### Collections

* community.crypto
* community.general


## Install roles and collections

```bash
shell> ansible-galaxy role install vbotka.rcb
shell> ansible-galaxy role install vbotka.ansible_lib
```

The collections community.crypto and community.general should be
included in standard Ansible installation. If they are not or if you want
to use the latest versions install them

```bash
shell> ansible-galaxy collections install community.crypto
shell> ansible-galaxy collections install community.general
```


## Ansible lint

Use the configuration file *.ansible-lint.local* when running
*ansible-lint*. Some rules might be disabled and some warnings might
be ignored. See the notes in the configuration file.

```bash
shell> ansible-lint -c .ansible-lint.local
```


## License

[![license](https://img.shields.io/badge/license-BSD-red.svg)](https://www.freebsd.org/doc/en/articles/bsdl-gpl/article.html)


## Author Information

[Vladimir Botka](https://botka.info)
