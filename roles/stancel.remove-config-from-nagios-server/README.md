remove-config-from-nagios-server
=========

Basic Ansible role to remove a server from being monitored by Nagios. 

Requirements
------------

Assumes that your Nagios Server is installed in the following path `/usr/local/nagios`

Role Variables
--------------

The hostname of the machine you are removing from being monitored by Nagios. Host names should not have spaces in them.

	`remove_config_from_nagios_server_host_name: "my-server" `  

Dependencies
------------

None

Example Playbook
----------------

	- hosts: your_nagios_server
	  vars_files:
	    - vars/main.yml
	  roles:
	    - { role: stancel.remove-config-from-nagios-server }


or 

	- hosts: your_nagios_server
	  vars:
		remove_config_from_nagios_server_host_name: "my-server-to-remove"
	  roles:
	    - stancel.remove-config-from-nagios-server 

License
-------

BSD

Author Information
------------------

[Brad Stancel](https://github.com/stancel)


