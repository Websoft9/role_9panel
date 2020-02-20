Ansible Role: 9panel
=========

下载 [9panel](https://github.com/websoft9/9panel) ，然后根据变量值设置 9panel 显示内容

Requirements
------------

### Operation System
CentOS7.x, Ubuntu18.04

### Python
Python2

此 role 需要 root 用户权限,可以在playbook全局加入 `become: yes`,或者如下调用 role:

```
- hosts: all
  roles:
    - role: role_common
      become: yes
```

Role Variables
--------------
None



Dependencies
------------

None

Example Playbook
----------------

```
- hosts: db-servers
  become: yes

  roles:
    - { role: role_common }
```

License
-------

BSD

