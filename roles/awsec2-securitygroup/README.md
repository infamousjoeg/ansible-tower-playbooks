awsec2-securitygroup
=========

Adds or removes an EC2 Security Group for temporary access to/from an EC2 Instance.

Requirements
------------

* boto3
  * `$ python3 -m pip install boto3 --user`

Role Variables
--------------

* region
* pasaas_vpc_id
* conjur_instance_id
* conjur_sg
* pasaas_external_sg
* pasaas_internal_sg
* ssh_sg
* update
* ip_address

Example Playbook
----------------

```yaml
    - hosts: localhost
      roles:
         - { role: roles/awsec2-securitygroup, update: yes, ip_address: 0.0.0.0/32 }
```

**NOTE:** In Ansible Tower, `extra_vars` can be provided in the Job Template rather than in the playbook.

License
-------

MIT

Author Information
------------------

Joe Garcia, DevOps Security Engineer, CyberArk - [Twitter](https://twitter.com/Joe_Garcia)
