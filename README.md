# ansible-ssm-upgrade
This repo contains an Ansible playbook that will upgrade the software on your Cisco Smart Software Manager On-Prem.  

## Prerequisites
The following tools will need to be installed on your system:
  - Ansible (Required to run Ansible playbooks.  The install instructions here:  https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html)
  - SSHPass (This package allows ansible to ssh in to your OnPrem with your supplied username and password.  To install on Ubuntu: `apt-get install sshpass`.)

## Update Directory File
A sample inventory file is included.  Prior to running the playbook, you will need to update the host, username, and password variables to match your environment.

## SSM OnPrem Patch
The patch playbook requires that two files are present in the same directory as the playbook. Visit [software.cisco.com](https://software.cisco.com) to download the upgrade images.

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

Once the steps above have been completed you can run the playbook with this command: 

```
ansible-playbook patch.yml -e version=<desired_version>
```
### Please Note:  This process can take some time depending on your upload/download speeds as it must first scp the files, then run the upgrade.  The process can take 15 minutes to an hour depending on the size of your database.  Always take a snapshot or database back-up before beginning the upgrade process. 
