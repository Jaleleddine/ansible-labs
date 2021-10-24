# ansible-lab08 ansible roles  


## add requirements.yml file 
```javascript
# Install a role for wordpress
- src: https://github.com/diranetafen/ansible-role-containerized-wordpress.git
```

``` bash
ssh-keygen -t rsa
```

## wordpress.yml file

```javascript
---
- hosts: prod
  become: true
  vars: 
    system_user: admin
  vars_files:
    - files/secrets/credentials.vault
  pre_tasks:
    - name: create www-data
      user: name=www-data state=present
  roles:
    - {role: ansible-role-containerized-wordpress }
```

## install the role

``` bash
[admin@node1 webapp]$ ansible-galaxy install -r roles/requirements.yml
``` 

## output

```javascript
- extracting ansible-role-containerized-wordpress to /home/admin/.ansible/roles/ansible-role-containerized-wordpress
- ansible-role-containerized-wordpress was installed successfully
```

## run wordpress playbook

``` bash
[admin@node1 webapp]$ ansible-playbook -i hosts.yml --ask-vault-pass wordpress.ym 
``` 

``` bash
BECOME password:
Vault password:

PLAY [prod] ********************************************************************

TASK [Gathering Facts] *********************************************************
ok: [client]

TASK [create www-data] *********************************************************
changed: [client]

TASK [ansible-role-containerized-wordpress : Setup compose dir structure] ******
changed: [client] => (item=wordpress)
changed: [client] => (item=wp-db-data)
changed: [client] => (item=logs/nginx)

TASK [ansible-role-containerized-wordpress : Create docker-compose.yml file] ***
changed: [client]

TASK [ansible-role-containerized-wordpress : Deploy uploads.ini to WordPress "/home/admin/compose-wordpress" dir] ***
changed: [client]

TASK [ansible-role-containerized-wordpress : Deploy Docker Compose project for Wordpress/MySQL/Nginx (Let's Encrypt) containers] ***
changed: [client]

TASK [ansible-role-containerized-wordpress : Run docker-compose up] ************
changed: [client]

TASK [ansible-role-containerized-wordpress : Waiting for all containers to start up and foolcontrol.org to be accessible] ***
ok: [client]

TASK [ansible-role-containerized-wordpress : debug] ****************************
ok: [client] => {
    "msg": "Site is reachable"
}

TASK [ansible-role-containerized-wordpress : debug] ****************************
skipping: [client]

TASK [ansible-role-containerized-wordpress : debug] ****************************
ok: [client] => {
    "msg": [
        "With specified variables, following configuration has been made:",
        "",
        "URL used for Nginx virtual host: foolcontrol.org",
        "Specified URL is live/DNS is setup: staging",
        "WordPress Docker image version:5.2.4",
        "WORDPRESS_DB_NAME: wordpress",
        "WORDPRESS_TABLE_PREFIX: wp_",
        "WORDPRESS_DB_HOST: mysql",
        "WORDPRESS_DB_USER: admin",
        "WORDPRESS_DB_PASSWORD: change-M3",
        "MYSQL_ROOT_PASSWORD: change-M3",
        "MYSQL_DATABASE: wordpress",
        "MYSQL_USER: admin",
        "MYSQL_PASSWORD: change-M3"
    ]
}

TASK [ansible-role-containerized-wordpress : debug] ****************************
ok: [client] => {
    "msg": [
        "Setup successfully complete.",
        "",
        "Wordpress instance is available on following IP: client",
        "If DNS is pointing to this IP, it'll be available on: foolcontrol.org"
    ]
}

PLAY RECAP *********************************************************************
client                     : ok=11   changed=6    unreachable=0    failed=0    skipped=1    rescued=0    ignored=0
```    

## The target machine 

``` bash
[admin@node2 ~]$ ls compose-wordpress/
``` 
```javascript
docker-compose.yml  logs  wordpress  wp-db-data
``` 

``` bash
[admin@node2 ~]$ sudo docker ps
``` 

```javascript
[sudo] password for admin:
CONTAINER ID   IMAGE                    COMMAND                  CREATED         STATUS                   PORTS                               NAMES
715cea38dc50   wordpress:5.2.4-apache   "docker-entrypoint.s…"   9 minutes ago   Up 9 minutes             0.0.0.0:80->80/tcp, :::80->80/tcp   wp
f32f1c45dff7   mysql:5.7                "docker-entrypoint.s…"   9 minutes ago   Up 9 minutes (healthy)   3306/tcp, 33060/tcp                 db
``` 































