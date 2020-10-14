---
layout: category
categories:
  - Linux
tags:
  - bash
last_modified_at: 2020-09-28T12:25:10-05:00
---

定时任务学习笔记。

---

##### 设置定时器

1、 查询定时任务状态

```bash
  service crond status
```

2、启动定时任务

```bash
 service crond start
 ```

3、重新启动

```bash
service crond reload
```

4、停止定时任务

```bash
service crond stop
```

5、配置开机自启动

```bash
chkconfig –level 35 crond on
```
---

##### 配置定时任务
1、语法: crontab [-u <用户名称>][配置文件] 或 contab [-u <用户名称>][-elr]
2、配置文件格式
-  '* * * * * command' 
-  分　时　日　月　周　 命令
-  第1列表示分钟1～59 每分钟用*或者 */1表示
- 第2列表示小时1～23（0表示0点）
- 第3列表示日期1～31
- 第4列 表示月份1～12
- 第5列标识号星期0～6（0表示星期天）
- 第6列要运行的命令
- #Use the hash sign to prefix a comment
- #+—————- minute (0 – 59)
- #| +————- hour (0 – 23)
- #| | +———- day of month (1 – 31)
- #| | | +——- month (1 – 12)
- #| | | | +—- day of week (0 – 7) (Sunday=0 or 7)
- #| | | | |
- #* * * * * command to be executed

3、配置的目标位置在:  vi /etc/crontab 

---

##### 使用参数

```bash
05 10 * * * bash /data/ui-shell/run.sh > /data/ui-shell/log/run-`date +"\%Y\%m\%d"`.log 2>&1
```