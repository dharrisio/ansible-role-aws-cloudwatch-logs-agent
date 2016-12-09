Role Name
=========

Installs AWS CloudWatch Log Agent

Requirements
------------

Requires ec2_facts.

Role Variables
--------------

List of logs with the following keys

| Name        | Description                | Required | Default
|-------------|----------------------------|----------|---------
| file        | Full path to log file      | Yes      |
| format      | Datetime format            | No       | None
| group_name  | CloudWatch Log Group       | Yes      |
| stream_name | CloudWatch Log Stream Name | No       | The instance id

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
            stream_name: "auth-stream"
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
