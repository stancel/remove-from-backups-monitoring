remove-from-backups-monitoring
=========

Ansible role to remove a given host (hostname) from my backup system, Bareos, and monitoring system, Nagios4.

How to Use
------------

To use this playbook just run this command.

	1. ansible-galaxy install -r requirements.yml -p roles/ --force
	2. ansible-playbook master.yml -e @vars/all_vars.yml -i hosts/production


Requirements
------------

Used for personal / internal use. Must use Nagios for monitoring and Bareos for backups and have Bareos files laid out like I do in [this role I created](https://github.com/stancel/add-job-to-bareos-director)

Variables
------------

The hostname of the machine you are removing
```
	host_name: ""
```
The Bareos Archive Device location (or file path) where the backups volumes are stored for this host. *** Make sure you do NOT put a path here that has backup volumes for other hosts ***. The variable assignment for archive_device is listed below but can be overridden if you store your host specific backups in a different location.

```
	archive_device: "/z-storage/backups/{{ host_name }}"
```

Roles
------------

	- stancel.remove-config-from-bareos-server	
	- stancel.remove-config-from-nagios-server	

Additional Info
------------

I have setup a bash profile alias to allow calling the playbook and passing the host_name of the server as the first parameter.

```
alias remove-server='function _remove-server() { cd /Users/Brad/DevOps/Ansible_Playbooks/playbooks/remove-from-backups-monitoring; ansible-playbook master.yml --inventory-file=/Users/Brad/.ansible/hosts -e @vars/all_vars.yml --extra-vars "host_name=$1"; };_remove-server'
```