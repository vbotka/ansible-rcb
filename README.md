Role Name
=========

Install and configure RCB (Rsync-Crypto-Backup) from github.com/vbotka/rcb


Requirements
------------

Ubuntu 16.04 at digitalocean.com needs python2.7


Role Variables
--------------

TBD


Dependencies
------------

None


Examples
----------------

Playbooks are available in the [RCB project](https://github.com/vbotka/rcb/ansible)


1) Following Workflow was tested with Ubuntu 16.04 at digitalocean.com. Create one droplet for Backup-Server and at least one droplet for Backup-Client. Change at least:
- the IP addresses in the ansible hosts file
- the IP address of rcb_BCK_HOST in ansible vars
- rcb_user_password in rcb-backup-server.yml

2) "rcb.yml -t phase1" creates SSH keys at Backup-Clients and stores the public keys at the localhost

```
 ansible-playbook ~/.ansible/playbooks/rcb.yml -t phase1
```

3) rcb-backup-server.yml configures the Backup-Server

```
ansible-playbook ~/.ansible/playbooks/rcb-backup-server.yml
```

4) rcb.yml -t phase2 configures the Backup-Clients

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
ansible-playbook ~/.ansible/playbooks/rcb.yml -t devel
```


License
-------

BSD


Author Information
------------------

[Vladimir Botka](https://botka.link)
