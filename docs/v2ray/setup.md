# V2Ray 服务器搭建

## 系统配置

> 以 `Debian 11` 为例。

### 更新软件包

```shell
apt update && apt upgrade -y
```

### 设置时区为 `UTC+8`

```shell
rm -rf /etc/localtime
ln -s /usr/share/zoneinfo/Asia/Shanghai /etc/localtime
```

### 重启

```shell
reboot
```

### 清理软件包和缓存

```shell
uname -r
dpkg -l | grep linux-image
apt purge linux-image-[name]
apt clean
uname -r
```

## 软件配置

### 安装和更新 `V2Ray`

```shell
bash <(curl -L https://raw.githubusercontent.com/v2fly/fhs-install-v2ray/master/install-release.sh)
```

### 安装和更新 `geoip.dat` 和 `geosite.dat`

```shell
bash <(curl -L https://raw.githubusercontent.com/v2fly/fhs-install-v2ray/master/install-dat-release.sh)
```

### 移除 `V2Ray`

```shell
bash <(curl -L https://raw.githubusercontent.com/v2fly/fhs-install-v2ray/master/install-release.sh) --remove
```

### 配置 `V2Ray`

```shell
nano /usr/local/etc/v2ray/config.json
```

### 启动 `V2Ray`

```shell
systemctl enable v2ray
systemctl start v2ray
v2ray -version
```

### 重新启动 `V2Ray`

```shell
systemctl restart v2ray
systemctl status v2ray
```

### 流量统计

```shell
chmod 755 /usr/local/etc/v2ray/traffic.sh
```

---

_文档更新日期：`2021-11-26`_
