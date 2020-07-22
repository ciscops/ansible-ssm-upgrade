# ansible-ssm-upgrade
An ansible role designed for patching the Cisco Smart Software Manager Satellite.

## Prerequisites
The following tools will need to be installed on your system:
  - ansible
  - SSHPass

## Update Directory File
We have included a sample directory but you will need to update the directory with your hosts, usernames, and passwords before you run the playbook.

## SSM OnPrem Patch
The patch playbook will require that two files are present in the playbook directory. You can find the most recent patch here:  https://software.cisco.com/download/home/286285506/type/286285517/os/Linux/release/8-202006

 - download the desired Upgrade.zip
 - unzip the file
 - copy the following .sh and .sh.sha256 to your playbook directory

```
SSM_On-Prem_8-202006_Upgrade.sh
SSM_On-Prem_8-202006_Upgrade.sh.sha256
```

Once these files are present you will need to edit the patch.yml to your required version, upgrade file, and checksum files. Once this has been completed you can run as: 

```
ansible-playbook patch.yml
```
