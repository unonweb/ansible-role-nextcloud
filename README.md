ABOUT
=====

A radically simple Ansible role.
- System: Debian 13
- State: Testing


HOW TO
======

Restore Nextcloud installation
------------------------------

In order to reinstall Nextcloud using data from your backups, you need to call `tasks_from: nextcloud-restore.yml`, e.g:

```yml
- ansible.builtin.import_role:
    name: nextcloud
    tasks_from: nextcloud-restore.yml
  vars:
    nextcloud_app_dir: "{{ host_nextcloud_app_dir }}" # required
    nextcloud_linux_user: www-data # required
    nextcloud_install_version: 33.0.5 # required
    nextcloud_config_vars: {} # required
```

Furthermore you need to `nextcloud_config_vars` instead of `nextcloud_config_overrides` because we need to create Nextclouds's main `config.php`. Additionally to your preferred configurations you need to include in `nextcloud_config_vars` the following variables:

```yml
nextcloud_config_vars: {}
	passwordsalt: VALUE_FROM_PREVIOUS_INSTANCE
	secret: VALUE_FROM_PREVIOUS_INSTANCE
	instanceid: VALUE_FROM_PREVIOUS_INSTANCE
	version: VALUE_FROM_PREVIOUS_INSTANCE
```

Note that `nextcloud_config_vars: { version: }` and `nextcloud_install_version` are different regarding the last digit.


MANUAL CONFIG
=============

Enable Mysql 4 Byte Support
---------------------------

- https://docs.nextcloud.com/server/22/admin_manual/configuration_database/mysql_4byte_support.html