# Wordpress on Ubuntu 20.04 LEMP

This playbook will install a WordPress website on top of a LEMP environment (**L**inux, **E**gine-x, **M**ariaDB and **P**HP) on an Ubuntu 20.04 machine. A virtualhost will be created with the options specified in the `vars/default.yml` variable file.

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
git clone https://github.com/do-community/ansible-playbooks.git
cd ansible-playbooks/wordpress-lamp_ubuntu1804
```

### 2. Customize Options

```shell
nano vars/default.yml
```

```yml
---
#System Settings
php_modules: [ 'php-curl', 'php-gd', 'php-mbstring', 'php-xml', 'php-xmlrpc', 'php-soap', 'php-intl', 'php-zip' ]

#MySQL Settings
mysql_root_password: "mysql_root_password"
mysql_db: "wordpress"
mysql_user: "sammy"
mysql_password: "password"

#HTTP Settings
http_host: "your_domain"
http_conf: "your_domain.conf"
http_port: "80"
```

### 3. Run the Playbook

```command
ansible-playbook -l [target] -i [inventory file] -u [remote user] playbook.yml
```

For more information on how to run this Ansible setup, please check this guide: [How to Use Ansible to Install and Set Up WordPress with LAMP on Ubuntu 18.04](https://www.digitalocean.com/community/tutorials/how-to-use-ansible-to-install-and-set-up-wordpress-with-lamp-on-ubuntu-18-04).
