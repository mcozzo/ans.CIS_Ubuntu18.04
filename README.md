# CIS hardening Ubuntu 18.04
ansible-playbook -i hosts site.yml

## Readme:
### Configure grub password 
Section 1.4 Please follow the directions and update the password for the GRUB template file

## Getting started 

### Setting up WSL & linux 
https://docs.microsoft.com/en-us/windows/wsl/install-on-server <br>
https://docs.microsoft.com/en-us/windows/wsl/install-manual <br> 
https://docs.microsoft.com/en-us/windows/wsl/initialize-distro <br>

### Update WSL
From inside your WSL linux edition.
```bash
sudo apt-get update
sudo apt-get upgrade
```
### Pulling config from git
Create a folder, initialize git, pull the repo
```bash
mkdir ~/git
mkdir ~/git/ans.CIS_Ubuntu18.04
cd ~/git/ans.CIS_Ubuntu18.04
git init
git@github.com:mcozzo/ans.CIS_Ubuntu18.04.git
```

### To run plays 
```bash
# Run against test
ansible-playbook -i test site.yml
# Run against prod
ansible-playbook -i prod site.yml
```
If you only want to run specific plays
```bash
ansible-playbook -i test site.yml --tags <tag>
ansible-playbook -i test site.yml --tags CIS_1,CIS_2.1
```
## Commit changes / backup config
```bash
git add *
git commit -m "<Change This>"
git push -u origin master 
```

