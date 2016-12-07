Role Name
=========

Installs AWS CloudWatch Log Agent

Requirements
------------

Requires ec2_facts. 

Role Variables
--------------

List of logs with the following keys

| Name       | Description            | Required
|------------|------------------------|---------
| file       | Full path to log file  | Yes
| format     | Datetime format        | No
| group_name | CloudWatch Log Group   | Yes

Note: extra_logs is identical to logs.
The two variables are merged in the template in order to allow the definition of both 'system' logs and 'specific' logs.

Dependencies
------------

This role has no dependencies. 

Example Playbook
----------------

    - hosts: servers
      vars:
        logs:
          - file: /var/log/auth.log
            format: "%b %d %H:%M:%S"
            group_name: "auth"
          - file: /home/ubuntu/.bash_history
            group_name: "bash_history"
      roles:
         - { role: dharrisio.aws-cloudwatch-logs }

License
-------

GPLv3

Author Information
------------------

Created by David Harris
