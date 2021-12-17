cybr-cli-deploy
=========

Deploys the latest deployed [cybr-cli](https://github.com/infamousjoeg/cybr-cli) binary onto a newly provisioned EC2 instance. The binary is downloaded from AWS S3.

Requirements
------------

* `amazon.aws` Collection
  * `$ ansible-galaxy collection install amazon.aws`
* boto3
  * `$ python3 -m pip install boto3 --user`
* CyberArk Privilege Custom Credential Type
  * (https://github.com/infamousjoeg/ansible-tower-playbooks/tree/master/custom_credtypes/cyberark_privilege_restapi)[https://github.com/infamousjoeg/ansible-tower-playbooks/tree/master/custom_credtypes/cyberark_privilege_restapi]

Role Variables
--------------

Role variables will be consumed using the `env` lookup plugin to inject credentials provided by the [CyberArk Privilege Custom Credential Type](https://github.com/infamousjoeg/ansible-tower-playbooks/tree/master/custom_credtypes/cyberark_privilege_restapi).

Example Playbook
----------------

##### tasks/main.yml

```yaml
---
- name: Download Latest Release
  amazon.aws.aws_s3:
    bucket: cybr-cli-releases
    object: "{{ ansible_date_time.date }}_linux_cybr"
    dest: /usr/local/bin/cybr
    mode: get
- name: Login to cybr-cli for PAS
  ansible.builtin.command: |
    "cybr logon -u {{ cyberark.username }} -a {{ cyberark.auth_type }} -b {{ cyberark.pvwa_url }} -p {{ cyberark.password }} --non-interactive"
  register: cybrlogon
```

##### vars/main.yml

```yaml
---
cyberark:
  pvwa_url: '{{ lookup("env", "CYBERARK_APU_URL") }}'
  auth_type: '{{ lookup("env", "CYBERARK_API_AUTH_TYPE") }}'
  username: '{{ lookup("env", "CYBERARK_API_USERNAME") }}'
  password: '{{ lookup("env", "CYBERARK_API_PASSWORD") }}'
```

License
-------

MIT

Author Information
------------------

Joe Garcia, DevOps Security Engineer, CyberArk - [Twitter](https://twitter.com/Joe_Garcia)
