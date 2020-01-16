# CIS hardening Ubuntu 18.04
ansible-playbook -i hosts site.yml

## To run: 
```bash
ansible-playbook -i test site.yml
```
If you only want to run specific plays
```bash
ansible-playbook -i test site.yml --tags <tag>
ansible-playbook -i test site.yml --tags CIS_1,CIS_2.1
```

## Commit to git
```bash
git add *
git commit -m "<Change This>"
git push -u origin master 
```

## Grub password 
Section 1.4 Please follow the directions and update the password for the GRUB template file

### Setting up WSL & linux 
https://docs.microsoft.com/en-us/windows/wsl/install-on-server <br>
https://docs.microsoft.com/en-us/windows/wsl/install-manual <br> 
https://docs.microsoft.com/en-us/windows/wsl/initialize-distro <br>

### Pulling config from git
From inside your WSL linux edition. <br>
Update linux
```bash
sudo apt-get update
sudo apt-get upgrade
```
Create a folder, initialize git, pull the repo
```bash
mkdir ~/git
mkdir ~/git/ans.CIS_Ubuntu18.04
cd ~/git/ans.CIS_Ubuntu18.04
git init
git@github.com:mcozzo/ans.CIS_Ubuntu18.04.git
```