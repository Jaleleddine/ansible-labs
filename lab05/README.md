# ansible-lab04 Templating Loop Condition

``` bash
[admin@node1 ~]$ ansible-playbook -i hosts.yml deploy.yml
```

## output :

```javascript
[root@node1 webapp]# ansible-playbook -i hosts.yml deploy.yml 
BECOME password: 

PLAY [httpd install play] ******************************************************

TASK [Gathering Facts] *********************************************************
ok: [client]

TASK [download python pip script] **********************************************
ok: [client]

TASK [install python-pip] ******************************************************
ok: [client]

TASK [install docker python] ***************************************************
ok: [client]

TASK [install yum and git] *****************************************************
ok: [client] => (item=git)
changed: [client] => (item=wget)

TASK [Copie template to client] ************************************************
changed: [client]

TASK [create httpd container] **************************************************
changed: [client]

PLAY RECAP *********************************************************************
client                     : ok=7    changed=3    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0   
```

 












