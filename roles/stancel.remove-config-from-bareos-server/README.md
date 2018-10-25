remove-config-from-bareos-server
=========

Removes the Bareos configuration files for a given host/computer as they were setup by my [add-job-to-bareos-director Ansible role](https://github.com/stancel/add-job-to-bareos-director).

Requirements
------------

Bareos Server and your configuration files setup like those from my [add-job-to-bareos-director Ansible role](https://github.com/stancel/add-job-to-bareos-director).

Role Variables
--------------

The hostname of the machine you are removing

	`remove_config_from_bareos_server_host_name: "hostname-of-machine-to-remove"'

The Bareos Archive Device location (or file path) where the backups volumes are stored for this host. Make sure you do NOT put a path here that has backup volumes for other hosts. Below is the default value that will be populated if not overridden.

	`remove_config_from_bareos_server_archive_device: "/z-storage/backups/{{ host_name }}"`

Dependencies
------------

None

Example Playbook
----------------

	- hosts: your_bareos_server
	  vars_files:
	    - vars/main.yml
	  roles:
	    - { role: stancel.remove-config-from-bareos-server }


or 


	- hosts: your_bareos_server
	  vars:
		remove_config_from_bareos_server_host_name: "hostname-of-machine-to-remove"
		remove_config_from_bareos_server_archive_device: "/path/to/bareos/backup/volumes/for/this/host/only"
	  roles:
	    - stancel.remove-config-from-bareos-server

License
-------

BSD

Author Information
------------------

[Brad Stancel](https://github.com/stancel)
