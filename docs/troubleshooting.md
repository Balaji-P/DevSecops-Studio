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
