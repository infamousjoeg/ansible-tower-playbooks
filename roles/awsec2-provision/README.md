awsec2-provision
=========

Provisions an EC2 instance in AWS based on variable values provided.

Requirements
------------

* boto3
  * `$ python3 -m pip install boto3 --user`

Role Variables
--------------

* ami_id
* assign_public_ip
* instance_tags_name
* instance_tags_role
* keypair
* region
* security_group
* subnet
* type

Example Playbook
----------------

```yaml
    - hosts: localhost
      roles:
         - { role: roles/awsec2-provision, ami_id: ami-123456789, instance_tags_name: Ubuntu Client, instance_tags_role: client_ubuntu }
```

**NOTE:** In Ansible Tower, `extra_vars` can be provided in the Job Template rather than in the playbook.

License
-------

MIT

Author Information
------------------

Joe Garcia, DevOps Security Engineer, CyberArk - [Twitter](https://twitter.com/Joe_Garcia)
