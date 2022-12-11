---
cover: >-
  https://images.unsplash.com/photo-1584433144859-1fc3ab64a957?crop=entropy&cs=tinysrgb&fm=jpg&ixid=MnwxOTcwMjR8MHwxfHNlYXJjaHw0fHxwcml2YWN5fGVufDB8fHx8MTY2ODgzMjk1NQ&ixlib=rb-4.0.3&q=80
coverY: 0
---

# 📱 安卓隐私合规检测工具(Mac 环境)

## 环境搭建

### 1. 安装 Python（MAC）

- M1 芯片自带 python3
- intel 芯片自带 python2

### 2. 安装 frida

```bash
pip3 install frida
```

### 3. 安装 frida-tools

```bash
pip3 install frida-tools
```

### 4. 开启一台安卓模拟器（自带 root）或 USB 连接一台已 root 的手机

#### **4.1 获取设备 CPU 架构**

```bash
adb shell getprop ro.product.cpu.abi
```

#### **4.2 获取安装的 frida 版本**

```bash
frida --version
```

#### **4.3** [**下载**](https://github.com/frida/frida/releases)**与 frida 版本一致的 frida-server 版本**

```
文件名模式：frida-server-[x.y.z]-android-[x86 | x86_64 | arm | arm64].xz
```

#### **4.4 解压 frida-server 压缩包**

#### **4.5 安装 frida-server 到设备**

```bash
adb push frida-server-[x.y.z]-android-[x86 | x86_64 | arm | arm64] /data/local/tmp
```

#### **4.6 启动手机中的 frida-server**

```bash
// 1. 进入手机
adb shell

// 2. 使用su权限
su

// 3. 进入到frida-server所在目录
cd /data/local/tmp

// 4. 给frida-server授权
chmod 777 frida-server-[x.y.z]-android-[x86 | x86_64 | arm | arm64]

// 5、启动frida-server
./frida-server-[x.y.z]-android-[x86 | x86_64 | arm | arm64]
```

#### **4.7 新开终端窗口**

#### **4.8 查看设备上的 frida-server 是否启动成功**

```bash
frida-ps -U
```

## 安装 camille

```bash
// 1. 进到工程的安卓目录
cd android/privacy
// 2. 下载camille库
git clone https://github.com/zhengjim/camille.git
// 3. 进入camille
cd camille
// 4. 安装插件
pip3 install -r requirements.txt
// 5. 运行camille
python3 camille.py -h
```

## 开启监控

```bash
1. 重新启动的模拟器需要重新安装 frida-server 到模拟器，执行[4.4-4.8]
2. 新开终端窗口
3. 进到camille目录
cd android/privacy/camille
3. 启动监控
python3 camille.py com.dicos
```

## 样例

```bash
// frida version: 16.0.2
// frida-server file version 16.0.2

[Terminal window 1]
    yarn startup
[Terminal window 2]
    yarn android:devDebug
[Terminal window 3]
    cd android/privacy
    adb push frida-server-16.0.2-android-arm64 /data/local/tmp
    adb shell
    su
    cd /data/local/tmp
    chmod 777 frida-server-16.0.2-android-arm64
    ./frida-server-16.0.2-android-arm64
[Terminal window 4]
    cd android/privacy/camille
    python3 camille.py com.dicos
```
