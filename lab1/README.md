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
[admin@node1 ~]$ ansible -i hosts all -m copy -a "dest=/home/admin/toto.txt content='bonjour eazytraining'" 
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

## update hosts with the following line in hosts: 

``` bash
10.0.2.5 ansible_user=admin ansible_password=admin ansible_ssh_common_args='-o SS trictHostKeyChecking=no' 
```

## re-execute again the command with copy module:  

``` bash
[admin@node1 ~]$ ansible -i hosts all -m copy -a "dest=/home/admin/toto.txt content='bonjour eazytraining'" 
```

## output 3: 

```javascript
10.0.2.4 | SUCCESS => {
    "ansible_facts": {
        "discovered_interpreter_python": "/usr/bin/python"
    }, 
    "changed": false, 
    "checksum": "ba90e31f2c066fc3a9911d9ae26b89bfaf724198", 
    "dest": "/home/admin/toto.txt", 
    "gid": 1000, 
    "group": "admin", 
    "mode": "0664", 
    "owner": "admin", 
    "path": "/home/admin/toto.txt", 
    "size": 20, 
    "state": "file", 
    "uid": 1000
}

10.0.2.5 | CHANGED => {
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
    "src": "/home/admin/.ansible/tmp/ansible-tmp-1634381849.97-295-91945755090938/source", 
    "state": "file", 
    "uid": 1000
}
```
## get the setup with the following command:

``` bash
ansible -i hosts all -m setup 
```

## setup results: 



```javascript
10.0.2.4 | SUCCESS => {
    "ansible_facts": {
        "ansible_apparmor": {
            "status": "disabled"
        }, 
        "ansible_architecture": "x86_64", 
        "ansible_bios_date": "08/24/2006", 
        "ansible_bios_version": "4.2.amazon", 
        "ansible_cmdline": {
            "BOOT_IMAGE": "/boot/vmlinuz-3.10.0-862.14.4.el7.x86_64", 
            "LANG": "en_US.UTF-8", 
            "console": "ttyS0,115200", 
            "crashkernel": "auto", 
            "ro": true, 
            "root": "UUID=eaadd3f0-e151-4950-a4ba-49ae6f413224"
        }, 
        "ansible_date_time": {
            "date": "2021-10-16", 
            "day": "16", 
            "epoch": "1634382866", 
            "hour": "11", 
            "iso8601": "2021-10-16T11:14:26Z", 
            "iso8601_basic": "20211016T111426822729", 
            "iso8601_basic_short": "20211016T111426", 
            "iso8601_micro": "2021-10-16T11:14:26.822729Z", 
            "minute": "14", 
            "month": "10", 
            "second": "26", 
            "time": "11:14:26", 
            "tz": "UTC", 
            "tz_offset": "+0000", 
            "weekday": "Saturday", 
            "weekday_number": "6", 
            "weeknumber": "41", 
            "year": "2021"
        }, 
        "ansible_device_links": {
            "ids": {}, 
            "labels": {}, 
            "masters": {}, 
            "uuids": {}
        }, 
        "ansible_devices": {
            "xvda": {
                "holders": [], 
                "host": "", 
                "links": {
                    "ids": [], 
                    "labels": [], 
                    "masters": [], 
                    "uuids": []
                }, 
                "model": null, 
                "partitions": {
                    "xvda1": {
                        "holders": [], 
                        "links": {
                            "ids": [], 
                            "labels": [], 
                            "masters": [], 
                            "uuids": []
                        }, 
                        "sectors": "209713119", 
                        "sectorsize": 512, 
                        "size": "100.00 GB", 
                        "start": "2048", 
                        "uuid": null
                    }
                }, 
                "removable": "0", 
                "rotational": "0", 
                "sas_address": null, 
                "sas_device_handle": null, 
                "scheduler_mode": "deadline", 
                "sectors": "209715200", 
                "sectorsize": "512", 
                "size": "100.00 GB", 
                "support_discard": "0", 
                "vendor": null, 
                "virtual": 1
            }
        }, 
        "ansible_distribution": "CentOS", 
        "ansible_distribution_file_parsed": true, 
        "ansible_distribution_file_path": "/etc/redhat-release", 
        "ansible_distribution_file_variety": "RedHat", 
        "ansible_distribution_major_version": "7", 
        "ansible_distribution_release": "Core", 
        "ansible_distribution_version": "7.9", 
        "ansible_dns": {
            "nameservers": [
                "127.0.0.11"
            ], 
            "options": {
                "ndots": "0"
            }, 
            "search": [
                "eu-west-3.compute.internal"
            ]
        }, 
        "ansible_domain": "", 
        "ansible_effective_group_id": 1000, 
        "ansible_effective_user_id": 1000, 
        "ansible_env": {
            "HOME": "/home/admin", 
            "LANG": "C", 
            "LC_ALL": "C", 
            "LC_NUMERIC": "C", 
            "LESSOPEN": "||/usr/bin/lesspipe.sh %s", 
            "LOGNAME": "admin", 
            "LS_COLORS": "rs=0:di=01;34:ln=01;36:mh=00:pi=40;33:so=01;35:do=01;35:bd=40;33;01:cd=40;33;01:or=40;31;01:mi=01;05;37;41:su=37;41:sg=30;43:ca=30;41:tw=30;42:ow=34;42:st=37;44:ex=01;32:*.tar=01;31:*.tgz=01;31:*.arc=01;31:*.arj=01;31:*.taz=01;31:*.lha=01;31:*.lz4=01;31:*.lzh=01;31:*.lzma=01;31:*.tlz=01;31:*.txz=01;31:*.tzo=01;31:*.t7z=01;31:*.zip=01;31:*.z=01;31:*.Z=01;31:*.dz=01;31:*.gz=01;31:*.lrz=01;31:*.lz=01;31:*.lzo=01;31:*.xz=01;31:*.bz2=01;31:*.bz=01;31:*.tbz=01;31:*.tbz2=01;31:*.tz=01;31:*.deb=01;31:*.rpm=01;31:*.jar=01;31:*.war=01;31:*.ear=01;31:*.sar=01;31:*.rar=01;31:*.alz=01;31:*.ace=01;31:*.zoo=01;31:*.cpio=01;31:*.7z=01;31:*.rz=01;31:*.cab=01;31:*.jpg=01;35:*.jpeg=01;35:*.gif=01;35:*.bmp=01;35:*.pbm=01;35:*.pgm=01;35:*.ppm=01;35:*.tga=01;35:*.xbm=01;35:*.xpm=01;35:*.tif=01;35:*.tiff=01;35:*.png=01;35:*.svg=01;35:*.svgz=01;35:*.mng=01;35:*.pcx=01;35:*.mov=01;35:*.mpg=01;35:*.mpeg=01;35:*.m2v=01;35:*.mkv=01;35:*.webm=01;35:*.ogm=01;35:*.mp4=01;35:*.m4v=01;35:*.mp4v=01;35:*.vob=01;35:*.qt=01;35:*.nuv=01;35:*.wmv=01;35:*.asf=01;35:*.rm=01;35:*.rmvb=01;35:*.flc=01;35:*.avi=01;35:*.fli=01;35:*.flv=01;35:*.gl=01;35:*.dl=01;35:*.xcf=01;35:*.xwd=01;35:*.yuv=01;35:*.cgm=01;35:*.emf=01;35:*.axv=01;35:*.anx=01;35:*.ogv=01;35:*.ogx=01;35:*.aac=01;36:*.au=01;36:*.flac=01;36:*.mid=01;36:*.midi=01;36:*.mka=01;36:*.mp3=01;36:*.mpc=01;36:*.ogg=01;36:*.ra=01;36:*.wav=01;36:*.axa=01;36:*.oga=01;36:*.spx=01;36:*.xspf=01;36:", 
            "MAIL": "/var/mail/admin", 
            "PATH": "/usr/local/bin:/usr/bin", 
            "PWD": "/home/admin", 
            "SHELL": "/bin/bash", 
            "SHLVL": "2", 
            "SSH_CLIENT": "10.0.0.3 42444 22", 
            "SSH_CONNECTION": "10.0.0.3 42444 10.0.0.5 22", 
            "SSH_TTY": "/dev/pts/0", 
            "TERM": "xterm", 
            "USER": "admin", 
            "_": "/usr/bin/python"
        }, 
        "ansible_fibre_channel_wwn": [], 
        "ansible_fips": false, 
        "ansible_form_factor": "Other", 
        "ansible_fqdn": "node3", 
        "ansible_hostname": "node3", 
        "ansible_hostnqn": "", 
        "ansible_is_chroot": true, 
        "ansible_iscsi_iqn": "", 
        "ansible_kernel": "3.10.0-862.14.4.el7.x86_64", 
        "ansible_kernel_version": "#1 SMP Wed Sep 26 15:12:11 UTC 2018", 
        "ansible_local": {}, 
        "ansible_lsb": {}, 
        "ansible_machine": "x86_64", 
        "ansible_memfree_mb": 23130, 
        "ansible_memory_mb": {
            "nocache": {
                "free": 26077, 
                "used": 5934
            }, 
            "real": {
                "free": 23130, 
                "total": 32011, 
                "used": 8881
            }, 
            "swap": {
                "cached": 0, 
                "free": 0, 
                "total": 0, 
                "used": 0
            }
        }, 
        "ansible_memtotal_mb": 32011, 
        "ansible_mounts": [
            {
                "block_available": 9690888, 
                "block_size": 4096, 
                "block_total": 26211579, 
                "block_used": 16520691, 
                "device": "/dev/xvda1", 
                "fstype": "xfs", 
                "inode_available": 50592625, 
                "inode_total": 52428224, 
                "inode_used": 1835599, 
                "mount": "/etc/hosts", 
                "options": "rw,seclabel,relatime,attr2,inode64,noquota,bind", 
                "size_available": 39693877248, 
                "size_total": 107362627584, 
                "uuid": "N/A"
            }, 
            {
                "block_available": 9690888, 
                "block_size": 4096, 
                "block_total": 26211579, 
                "block_used": 16520691, 
                "device": "/dev/xvda1", 
                "fstype": "xfs", 
                "inode_available": 50592625, 
                "inode_total": 52428224, 
                "inode_used": 1835599, 
                "mount": "/etc/hostname", 
                "options": "rw,seclabel,relatime,attr2,inode64,noquota,bind", 
                "size_available": 39693877248, 
                "size_total": 107362627584, 
                "uuid": "N/A"
            }, 
            {
                "block_available": 9690888, 
                "block_size": 4096, 
                "block_total": 26211579, 
                "block_used": 16520691, 
                "device": "/dev/xvda1", 
                "fstype": "xfs", 
                "inode_available": 50592625, 
                "inode_total": 52428224, 
                "inode_used": 1835599, 
                "mount": "/etc/resolv.conf", 
                "options": "rw,seclabel,relatime,attr2,inode64,noquota,bind", 
                "size_available": 39693877248, 
                "size_total": 107362627584, 
                "uuid": "N/A"
            }
        ], 
        "ansible_nodename": "node3", 
        "ansible_os_family": "RedHat", 
        "ansible_pkg_mgr": "yum", 
        "ansible_proc_cmdline": {
            "BOOT_IMAGE": "/boot/vmlinuz-3.10.0-862.14.4.el7.x86_64", 
            "LANG": "en_US.UTF-8", 
            "console": [
                "tty0", 
                "ttyS0,115200n8", 
                "ttyS0,115200"
            ], 
            "crashkernel": "auto", 
            "ro": true, 
            "root": "UUID=eaadd3f0-e151-4950-a4ba-49ae6f413224"
        }, 
        "ansible_processor": [
            "0", 
            "GenuineIntel", 
            "Intel(R) Xeon(R) CPU E5-2676 v3 @ 2.40GHz", 
            "1", 
            "GenuineIntel", 
            "Intel(R) Xeon(R) CPU E5-2676 v3 @ 2.40GHz", 
            "2", 
            "GenuineIntel", 
            "Intel(R) Xeon(R) CPU E5-2676 v3 @ 2.40GHz", 
            "3", 
            "GenuineIntel", 
            "Intel(R) Xeon(R) CPU E5-2676 v3 @ 2.40GHz", 
            "4", 
            "GenuineIntel", 
            "Intel(R) Xeon(R) CPU E5-2676 v3 @ 2.40GHz", 
            "5", 
            "GenuineIntel", 
            "Intel(R) Xeon(R) CPU E5-2676 v3 @ 2.40GHz", 
            "6", 
            "GenuineIntel", 
            "Intel(R) Xeon(R) CPU E5-2676 v3 @ 2.40GHz", 
            "7", 
            "GenuineIntel", 
            "Intel(R) Xeon(R) CPU E5-2676 v3 @ 2.40GHz"
        ], 
        "ansible_processor_cores": 8, 
        "ansible_processor_count": 1, 
        "ansible_processor_threads_per_core": 1, 
        "ansible_processor_vcpus": 8, 
        "ansible_product_name": "HVM domU", 
        "ansible_product_serial": "NA", 
        "ansible_product_uuid": "NA", 
        "ansible_product_version": "4.2.amazon", 
        "ansible_python": {
            "executable": "/usr/bin/python", 
            "has_sslcontext": true, 
            "type": "CPython", 
            "version": {
                "major": 2, 
                "micro": 5, 
                "minor": 7, 
                "releaselevel": "final", 
                "serial": 0
            }, 
            "version_info": [
                2, 
                7, 
                5, 
                "final", 
                0
            ]
        }, 
        "ansible_python_version": "2.7.5", 
        "ansible_real_group_id": 1000, 
        "ansible_real_user_id": 1000, 
        "ansible_selinux": {
            "status": "disabled"
        }, 
        "ansible_selinux_python_present": true, 
        "ansible_service_mgr": "sysvinit", 
        "ansible_ssh_host_key_rsa_public": "AAAAB3NzaC1yc2EAAAADAQABAAABAQCbqxiatMpv6A0oHR6kASaNx2lEPBh65VCjvNykCqsBjxk1qub0bGL4+kN+SKLkXEGNwnMGwvRRhVDAxHsNt60hCBj25i2NXIC6FSsDAW4NB8bynIwgASSq+1B8dmhttZTQnu9TjEEXZRlurtLEqxxvL+1IAdOpofYxkzg23kiC0UmQn07c/3iT9uXi6w304xc9Gzy8Hg9eoKIYH+og57lv/b+LydAf0gNRDdyr2mFVSN5Iu2j6knDJcDHBY+dX76GNdeKzHd7aqGNzAqlCfYarHL1tJMhu1dhRRwQXh5PFvCfeHs+YCDKz4VT5asM4/Zrt5N3BE+qsBMoy8s+2RoAL", 
        "ansible_swapfree_mb": 0, 
        "ansible_swaptotal_mb": 0, 
        "ansible_system": "Linux", 
        "ansible_system_capabilities": [
            "cap_chown", 
            "cap_dac_override", 
            "cap_dac_read_search", 
            "cap_fowner", 
            "cap_fsetid", 
            "cap_kill", 
            "cap_setgid", 
            "cap_setuid", 
            "cap_setpcap", 
            "cap_linux_immutable", 
            "cap_net_bind_service", 
            "cap_net_broadcast", 
            "cap_net_admin", 
            "cap_net_raw", 
            "cap_ipc_lock", 
            "cap_ipc_owner", 
            "cap_sys_module", 
            "cap_sys_rawio", 
            "cap_sys_chroot", 
            "cap_sys_ptrace", 
            "cap_sys_pacct", 
            "cap_sys_admin", 
            "cap_sys_boot", 
            "cap_sys_nice", 
            "cap_sys_resource", 
            "cap_sys_time", 
            "cap_sys_tty_config", 
            "cap_mknod", 
            "cap_lease", 
            "cap_audit_write", 
            "cap_audit_control", 
            "cap_setfcap", 
            "cap_mac_override", 
            "cap_mac_admin", 
            "cap_syslog", 
            "35", 
            "36+i"
        ], 
        "ansible_system_capabilities_enforced": "True", 
        "ansible_system_vendor": "Xen", 
        "ansible_uptime_seconds": 242981, 
        "ansible_user_dir": "/home/admin", 
        "ansible_user_gecos": "", 
        "ansible_user_gid": 1000, 
        "ansible_user_id": "admin", 
        "ansible_user_shell": "/bin/bash", 
        "ansible_user_uid": 1000, 
        "ansible_userspace_architecture": "x86_64", 
        "ansible_userspace_bits": "64", 
        "ansible_virtualization_role": "guest", 
        "ansible_virtualization_type": "docker", 
        "discovered_interpreter_python": "/usr/bin/python", 
        "gather_subset": [
            "all"
        ], 
        "module_setup": true
    }, 
    "changed": false
}
10.0.2.5 | SUCCESS => {
    "ansible_facts": {
        "ansible_apparmor": {
            "status": "disabled"
        }, 
        "ansible_architecture": "x86_64", 
        "ansible_bios_date": "08/24/2006", 
        "ansible_bios_version": "4.2.amazon", 
        "ansible_cmdline": {
            "BOOT_IMAGE": "/boot/vmlinuz-3.10.0-862.14.4.el7.x86_64", 
            "LANG": "en_US.UTF-8", 
            "console": "ttyS0,115200", 
            "crashkernel": "auto", 
            "ro": true, 
            "root": "UUID=eaadd3f0-e151-4950-a4ba-49ae6f413224"
        }, 
        "ansible_date_time": {
            "date": "2021-10-16", 
            "day": "16", 
            "epoch": "1634382866", 
            "hour": "11", 
            "iso8601": "2021-10-16T11:14:26Z", 
            "iso8601_basic": "20211016T111426822041", 
            "iso8601_basic_short": "20211016T111426", 
            "iso8601_micro": "2021-10-16T11:14:26.822041Z", 
            "minute": "14", 
            "month": "10", 
            "second": "26", 
            "time": "11:14:26", 
            "tz": "UTC", 
            "tz_offset": "+0000", 
            "weekday": "Saturday", 
            "weekday_number": "6", 
            "weeknumber": "41", 
            "year": "2021"
        }, 
        "ansible_device_links": {
            "ids": {}, 
            "labels": {}, 
            "masters": {}, 
            "uuids": {}
        }, 
        "ansible_devices": {
            "xvda": {
                "holders": [], 
                "host": "", 
                "links": {
                    "ids": [], 
                    "labels": [], 
                    "masters": [], 
                    "uuids": []
                }, 
                "model": null, 
                "partitions": {
                    "xvda1": {
                        "holders": [], 
                        "links": {
                            "ids": [], 
                            "labels": [], 
                            "masters": [], 
                            "uuids": []
                        }, 
                        "sectors": "209713119", 
                        "sectorsize": 512, 
                        "size": "100.00 GB", 
                        "start": "2048", 
                        "uuid": null
                    }
                }, 
                "removable": "0", 
                "rotational": "0", 
                "sas_address": null, 
                "sas_device_handle": null, 
                "scheduler_mode": "deadline", 
                "sectors": "209715200", 
                "sectorsize": "512", 
                "size": "100.00 GB", 
                "support_discard": "0", 
                "vendor": null, 
                "virtual": 1
            }
        }, 
        "ansible_distribution": "CentOS", 
        "ansible_distribution_file_parsed": true, 
        "ansible_distribution_file_path": "/etc/redhat-release", 
        "ansible_distribution_file_variety": "RedHat", 
        "ansible_distribution_major_version": "7", 
        "ansible_distribution_release": "Core", 
        "ansible_distribution_version": "7.9", 
        "ansible_dns": {
            "nameservers": [
                "127.0.0.11"
            ], 
            "options": {
                "ndots": "0"
            }, 
            "search": [
                "eu-west-3.compute.internal"
            ]
        }, 
        "ansible_domain": "", 
        "ansible_effective_group_id": 1000, 
        "ansible_effective_user_id": 1000, 
        "ansible_env": {
            "HOME": "/home/admin", 
            "LANG": "C", 
            "LC_ALL": "C", 
            "LC_NUMERIC": "C", 
            "LESSOPEN": "||/usr/bin/lesspipe.sh %s", 
            "LOGNAME": "admin", 
            "LS_COLORS": "rs=0:di=01;34:ln=01;36:mh=00:pi=40;33:so=01;35:do=01;35:bd=40;33;01:cd=40;33;01:or=40;31;01:mi=01;05;37;41:su=37;41:sg=30;43:ca=30;41:tw=30;42:ow=34;42:st=37;44:ex=01;32:*.tar=01;31:*.tgz=01;31:*.arc=01;31:*.arj=01;31:*.taz=01;31:*.lha=01;31:*.lz4=01;31:*.lzh=01;31:*.lzma=01;31:*.tlz=01;31:*.txz=01;31:*.tzo=01;31:*.t7z=01;31:*.zip=01;31:*.z=01;31:*.Z=01;31:*.dz=01;31:*.gz=01;31:*.lrz=01;31:*.lz=01;31:*.lzo=01;31:*.xz=01;31:*.bz2=01;31:*.bz=01;31:*.tbz=01;31:*.tbz2=01;31:*.tz=01;31:*.deb=01;31:*.rpm=01;31:*.jar=01;31:*.war=01;31:*.ear=01;31:*.sar=01;31:*.rar=01;31:*.alz=01;31:*.ace=01;31:*.zoo=01;31:*.cpio=01;31:*.7z=01;31:*.rz=01;31:*.cab=01;31:*.jpg=01;35:*.jpeg=01;35:*.gif=01;35:*.bmp=01;35:*.pbm=01;35:*.pgm=01;35:*.ppm=01;35:*.tga=01;35:*.xbm=01;35:*.xpm=01;35:*.tif=01;35:*.tiff=01;35:*.png=01;35:*.svg=01;35:*.svgz=01;35:*.mng=01;35:*.pcx=01;35:*.mov=01;35:*.mpg=01;35:*.mpeg=01;35:*.m2v=01;35:*.mkv=01;35:*.webm=01;35:*.ogm=01;35:*.mp4=01;35:*.m4v=01;35:*.mp4v=01;35:*.vob=01;35:*.qt=01;35:*.nuv=01;35:*.wmv=01;35:*.asf=01;35:*.rm=01;35:*.rmvb=01;35:*.flc=01;35:*.avi=01;35:*.fli=01;35:*.flv=01;35:*.gl=01;35:*.dl=01;35:*.xcf=01;35:*.xwd=01;35:*.yuv=01;35:*.cgm=01;35:*.emf=01;35:*.axv=01;35:*.anx=01;35:*.ogv=01;35:*.ogx=01;35:*.aac=01;36:*.au=01;36:*.flac=01;36:*.mid=01;36:*.midi=01;36:*.mka=01;36:*.mp3=01;36:*.mpc=01;36:*.ogg=01;36:*.ra=01;36:*.wav=01;36:*.axa=01;36:*.oga=01;36:*.spx=01;36:*.xspf=01;36:", 
            "MAIL": "/var/mail/admin", 
            "PATH": "/usr/local/bin:/usr/bin", 
            "PWD": "/home/admin", 
            "SHELL": "/bin/bash", 
            "SHLVL": "2", 
            "SSH_CLIENT": "10.0.0.3 41016 22", 
            "SSH_CONNECTION": "10.0.0.3 41016 10.0.0.4 22", 
            "SSH_TTY": "/dev/pts/0", 
            "TERM": "xterm", 
            "USER": "admin", 
            "_": "/usr/bin/python"
        }, 
        "ansible_fibre_channel_wwn": [], 
        "ansible_fips": false, 
        "ansible_form_factor": "Other", 
        "ansible_fqdn": "node2", 
        "ansible_hostname": "node2", 
        "ansible_hostnqn": "", 
        "ansible_is_chroot": true, 
        "ansible_iscsi_iqn": "", 
        "ansible_kernel": "3.10.0-862.14.4.el7.x86_64", 
        "ansible_kernel_version": "#1 SMP Wed Sep 26 15:12:11 UTC 2018", 
        "ansible_local": {}, 
        "ansible_lsb": {}, 
        "ansible_machine": "x86_64", 
        "ansible_memfree_mb": 23130, 
        "ansible_memory_mb": {
            "nocache": {
                "free": 26077, 
                "used": 5934
            }, 
            "real": {
                "free": 23130, 
                "total": 32011, 
                "used": 8881
            }, 
            "swap": {
                "cached": 0, 
                "free": 0, 
                "total": 0, 
                "used": 0
            }
        }, 
        "ansible_memtotal_mb": 32011, 
        "ansible_mounts": [
            {
                "block_available": 9690888, 
                "block_size": 4096, 
                "block_total": 26211579, 
                "block_used": 16520691, 
                "device": "/dev/xvda1", 
                "fstype": "xfs", 
                "inode_available": 50592625, 
                "inode_total": 52428224, 
                "inode_used": 1835599, 
                "mount": "/etc/hosts", 
                "options": "rw,seclabel,relatime,attr2,inode64,noquota,bind", 
                "size_available": 39693877248, 
                "size_total": 107362627584, 
                "uuid": "N/A"
            }, 
            {
                "block_available": 9690888, 
                "block_size": 4096, 
                "block_total": 26211579, 
                "block_used": 16520691, 
                "device": "/dev/xvda1", 
                "fstype": "xfs", 
                "inode_available": 50592625, 
                "inode_total": 52428224, 
                "inode_used": 1835599, 
                "mount": "/etc/hostname", 
                "options": "rw,seclabel,relatime,attr2,inode64,noquota,bind", 
                "size_available": 39693877248, 
                "size_total": 107362627584, 
                "uuid": "N/A"
            }, 
            {
                "block_available": 9690888, 
                "block_size": 4096, 
                "block_total": 26211579, 
                "block_used": 16520691, 
                "device": "/dev/xvda1", 
                "fstype": "xfs", 
                "inode_available": 50592625, 
                "inode_total": 52428224, 
                "inode_used": 1835599, 
                "mount": "/etc/resolv.conf", 
                "options": "rw,seclabel,relatime,attr2,inode64,noquota,bind", 
                "size_available": 39693877248, 
                "size_total": 107362627584, 
                "uuid": "N/A"
            }
        ], 
        "ansible_nodename": "node2", 
        "ansible_os_family": "RedHat", 
        "ansible_pkg_mgr": "yum", 
        "ansible_proc_cmdline": {
            "BOOT_IMAGE": "/boot/vmlinuz-3.10.0-862.14.4.el7.x86_64", 
            "LANG": "en_US.UTF-8", 
            "console": [
                "tty0", 
                "ttyS0,115200n8", 
                "ttyS0,115200"
            ], 
            "crashkernel": "auto", 
            "ro": true, 
            "root": "UUID=eaadd3f0-e151-4950-a4ba-49ae6f413224"
        }, 
        "ansible_processor": [
            "0", 
            "GenuineIntel", 
            "Intel(R) Xeon(R) CPU E5-2676 v3 @ 2.40GHz", 
            "1", 
            "GenuineIntel", 
            "Intel(R) Xeon(R) CPU E5-2676 v3 @ 2.40GHz", 
            "2", 
            "GenuineIntel", 
            "Intel(R) Xeon(R) CPU E5-2676 v3 @ 2.40GHz", 
            "3", 
            "GenuineIntel", 
            "Intel(R) Xeon(R) CPU E5-2676 v3 @ 2.40GHz", 
            "4", 
            "GenuineIntel", 
            "Intel(R) Xeon(R) CPU E5-2676 v3 @ 2.40GHz", 
            "5", 
            "GenuineIntel", 
            "Intel(R) Xeon(R) CPU E5-2676 v3 @ 2.40GHz", 
            "6", 
            "GenuineIntel", 
            "Intel(R) Xeon(R) CPU E5-2676 v3 @ 2.40GHz", 
            "7", 
            "GenuineIntel", 
            "Intel(R) Xeon(R) CPU E5-2676 v3 @ 2.40GHz"
        ], 
        "ansible_processor_cores": 8, 
        "ansible_processor_count": 1, 
        "ansible_processor_threads_per_core": 1, 
        "ansible_processor_vcpus": 8, 
        "ansible_product_name": "HVM domU", 
        "ansible_product_serial": "NA", 
        "ansible_product_uuid": "NA", 
        "ansible_product_version": "4.2.amazon", 
        "ansible_python": {
            "executable": "/usr/bin/python", 
            "has_sslcontext": true, 
            "type": "CPython", 
            "version": {
                "major": 2, 
                "micro": 5, 
                "minor": 7, 
                "releaselevel": "final", 
                "serial": 0
            }, 
            "version_info": [
                2, 
                7, 
                5, 
                "final", 
                0
            ]
        }, 
        "ansible_python_version": "2.7.5", 
        "ansible_real_group_id": 1000, 
        "ansible_real_user_id": 1000, 
        "ansible_selinux": {
            "status": "disabled"
        }, 
        "ansible_selinux_python_present": true, 
        "ansible_service_mgr": "sysvinit", 
        "ansible_ssh_host_key_rsa_public": "AAAAB3NzaC1yc2EAAAADAQABAAABAQCbqxiatMpv6A0oHR6kASaNx2lEPBh65VCjvNykCqsBjxk1qub0bGL4+kN+SKLkXEGNwnMGwvRRhVDAxHsNt60hCBj25i2NXIC6FSsDAW4NB8bynIwgASSq+1B8dmhttZTQnu9TjEEXZRlurtLEqxxvL+1IAdOpofYxkzg23kiC0UmQn07c/3iT9uXi6w304xc9Gzy8Hg9eoKIYH+og57lv/b+LydAf0gNRDdyr2mFVSN5Iu2j6knDJcDHBY+dX76GNdeKzHd7aqGNzAqlCfYarHL1tJMhu1dhRRwQXh5PFvCfeHs+YCDKz4VT5asM4/Zrt5N3BE+qsBMoy8s+2RoAL", 
        "ansible_swapfree_mb": 0, 
        "ansible_swaptotal_mb": 0, 
        "ansible_system": "Linux", 
        "ansible_system_capabilities": [
            "cap_chown", 
            "cap_dac_override", 
            "cap_dac_read_search", 
            "cap_fowner", 
            "cap_fsetid", 
            "cap_kill", 
            "cap_setgid", 
            "cap_setuid", 
            "cap_setpcap", 
            "cap_linux_immutable", 
            "cap_net_bind_service", 
            "cap_net_broadcast", 
            "cap_net_admin", 
            "cap_net_raw", 
            "cap_ipc_lock", 
            "cap_ipc_owner", 
            "cap_sys_module", 
            "cap_sys_rawio", 
            "cap_sys_chroot", 
            "cap_sys_ptrace", 
            "cap_sys_pacct", 
            "cap_sys_admin", 
            "cap_sys_boot", 
            "cap_sys_nice", 
            "cap_sys_resource", 
            "cap_sys_time", 
            "cap_sys_tty_config", 
            "cap_mknod", 
            "cap_lease", 
            "cap_audit_write", 
            "cap_audit_control", 
            "cap_setfcap", 
            "cap_mac_override", 
            "cap_mac_admin", 
            "cap_syslog", 
            "35", 
            "36+i"
        ], 
        "ansible_system_capabilities_enforced": "True", 
        "ansible_system_vendor": "Xen", 
        "ansible_uptime_seconds": 242981, 
        "ansible_user_dir": "/home/admin", 
        "ansible_user_gecos": "", 
        "ansible_user_gid": 1000, 
        "ansible_user_id": "admin", 
        "ansible_user_shell": "/bin/bash", 
        "ansible_user_uid": 1000, 
        "ansible_userspace_architecture": "x86_64", 
        "ansible_userspace_bits": "64", 
        "ansible_virtualization_role": "guest", 
        "ansible_virtualization_type": "docker", 
        "discovered_interpreter_python": "/usr/bin/python", 
        "gather_subset": [
            "all"
        ], 
        "module_setup": true
    }, 
    "changed": false
}
```
