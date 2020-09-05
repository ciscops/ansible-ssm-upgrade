# ansible-ssm-upgrade
This ansible playbook provides automation to upgrade your Cisco Smart Software Manager On-Prem to your desired verson.  

## Prerequisites
The following tools will need to be installed on your system:
  - ansible (you can find install instructions here:  https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html)
  - SSHPass (this package allows ansible to ssh in to your OnPrem with your supplied user and password.)

## Update Directory File
We have included a sample directory but you will need to update the directory file with your hosts, usernames, and passwords before you run the playbook.

## SSM OnPrem Patch
The patch playbook will require that two files are present in the playbook directory. You can find the most recent patch here:  https://software.cisco.com/download/home/286285506/type/286285517/os/Linux/release/8-202006

 - download the desired Upgrade.zip
 - unzip the file
 - copy the following .sh and .sh.sha256 to your playbook directory

```
SSM_On-Prem_8-202006_Upgrade.sh
SSM_On-Prem_8-202006_Upgrade.sh.sha256
```
After the files are copied, you will need to make them executable using the commands below:
```
chmod +x SSM_On-Prem_8-202006_Upgrade.sh
chmod +x SSM_On-Prem_8-202006_Upgrade.sh.sha256
```

Once these files are present you will need to edit the patch.yml to your desired version, upgrade file, and checksum files. Once the steps above have been completed you can run the playbook with this command: 

```
ansible-playbook patch.yml e- version=<desired_version>
```
