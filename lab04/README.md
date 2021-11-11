# ansible-lab04

## command 1: ansible-lint install

``` bash
[admin@node1 ~]$ sudo pip install ansible-lint
```


## command 2: ansible-lint install playbook

``` bash
[admin@node1 ~]$ ansible-lint deploy.yml 
```


## command 3: ansible-playbook

``` bash
[admin@node1 ~]$ ansible-playbook -i hosts.yml deploy.yml
```

## output :

```javascript
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
## ansible-playbook (command 3) without "become: true" in deploy.ml which allows elevation of privileges (like sudo). This gives the following error 


```javascript
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
fatal: [client]: FAILED! => {"changed": false, "msg": "Error connecting: Error while fetching server API version: ('Connection aborted.', error(13, 'Permission denied'))"}

PLAY RECAP *********************************************************************
client                     : ok=4    changed=0    unreachable=0    failed=1    skipped=0    rescued=0    ignored=0 
```


## ansible-playbook (command 3) without "ansible_sudo_pass: admin" gives the following error





```javascript
PLAY [httpd install play] ********************************************************************************************************************************************

TASK [Gathering Facts] ***********************************************************************************************************************************************
fatal: [client]: FAILED! => {"msg": "Missing sudo password"}

PLAY RECAP ***********************************************************************************************************************************************************
client                     : ok=0    changed=0    unreachable=0    failed=1    skipped=0    rescued=0    ignored=0 
```

## deploy.yml content when we use ansible.cfg


```javascript
---
- name: httpd install play
  hosts: prod
  become: true
  pre_tasks:
    - name: download python pip script
      get_url:
        url: https://bootstrap.pypa.io/pip/2.7/get-pip.py
        dest: /tmp/get-pip.py
    - name: install python-pip
      command: python2.7 /tmp/get-pip.py
      changed_when: false
    - name: install docker python
      pip: name=docker-py
  tasks:
   - name: create httpd container
     docker_container:
        name: webapp
        image: httpd
        ports:
         - "80:80"
```
















