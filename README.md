# CIS hardening Ubuntu 18.04
This runs against a set of ubuntu 18.04 hosts and configures the system based on CIS v1.0.0 recommendations. 
At least L1 settings, some L2 stuff where it was easy to add.

## Readme notes
### Make sure to set your variables
* Section 1.4 Please follow the directions and update the password for the GRUB template file. 
* Look at the ToDo items. there's some stuff that isn't 100% complete, as expected. 

## Getting started 
### Setting up environment
#### Install WSL
Skip if your running from Linux / Mac
* https://docs.microsoft.com/en-us/windows/wsl/install-on-server
* https://docs.microsoft.com/en-us/windows/wsl/install-manual     
* https://docs.microsoft.com/en-us/windows/wsl/initialize-distro 

#### Update APT
Update apt, and upgrade packages
```bash
sudo apt-get update
sudo apt-get upgrade
```

#### Install Ansible 
https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html#installing-ansible-on-ubuntu 
```bash
apt update
apt install software-properties-common
apt-add-repository --yes --update ppa:ansible/ansible
apt install ansible
```

### Pull config from git
Git should already be installed, if not, install with apt. 
```bash
apt update
apt install git
```
Create a folder, initialize git, pull the repo.
```bash
mkdir ~/git
mkdir ~/git/ans.CIS_Ubuntu18.04
cd ~/git/ans.CIS_Ubuntu18.04
git init
git pull https://github.com/mcozzo/ans.CIS_Ubuntu18.04.git
```

### To run plays 
```bash
# Run against test
ansible-playbook -i site-test.yml site-play.yml
# Run against prod
ansible-playbook -i site-prod.yml site-play.yml
# Run service account creation
ansible-playbook -i site-test.yml site-play.yml --tags user -e "ansible_ssh_user=mattcozzolino" --ask-pass -K
```
If you only want to run specific plays
```bash
ansible-playbook -i site-test.yml site-play.yml --tags <tag>
# E.G.
ansible-playbook -i site-test.yml site-play.yml --tags CIS_1,CIS_2.1
```

## Commit changes / backup config
Probably want to fork and write to your own repository. Or, contact me and you can update this repository.
```bash
git add *
git commit -m "<Change This>"
git push -u origin master 
```

## ToDo
- [ ] CIS_1.7    - collapse all of the lineinfile to a single play, using with_items
- [ ] CIS_2.2    - Clean up service shutdown/removal
- [ ] CIS_3.2    - collapse all of the lineinfile to a single play, using with_items
- [ ] CIS_5.2.11 - MACs config is currently disabled. Need to add version to ansible run
- [ ] CIS_5.2.14 - Set the appropriate variables in group_vars/all.yml
- [ ] CIS_5.2.14 - Uncomment allow/deny lines in roles/CIS_5.2/tasks/main.yml
- [ ] CIS_6.2    - Mostly copy & run scripts. Need some better logic to run against "discovered folders"