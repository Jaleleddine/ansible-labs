# ansible-lab1

## command 1:

``` bash
[admin@node1 ~]$ ansible -i hosts all -m ping 
```

## output 1:

```javascript

10.0.3.4 | SUCCESS => {
    "ansible_facts": {
        "discovered_interpreter_python": "/usr/bin/python"
    }, 
    "changed": false, 
    "ping": "pong"
} 

```


## command 2:

``` bash
ansible -i hosts all -m copy -a "dest=/home/admin/toto.txt content='bonjour eazytraining'" 
```

## output 2:
```javascript
10.0.2.4 | CHANGED => {
    "ansible_facts": {
        "discovered_interpreter_python": "/usr/bin/python"
    }, 
    "changed": true, 
    "checksum": "ba90e31f2c066fc3a9911d9ae26b89bfaf724198", 
    "dest": "/home/admin/toto.txt", 
    "gid": 1000, 
    "group": "admin", 
    "md5sum": "b79d3f8b9096bd05d3e06af490d8c2fd", 
    "mode": "0664", 
    "owner": "admin", 
    "size": 20, 
    "src": "/home/admin/.ansible/tmp/ansible-tmp-1634306885.84-112-243971746128726/source", 
    "state": "file", 
    "uid": 1000
}
```

