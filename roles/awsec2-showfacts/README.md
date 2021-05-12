awsec2-showfacts
=========

Shows facts for all EC2 instances containing the AWS Tag `role: value` where `value` is the value of the `tag_role` variable.

Requirements
------------

* boto3
  * `$ pip3 install boto3 --user`

Role Variables
--------------

* region
* tag_role

Example Playbook
----------------

```yaml
- hosts: localhost
  roles:
    - { role: roles/awsec2-showfacts, region: us-east-1, tag_role: client_rhel }
```

License
-------

MIT

Author Information
------------------

Joe Garcia, DevOps Security Engineer, CyberArk - [Twitter](https://twitter.com/Joe_Garcia)