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