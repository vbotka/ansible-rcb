Role Name
=========

Install and configure RCB (Rsync-Crypto-Backup) from github.com/vbotka/rcb


Requirements
------------

Ubuntu 16.04 at digitalocean.com needs python2.7


Role Variables
--------------

<TBD>


Dependencies
------------

None


Examples
----------------

Playbooks are available in the RCB project https://github.com/vbotka/rcb


1) Following Workflow was tested with Ubuntu 16.04 at digitalocean.com. Create one droplet for Backup-Server and at least one droplet for Backup-Client. Change at least the IP addresses in the ansible hosts file and the IP address of rcb_BCK_HOST in ansible vars.


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

5) Run tests check /var/log/rcb.log for potential errors.

```
ansible-playbook ~/.ansible/playbooks/rcb.yml -t testall
```    


License
-------

BSD

Author Information
------------------

Vladimir Botka [https://botka.link]
