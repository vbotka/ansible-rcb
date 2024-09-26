============================
vbotka.rcb 2.6 Release Notes
============================

.. contents:: Topics


2.6.3
=====

Release Summary
---------------
Maintenance update.

Major Changes
-------------

Minor Changes
-------------
- Update python 3.11 in .travis.yml


2.6.2
=====

Release Summary
---------------
Maintenance update.

Major Changes
-------------
* Update source vewrsion 1.2.0

Minor Changes
-------------


2.6.1
=====

Release Summary
---------------
Ansible 2.17 update.

Major Changes
-------------
* Add supported Ubuntu 24.04 Noble

Minor Changes
-------------
* Update README.
* Fix README label.
* Update lint config.
* Add var rcb_role_version
* Update tasks/debug.yml
* Rename tasks keys->cert, configure->config, packages->pkg
* Update all debug names
* Create logical blocks of tasks
* Update ansible_check_mode conditions
* Tasks paths.yml note: The two steps: 1) Copy scripts to working
  directory and 2) Patch scripts in working directory are not
  idempotent. The second step will always report changed.


2.6.0
=====

Release Summary
---------------
Ansible 2.16 update.

Major Changes
-------------
* Update meta. Ansible 2.16.

Minor Changes
-------------

Bugfixes
--------

Breaking Changes / Porting Guide
--------------------------------
