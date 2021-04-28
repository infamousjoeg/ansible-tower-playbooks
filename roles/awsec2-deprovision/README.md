awsec2-deprovision
=========

Deprovisions an EC2 instance in AWS based on `tag_role` value provided.

Requirements
------------

* boto3
  * `$ pip3 install boto3`

Role Variables
--------------

* region
* tag_role

Example Playbook
----------------

```yaml
    - hosts: localhost
      roles:
         - { role: roles/awsec2-deprovision, tag_role: client_ubuntu }
```

License
-------

MIT

Author Information
------------------

Joe Garcia, DevOps Security Engineer, CyberArk - [Twitter](https://twitter.com/Joe_Garcia)
