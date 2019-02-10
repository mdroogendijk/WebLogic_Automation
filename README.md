Automated Oracle Fusion Middleware patching and stop/starting with Ansible
=======================

Playbooks for automated activities for WebLogic 11g/12c (tbc), SOA, OSB and WebGate Agents.

Requirements
------------

- Sufficient sudo access, f.e. %User ALL=(weblogic) ALL, /bin/bash -c

Dependencies
------------

- Ansible installed on a host
- SSH access from Ansible Controller to FMW hosts

Example #1 - WebLogic/OSB/SOA
------------

## Dry-run with Ansible check mode
$ ansible-playbook wls.yml - inventories/wls_inv.yml --ask-pass --ask-become-pass --check -e "@templates/patch_wls.json"

## Patch WebLogic
$ ansible-playbook wls.yml - inventories/wls_inv.yml --ask-pass --ask-become-pass -e "@templates/patch_wls.json"

## Patch SOA
$ ansible-playbook wls.yml - inventories/wls_inv.yml --ask-pass --ask-become-pass -e "@templates/patch_soa.json"

## Rollback WebLogic patches
$ ansible-playbook wls.yml - inventories/wls_inv.yml --ask-pass --ask-become-pass -e "@templates/rollback_wls.json"

## Restart WebLogic servers
$ ansible-playbook wls.yml - inventories/wls_inv.yml --ask-pass --ask-become-pass -t restart

## Restore backup(s) created earlier for WebLogic servers
$ ansible-playbook wls.yml - inventories/wls_inv.yml --ask-pass --ask-become-pass -e "@templates/restore_backup.json"


Example #2 - WebGate Agents
------------

## Dry-run with Ansible check mode
$ ansible-playbook webgate.yml - inventories/webgate_inv.yml --ask-pass --ask-become-pass --check -e "@templates/patch_webgate.json"

## Patch WebGate
$ ansible-playbook webgate.yml - inventories/webgate_inv.yml --ask-pass --ask-become-pass -e "@templates/patch_webgate.json"

## Rollback WebGate patches
$ ansible-playbook webgate.yml - inventories/webgate_inv.yml --ask-pass --ask-become-pass -e "@templates/rollback_webgate.json"

## Restart webservers
$ ansible-playbook webgate.yml - inventories/webgate_inv.yml --ask-pass --ask-become-pass -t restart

## Restore backup(s) created earlier for WebGate
$ ansible-playbook webgate.yml - inventories/webgate_inv.yml --ask-pass --ask-become-pass -e "@templates/restore_backup.json"