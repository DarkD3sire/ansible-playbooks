# Wordpress on Ubuntu 20.04 LEMP

This playbook will install a WordPress website on top of a LEMP environment (**L**inux, **E**ngine-x, **M**ariaDB and **P**HP) on an Ubuntu 20.04 machine. A virtualhost will be created with the options specified in the `vars/default.yml` variable file.

## Settings

- `php_modules`:  An array containing PHP extensions that should be installed to support your WordPress setup. You don't need to change this variable, but you might want to include new extensions to the list if your specific setup requires it.
- `http_host`: Your domain name.
- `http_conf`: The name of the configuration file that will be created within Apache.
- `mysql_root_password`: The desired password for the **root** MySQL account.
- `mysql_db`: The name of the MySQL database that should be created for WordPress.
- `mysql_user`: The name of the MySQL user that should be created for WordPress.
- `mysql_password`: The password for the new MySQL user.
- `user`: The linux system user which has sudo access enabled.
- `wp_dir`: Set this to wordpress by default.


## Running this Playbook

Quickstart guide for those already familiar with Ansible:

### 1. Obtain the playbook
```shell
git clone https://github.com/DarkD3sire/ansible-playbooks.git
cd ansible-playbooks/WordPress_on_LEMP
```

### 2. Customize Options

```shell
nano vars/default.yml
```
```yml
---
#System Settings
php_modules: [ 'php-curl', 'php-gd', 'php-mbstring', 'php-xml', 'php-xmlrpc', 'php-soap', 'php-intl', 'php-zip' ]

#Nginx Settings
http_host: "localhost"
http_conf: "localhost.conf"

#MySQL Settings
mysql_root_password: "mysql_root_password"
mysql_db: "wordpress"
mysql_user: "wordpress"
mysql_password: "password"

user: iitbdrf
wp_dir: wordpress
```

### 3. Run the Playbook

```command
ansible-playbook -l [target] -i [inventory file] -u [remote user] playbook.yml
```
