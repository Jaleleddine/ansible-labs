# ansible-lab1

## command:

``` bash
[admin@node1 ~]$ ansible -i hosts all -m ping 
```

## output:

```javascript

10.0.3.4 | SUCCESS => {
    "ansible_facts": {
        "discovered_interpreter_python": "/usr/bin/python"
    }, 
    "changed": false, 
    "ping": "pong"
} 

```

