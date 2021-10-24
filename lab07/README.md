# ansible-lab07 Security vaulting and keypairs  (part2)


## generate public key 
``` bash
ssh-keygen -t rsa
```

```javascript
Generating public/private rsa key pair.
Enter file in which to save the key (/home/admin/.ssh/id_rsa): 
Created directory '/home/admin/.ssh'.
Enter passphrase (empty for no passphrase): 
Enter same passphrase again: 
Your identification has been saved in /home/admin/.ssh/id_rsa.
Your public key has been saved in /home/admin/.ssh/id_rsa.pub.
The key fingerprint is:
SHA256:KJTYut6vkgmz71uNbZ90v/NRKZzhVIIgtHMA7y4JzTo admin@node1
The key's randomart image is:
+---[RSA 2048]----+
|     .o+ .. .. . |
|   o .. +  .  o  |
|  . +  + .   o   |
|   oo ..o   + o .|
|  ...o..S    = ..|
|o  .o=o       .. |
| +.Eoo+.. .   .  |
|..+o...o o ..  . |
| o=ooo. o   o+.  |
+----[SHA256]-----+
```


## copy public key in the target machine (prod)
``` bash
[admin@node1 webapp]$ ssh-copy-id admin@10.0.0.4
[admin@node2 ~]$ cat .ssh/authorized_keys
``` 


```javascript
ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQDBhJxVo7GM039VnPpFoFbR//73ZIWiu/6cYyqhxfNrB8oa49j40fUgDSZuLWC51r0qNvm5hgEnJGCJYnY4t3rxZWAusHvYz9STA25j462TA22qbX9WnsHY1LRRa1QwI2EOpgU4zrL5TwRw+tUOIxmy3xCfRalAMEobfbcN+BYW4ueSiG5c667NkWyreenfemzNlBEYvYwZs7Ez8gHmp4hZGLdhjB0tKrWOTaOIJx0d30xuZMpCkStCs2GMzLa7UKKrn5RWXHfR4HLH6j/ZjRiz0jS1Pv3xK7c7HhAuEbOIaTDRPE7H+VO1+g61uJ0bRAIs9JRhyOw/ZQs2KRUGl4Db admin@node1
``` 
## prevent ansible from using the login and password authentication method (comment the password in prod.yml). The target machine is accessible via private key. 

```javascript
---
ansible_user: admin
#ansible_password: "{{ vault_ansible_password }}"
``` 

``` bash
[admin@node1 webapp]$ ansible-playbook -i hosts.yml --ask-vault-pass deploy.yml 
``` 



## now try to remotely connect to the target machine using password method. It will not be required to give the password

``` bash
---
ansible_user: admin
ansible_password: "{{ vault_ansible_password }}"
``` 

``` bash
[admin@node1 webapp]$ ssh 10.0.0.4
``` 

