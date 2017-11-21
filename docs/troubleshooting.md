# Troubleshooting Guide
This guide helps you in troubleshooting common errors in DevSecOps Studio.

## Ansible Galaxy

1. If you get any error while installing roles using ansible-galaxy

	```bash
	$ ansible-galaxy install -r requirements.yml -p provisioning/roles
	```
	
	> downloading role 'pip', owned by geerlingguy
	
	> __ERROR!__ Unexpected Exception:
	> \<urlopen error ('_ssl.c:645: The handshake operation timed out',)>

	
	__Fix__: Try running the command again, it should resolve itself.

2. If download appears to be stuck.

	__Fix__: kill the command using Ctrl+C and re-run the command.

## Playbook (vagrant up)
1. If you encounter any errors while doing vagrant up, note down the role you are currently running.

The following snippet is shows that jenkins role is being executed at the moment.

> TASK [**jenkins**: Install Jenkins]


## Virtualbox

1. Virtualbox just crashes the guest machines with aborted status.
   Fix: Ensure you have enough memory (4B) free, if not close few programs and then run `vagrant up` from DevSecOps-Studio directory.
