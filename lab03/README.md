# ansible-lab03

## command 1: ping

``` bash
[admin@node1 ~]$ ansible -i hosts all -m ping 
```


## command 2: ping

``` bash
[admin@node1 ~]$ ansible -i prod all -m ping 
```


## command 3: ping

``` bash
[admin@node1 ~]$ ansible -i client all -m ping 
```

## output :

```javascript

10.0.0.4 | SUCCESS => {
    "ansible_facts": {
        "discovered_interpreter_python": "/usr/bin/python"
    }, 
    "changed": false, 
    "ping": "pong"
} 

```
## command 4: create file

``` bash
[admin@node1 ~]$ ansible -i hosts all -m copy -a "dest=/home/admin/toto.txt content='bonjour eazytraining {{env}}'" 
```



