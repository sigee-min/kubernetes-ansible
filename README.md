# kubernetes-ansible

### Requirements
1. /tmp/inventory.ini
```text
[masters]
%{ for addr in master_addrs ~}
${addr}
%{ endfor ~}
[workers]
%{ for addr in worker_addrs ~}
${addr}
%{ endfor ~}
[kubernetes:children]
masters
workers

```

2. /tmp/private.key
3. ~/.ansible.cfg
```text
[defaults]
host_key_checking = False
```

### Exec
```bash
ansible-playbook main.yml -i /tmp/inventory.ini
```