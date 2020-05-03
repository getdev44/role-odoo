# Role Odoo

Deploy odoo 10 via ansible


# Usage

## Prerequisite

Read ```meta/main.yml``` file to have default.

## Variables

### Password variable to set

```
odoo_pass:
  admin: 'password' # MANDATORY
```

### Others variables

```
in_odoo:
  conf:
    db:
      user: "odoo"
# Copier ses lignes dans l'inventory, sinon elles ne sont pas prise en compte
#  packages:
#    - { "cle" : "yum-utils", "version" : "1.1.31-40.el7.noarch" }
  dns_name: odoo.exemple.com
  nginx_available_conf: /etc/nginx/sites-available/odoo.conf
  nginx_enabled_conf: /etc/nginx/sites-enabled/odoo.conf
  nginx_ssl_key: /etc/ssl/nginx/odoo.key
  nginx_ssl_crt: /etc/ssl/nginx/odoo.crt
  url_html2pdf: https://github.com/wkhtmltopdf/wkhtmltopdf/releases/download/0.12.4/wkhtmltox-0.12.4_linux-generic-amd64.tar.xz
  wkhtlktox: /tmp/wkhtlktox.tar.xz
  packages:
```

```
in_odoo_web:
# Copier ses lignes dans l'inventory, sinon elles ne sont pas prise en compte
#  packages:
#    - { "cle" : "yum-utils", "version" : "1.1.31-40.el7.noarch" }
#  dns_name: odoo.exemple.com
  nginx_available_conf: /etc/nginx/sites-available/odoo-web.conf
  nginx_enabled_conf: /etc/nginx/sites-enabled/odoo-web.conf
  nginx_ssl_key: /etc/ssl/nginx/odoo-web.key
  nginx_ssl_crt: /etc/ssl/nginx/odoo-web.crt
  dns_name: 
```

## Usage

In a playbook, include this role in galaxy file and then :
```
- name: "Installing odoo"
  hosts: odoo
  become: yes
  tasks:
  - include_role:
      name: role-odoo
```
