### 验证启动模式

```
ls /sys/firmware/efi/efivars
```

### 禁用 reflector 服务

```
systemctl stop reflector.service
```

### 查看该服务是否被禁用

```
systemctl status reflector.service
```

### 再次确认是否为 UEFI 模式

```bash
ls /sys/firmware/efi/efivars
```

## 连接网络

#### 有线连接

#### 无线连接

```
iwctl # 进入交互式命令行
device list # 列出无线网卡设备名，比如无线网卡看到叫 wlan0
station wlan0 scan # 扫描网络
station wlan0 get-networks # 列出所有 wifi 网络
station wlan0 connect wifi-name # 进行连接，注意这里无法输入中文。回车后输入密码即可
exit # 连接成功后退出
```

## 测试网络连通性

```
ping bing.com -c 2
```

## 更新系统时钟

```
timedatectl set-ntp true # 将系统时间与网络时间进行同步
timedatectl status # 检查服务状态
```

## 更换国内软件仓库镜像源加快下载速度

```
nano /etc/pacman.d/mirrorlist
```

```
##
## Arch Linux repository mirrorlist
## Generated on 2022-11-09
##

Server = https://mirrors.tuna.tsinghua.edu.cn/archlinux/$repo/os/$arch
Server = https://mirrors.ustc.edu.cn/archlinux/$repo/os/$arch
Server = https://mirrors.bfsu.edu.cn/archlinux/$repo/os/$arch
Server = https://mirrors.nju.edu.cn/archlinux/$repo/os/$arch
Server = https://mirrors.sjtug.sjtu.edu.cn/archlinux/$repo/os/$arch

```

## 分区和格式化

#### 查看当前分区状况

```
lsblk # 显示当前分区情况
```

```
cfdisk /dev/nvmexn1
```
