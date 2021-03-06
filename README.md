sbog/postfix
============

Role to install Postfix and Postfixadmin

#### Requirements

Ansible 2.4

#### Role Variables

```yaml
postfix_packages:
  - postfix
  - sasl2-bin
  - postfix-mysql
  - mysql-client
  - mysql-server
  - libsasl2-2
  - libsasl2-modules
  - libsasl2-modules-sql
  - openssl
mail_domain: example.ru
mail_hostname: mail.example.ru
mail_ssl_enabled: true
mx_hosts:
  - mail.example.ru
  - smtp.example.ru
  - imap.example.ru
check_policy:
  enabled: true
  address: "127.0.0.1"
  port: 10023
dkim:
  enabled: false
  milter_address: "127.0.0.1"
  milter_port: 8891
spamassassin:
  enabled: false
postfix_db_user: postfix
postfix_db_password: postfixpassword
postfix_db_host: "127.0.0.1"
postfix_db_name: postfix
mysql_port: 3306
mysql_bind_address: "127.0.0.1"
mysql_root_db_pass: mysqlroot
mysql_users:
  - name: postfix
    pass: postfixpassword
    priv: "postfix.*:ALL"
  - name: postfixadmin
    pass: pfxadmpass
    priv: "postfix.*:ALL"
mysql_db:
  - name: postfix
    replicate: no
postfixadmin_db_password: pfxadmpass
postfixadmin_superuser: admin
postfixadmin_superpass: adminpassword
```

#### Dependencies

bennojoy.mysql

#### Example Playbook

```yaml
- name: Install Postfix and Postfixadmin
  hosts: localhost
  remote_user: root
  roles:
    - postfix
```

#### License

Apache 2.0

#### Author Information

Stanislaw Bogatkin (https://sbog.ru)
