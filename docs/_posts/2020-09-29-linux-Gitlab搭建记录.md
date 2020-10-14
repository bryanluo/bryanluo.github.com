---
layout: category
categories:
  - Linux
tags:
  - bash
last_modified_at: 2020-09-29T12:25:10-05:00
---

linux 搭建 gitlab 过程记录.

---

## 先安装 ssh ， 系统一般安装好的，也不排除最小系统安装没有ssh环境

 -

1、安装依赖组件

```bash
sudo yum install -y curl policycoreutils-python openssh-server
```

2、设置开机自启动

```bash

sudo systemctl enable sshd

```


3、启动 sshd

```bash
sudo systemctl start sshd
```

---
## 关闭防火墙，或者开放 HTTP 的端口

刷新防火墙规则

```bash
iptables -F

```

---
## 安装邮件服务

```bash
sudo yum install postfix
sudo systemctl enable postfix
sudo systemctl start postfix
```

出现问题解决：

```yaml
fatal: parameter inet_interfaces: no local interface found for ::1
```

解决办法:

> vi /etc/postfix/main.cf

```yaml
# 可以看到这里的配置文件配置的是localhost，问题就出现在这里
inet_interfaces = localhost
inet_protocols = all

# 我们把他改成
inet_interfaces = all
inet_protocols = all
```

---
### 从官网获取 gitlab 的安装脚本, 主要是添加 gitlab 的 yum 源

输出到文件里是为了看下下载的脚本内容

```bash
curl https://packages.gitlab.com/install/repositories/gitlab/gitlab-ee/script.rpm.sh > rpm.sh

chmod +x rpm.sh

./rpm.sh
```

2、 安装 Gitlab

> yum install -y gitlab-ee

查看 gitlab-ee 安装内容

> rpm -ql gitlab-ee | less

配置 gitlab 的监听地址与端口， 主要路径：/etc/gitlab/gitlab.rb

```yaml
external_url 'http://gitlab.ai-he.me'

nginx['listen_addresses'] = ['0.0.0.0', '[::]']

nginx['listen_port'] = 78780

```

详细配置： [gitlab 详细配置](https://docs.gitlab.com/omnibus/settings/configuration.html#configuring-the-external-url-for-gitlab)

---
#### 更新配置

> sudo gitlab-ctl reconfigure

重启 tiglab

> gitlab-ctl restart

查看命令帮助信息

> gitlab-ctl --help

创建用户账号:

http://120.25.157.8:5050/admin

root/gziiim2020