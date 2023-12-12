# Ansible Role: FailoverBo Nextcloud

This role installs, and configures Nextcloud for Ubuntu 22.04.

* php82
* mariadb 10.3
* Apache
* Nextcloud 

For more information, read the project wiki page: 

## Requirements

## Role Variables

| Variale Name | Required | Default Value |
| --- | --- | --- |
| `ubuntu_nextcloud_user` | yes | |
| `ubuntu_nextcloud_user_ssh_key_location` | yes | |
| `nextcloud_fqdn` | yes | |
| `mariadb_root_password` | yes | |
| `nextcloud_db_password` | yes | |
| `nextcloud_admin_user` | yes | |
| `nextcloud_admin_password` | yes | |
| `install_media`| no | no |


A full list of defaults and their values can be found in the `defaults/main.yml`.

## host file
```yml
[nextcloudserver]
localhost

[nextcloudserver:vars]
ansible_user=ubuntu
#ansible_become=yes
#ansible_become_method=sudo
#ansible_port= 2244
ansible_ssh_private_key_file= ./KEY-UBUNTU
```

## Example Playbook


```yml
---
- name: nextcloud
  hosts: nextcloudserver
  become: true
  #become_method: sudo

  vars:
    nextcloud_version: 26.0.3
    nextcloud_fqdn: localhost

    mariadb_root_password: XxXxX4Main

    nextcloud_db_name: nextcloud
    nextcloud_db_user: nextcloud
    nextcloud_db_password: XxXxX4user
    
    nextcloud_admin_user: admin
    nextcloud_admin_password: XxXxX4Admin

    install_media: false


  roles:
    - failoverbo.nextcloud


```

