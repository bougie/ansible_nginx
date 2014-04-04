ansible_nginx
=============

Ansible playbook for configuration of the nginx web server.
It handles two cases of configurations:
  * a single user mode
  * a multi user mode

The webserver runs under user www-data user. All data are stored in subdirectories of /srv/www.


## Single user configuration

This is the default mode.

Defaults values set :
  * user : the server hostname
  * user home dir (default vhost data dir) : /srv/www/default
  * vhost configuration file : /etc/nginx/sites-enabled/default


## Multi users configuration

A host_vars file have to be like this :
```
multiusers: True
users:
  - name: <username>
    vhosts:
      - <vhostname1>
      - <vhostname2>
```

Ansible will create an user for each users. The home directory will be /srv/www/<username>.
VHosts of this user will be stored in /srv/www/<username>/<vhostname>
