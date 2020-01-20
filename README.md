# CIS hardening Ubuntu 18.04
## Readme notes
### Configure grub password 
Section 1.4 Please follow the directions and update the password for the GRUB template file

### Configure logging host
Section 4.2 This could come out and be palced in a global variable

## Getting started 
### Setting up environment
#### Install WSL
https://docs.microsoft.com/en-us/windows/wsl/install-on-server <br>
https://docs.microsoft.com/en-us/windows/wsl/install-manual <br> 
https://docs.microsoft.com/en-us/windows/wsl/initialize-distro <br>

#### Update APT
```bash
sudo apt-get update
sudo apt-get upgrade
```

#### Install Ansible 
```bash
sudo apt update
sudo apt install software-properties-common
sudo apt-add-repository --yes --update ppa:ansible/ansible
sudo apt install ansible
```

### Pulli config from git
Create a folder, initialize git, pull the repo
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
```bash
git add *
git commit -m "<Change This>"
git push -u origin master 
```

## ToDo
1. 3.2 collapse all of the lineinfile to a single play, using with_items
2. 1.7 collapse all of the lineinfile to a single play, using with_items
3. 2.2 Clean up service shutdown/removal