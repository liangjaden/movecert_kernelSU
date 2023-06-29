# 安卓13 HttpCanary 证书安装

## 安装KernelSU
[参考这个](https://github.com/tiann/KernelSU)


我已把证书提取出来做成模块包了，理论上直接刷入即可，如不行可以按下面提取打包刷入。

## 准备证书
 HttpCanary导出证书
HttpCanary -> 设置 -> SSL证书设置 -> 导出HttpCanary根证书 -> System Trusted(.0)


## 制作模块
模块文件结构为

```bash
movercert_kernelSU
├── META-INF
│   └── com
│       └── google
│           └── android
│               ├── update-binary
│               └── updater-script
├── module.prop
└── system
    └── etc
        └── security
            └── cacerts
                ├── aaaaaaaa.0
                └── bbbbbbbb.0
```
将前面导出的证书复制到 system/etc/security/cacerts 下面，将movercert_kernelSU压缩成zip
## 安装模块
将压缩包推送到手机,通过KernelSU安装模块，重启生效。

参考：
https://github.com/DabanC/android_install_ca_certificate
感谢上链作者~~