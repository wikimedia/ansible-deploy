# Ansible experiments

## Simple rolling deployment / restart scripts for restbase

This runs a command on each of the hosts, then checks for a port to become
available:

Test:
```bash
ansible-playbook -i hosts restbase/deploy-staging.yml --check
```
To run this for real:
```bash
ansible-playbook -i hosts restbase/deploy-staging.yml

PLAY [restbase-staging]
*******************************************************

GATHERING FACTS
***************************************************************
ok: [xenon.eqiad.wmnet]
ok: [cerium.eqiad.wmnet]
ok: [praseodymium.eqiad.wmnet]

TASK: [check out the deploy repo]
*********************************************
ok: [cerium.eqiad.wmnet]

TASK: [wait for restbase to come up]
******************************************
ok: [cerium.eqiad.wmnet]

TASK: [check out the deploy repo]
*********************************************
ok: [praseodymium.eqiad.wmnet]

TASK: [wait for restbase to come up]
******************************************
ok: [praseodymium.eqiad.wmnet]

TASK: [check out the deploy repo]
*********************************************
ok: [xenon.eqiad.wmnet]

TASK: [wait for restbase to come up]
******************************************
ok: [xenon.eqiad.wmnet]

PLAY RECAP
********************************************************************
cerium.eqiad.wmnet         : ok=3    changed=0    unreachable=0    failed=0
praseodymium.eqiad.wmnet   : ok=3    changed=0    unreachable=0    failed=0
xenon.eqiad.wmnet          : ok=3    changed=0    unreachable=0    failed=0


real    0m15.613s
user    0m0.272s
sys     0m0.084s
```

