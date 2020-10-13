
1. 给 ubuntu 环境添加 chrome 源

```bash
sudo wget  http://www.linuxidc.com/files/repo/google-chrome.list -P /etc/apt/sources.list.d/
```

2. 添加密钥

```bash
sudo wget -q -O - https://dl.google.com/linux/linux_signing_key.pub  | sudo apt-key add -
```

3. 更新系统资源

```bash
sudo apt update
```

