# ansible-lab2

## command 1: create file

``` bash
[admin@node1 ~]$ ansible -i hosts all -m copy -a "dest=/home/admin/toto.txt content='bonjour eazytraining'"
```

## output 1:

```javascript

10.0.0.4 | CHANGED => {
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
    "src": "/home/admin/.ansible/tmp/ansible-tmp-1634388050.22-141-208252509466933/source", 
    "state": "file", 
    "uid": 1000
}
10.0.0.5 | CHANGED => {
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
    "src": "/home/admin/.ansible/tmp/ansible-tmp-1634388050.21-139-23851947426877/source", 
    "state": "file", 
    "uid": 1000
}

```

