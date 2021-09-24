cyberark-lamp
=========

Deploys a LAMP stack (Linux, Apache, MySQL, PHP) in a secure manner. All secrets are randomized and immediate stored in [CyberArk Conjur Secrets Manager](https://conjur.org) for management. All secrets are retrieved from [CyberArk Conjur Secrets Manager](https://conjur.org) for use within the play using custom credential types or [Ansible Automation Platform Secrets Management Systems](https://docs.ansible.com/ansible-tower/latest/html/userguide/credential_plugins.html).

Requirements
------------

* PyMySQL
  * `$ pip3 install pymysql --user`
* community.general
  * `$ ansible-galaxy collection install community.general`
* community.mysql
  * `$ ansible-galaxy collection install community.mysql`

Role Variables
--------------

* app_user
* http_host
* http_conf
* http_port
* disable_default

Dependencies
------------

* [roles/awsec2-showfacts](../awsec2-showfacts)

Example Playbook
----------------

```yaml
    - hosts: localhost
      roles:
        - { role: roles/cyberark_lamp.yml, app_user: ubuntu, http_host: lampdemo.joegarcia.dev, http_conf: lampdemo.conf, http_port: 80, disable_default: true}
```

**NOTE:** In Ansible Tower, `extra_vars` can be provided in the Job Template rather than in the playbook.

License
-------

MIT

Author Information
------------------

Joe Garcia, DevOps Security Engineer, CyberArk - [Twitter](https://twitter.com/Joe_Garcia)
