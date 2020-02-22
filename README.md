Ansible Role: 9panel
=========

本 Role 用于下载并安装 [9panel](https://github.com/websoft9/9panel) ，然后根据变量值设置 9panel 显示内容。

本 Role 可以与 php, java, apache, nginx 等roles组合成 LAMP,LNMP,JAVA 等运行环境项目

## Requirements

运行本 Role，必须实现理解如下的必要条件：

| **Items**      | **Details** |
| ------------------| ------------------|
| Operating system | Linux or Windows, 不限发行版本 |
| Python 版本 | Python2, Python3   |
| Python 组件 |    |
| Runtime |  服务器上已经安装 Apache 或 Nginx 其中之一 |


## Related roles

本 Role 与其他 Roles 没有耦合性，语法上可以单独存在。

但是，当与 apache, nginx, php|java 等 Roles 组合时，需要在其后运行。以 LAMP 为例：

```
  roles:
    - { role: role_apache } 
    - { role: role_php-fpm } 
    - { role: role_lamp } 
    ....
    - { role: role_9panel }
```


## Variables

本 Role 主要变量以及使用方法如下：

| **Items**      | **Details** | **Format**  |
| ------------------| ------------------|-----|
| phpmyadmin_webs | [ apache, nginx ] | 字符串 |
| phpmyadmin_php_version | [ "5.4", "5.5",..., "7.2" ] | 字符串 |
| phpmyadmin_download_url | 字典，取值 ["old": url,  "new": url ]   | 字典 |
| Other roles |  与其他 Roles 没有耦合性，语法上可以单独存在 | 字符串 |

建议在 *[role_cloud/var/cloud_download_url.yml](https://github.com/websoft9dev/role_cloud/blob/master/vars/cloud_download_url.yml)* 中修改 `phpmyadmin_download_url`值

### Example

```
- name: Nextcloud
  hosts: all
  become: yes
  become_method: sudo 
  vars_files:
    - vars/main.yml 
  
  vars:
    w9panel_webs: 'apache'
    w9panel_download_url: https://github.com/Websoft9/9panel.git
    w9panel_set_infrastructure: LAMP
    w9panel_set_apps: 
        - Moodle
  roles:
    - { role: role_9panel }
```

## FAQ
