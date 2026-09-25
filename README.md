ABOUT
=====

A radically simple Ansible role.
- System: Debian 13
- State: Testing


HOW TO
======

Install Nextcloud first time
----------------------------



Restore Nextcloud installation
------------------------------

Once the command completes, open config/config.php and copy these key lines from your original config.php backup:

```php
'instanceid' => 'orig_instance_id',
'passwordsalt' => 'orig_password_salt',
'secret' => 'orig_secret',
```

Index all files in your restored data folder so Nextcloud registers them:

```sh
sudo -u www-data php /path/to/nextcloud/occ files:scan --all
```