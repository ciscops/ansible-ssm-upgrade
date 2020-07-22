# ansible-ssm-upgrade
An ansible role designed for patching the Cisco Smart Software Manager Satellite.

# Usage
The patch playbook will require that two files are present in the playbook directory. You will need the respective SSM_On-Prem_*_Upgrade.sh and SSM_On-Prem_*_Upgrade.sh.sha256 files for the version you're upgrading to. For example:
```
SSM_On-Prem_8-202006_Upgrade.sh
SSM_On-Prem_8-202006_Upgrade.sh.sha256
```

Once these files are present you will need to edit the patch.yml to your required version, upgrade file, and checksum files. Once this has been completed you can run as: 

```
ansible-playbook patch.yml
```
