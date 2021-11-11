# ansible-lab04 Security vaulting and keypairs  


## firstly the content of credentials file is :

```javascript
---
ansible_password: admin
```

## credentials file vaulting :
 
``` bash
[admin@node1 ~]$ ansible-vault encrypt files/secrets/credentials.yml
```

``` bash
[admin@node1 ~]$ cat files/secrets/credentials.yml
```

## output :
```javascript
$ANSIBLE_VAULT;1.1;AES256
35356630336536643530623362643733323062323562636166376130333536373166643239353663
3265663934363261306563393564353864656337386632380a316138326436613163356561623765
62303337393263643563643032306234303636323463356433383031353731633133313562333365
3463376365373032360a663833643436393432353939653033393238386438313065346266366532
32383436616665633366363531616136306438326637323333353531666638663631663933396438
3064643761646639643561346634353237363436626131343633
```
## delete ansible_password in group_vars/prod.yml, now its content is:


```javascript
ansible_user: admin
```

## use the var files in the playbook deploy.yml :
```javascript
...
var_files:
 - files/secrets/credentials.yml
 ...
```

## command to run the playbook :
``` bash
[admin@node1 webapp]$ ansible-playbook -i hosts.yml --ask-vault-pass deploy.yml
```
## output :

```javascript
[admin@node1 webapp]$ ansible-playbook -i hosts.yml --ask-vault-pass deploy.yml 
BECOME password:
Vault password: 

PLAY [httpd install play] ******************************************************

TASK [Gathering Facts] *********************************************************
ok: [client]

TASK [download python pip script] **********************************************
ok: [client]

TASK [install python-pip] ******************************************************
ok: [client]

TASK [install docker python] ***************************************************
ok: [client]

TASK [create httpd container] **************************************************
ok: [client]

PLAY RECAP *********************************************************************
client                     : ok=5    changed=0    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0   
```


## to locate the ansible_password variable, we run:

``` bash
[admin@node1 webapp]$ grep -r "ansible_password"
```

## update credentials.yml:


```javascript
---
ansible_user: admin
ansible_password: "{{ vault_ansible_password }}"
```
## encrypt again the credentials.yml:

``` bash
[admin@node1 ~]$ ansible-vault encrypt files/secrets/credentials.yml
[admin@node1 webapp]$ grep -r "ansible_password"
```

## output

```javascript
group_vars/prod.yml:ansible_password: "{{ vault_ansible_password }}
```



