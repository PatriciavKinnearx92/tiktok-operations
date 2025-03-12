# HostHatch 和 RackNerd VPS Windows 系统一键 DD 脚本整理

在使用 HostHatch、RackNerd 等 VPS 的过程中，很多人需要对系统进行重装或更换为 Windows，本文整理了一套便捷的 DD 脚本合集，帮助大家快速完成安装。

## 安装或重装系统的必要环境

在进行重装前，需要预先安装一些必要的组件，以下命令分别适用于不同的操作系统：

### 对于 Debian/Ubuntu 系列：
bash
apt-get install -y xz-utils openssl gawk file wget screen && screen -S os


### 对于 RedHat/CentOS 系列：
bash
yum install -y xz openssl gawk file glibc-common wget screen && screen -S os


如果运行过程中出现异常，建议刷新镜像缓存或切换更快的镜像源。

#### 镜像源更新命令：
- **RedHat/CentOS 系列**：
bash
yum makecache && yum update -y

- **Debian/Ubuntu 系列**：
bash
apt update -y && apt dist-upgrade -y


👉 [【建议收藏】2025年Racknerd最新优惠套餐整理汇总 - 每日更新可用活动优惠](https://bit.ly/Rack_Nerd)

---

## 智能一键 DD 脚本

此一键 DD 脚本兼容性好，适用于国内外多种 VPS 环境，尤其对于国内主机访问国外资源较为缓慢的情况，表现尤为优异。

### 特点：
- 支持最新的 Debian 11 等版本。
- 对 Oracle Cloud (甲骨文云) 提供专门优化的安装选项，支持 UEFI 镜像。
- 可选择 25 合 1 包含多个系统版本，也可自定义镜像路径。

使用以下命令运行智能一键 DD 脚本：
bash
wget --no-check-certificate -O AutoReinstall.sh https://d.02es.com/AutoReinstall.sh && chmod a+x AutoReinstall.sh && bash AutoReinstall.sh


运行后，进入交互式界面，根据需要选择 Y 确认自动获取 IP，或选择 N 自行设置 IP 并手动输入正确的网络参数。

---

## 25 合 1 系统默认密码列表

以下是支持的系统及其默认登录密码：

1. **CentOS 7.7** - 默认密码：`Pwd@CentOS`
2. **CentOS 7/8/6** - 默认密码：`cxthhhhh.com`
3. **Debian 11/10/9/8** - 默认密码：`Minijer.com`
4. **Ubuntu 20.04/18.04/16.04** - 默认密码：`Minijer.com`
5. **Windows Server 2019/2016/2012/2008/2003** - 默认密码：`cxthhhhh.com`
6. **Windows 10 LTSC Lite/Windows 7 Lite** - 默认密码：`nat.ee`

特殊版本：
- UEFI 支持甲骨文云镜像：选择系统 ID 23-25。

---

## 自定义 DD 镜像地址安装

如果已有自定义的 DD 镜像地址，可使用以下示例脚本将镜像部署到 VPS 上：
bash
wget --no-check-certificate -qO InstallNET.sh 'https://d.02es.com/InstallNET.sh' && bash InstallNET.sh -dd '[自定义镜像地址]'


---

## 注意事项

1. **子网掩码调整**：使用 Google Cloud 原版镜像时，重装后可能默认子网掩码为 `255.255.255.255`，需要手动改为正确的值（如 `255.255.255.0`），否则可能导致网络不可用。
2. **甲骨文云适配**：在甲骨文云上重装建议用 Ubuntu 系统作为基础镜像，部分 CentOS 原生系统可能不兼容。

通过以上脚本，您可以轻松完成 VPS 的系统重装！希望此教程对您有所帮助。