# Ansible expirements

## Rolling action (simulation for deploy) on each host

This runs a command on each of the hosts, then checks for a port to become
available:

Test:
```bash
ansible-playbook -f10 -i hosts rolling-deploy/restbase.yml --check
```
To run this for real:
```bash
ansible-playbook -f10 -i hosts rolling-deploy/restbase.yml
```
