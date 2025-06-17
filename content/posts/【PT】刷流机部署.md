+++
title = "【PT】刷流机部署！"
date = 2023-06-15T22:01:00+08:00
draft = false
+++

## 【PT】刷流机部署

### 部署环境

+   Debian11，AMD架构
    
+   硬盘：推荐nvme SSD，I/O得高，否则任务多了就跟不上，大小建议160或以上
    
+   机房位置：通常推荐欧洲地区，特别是德国，其次美西，国内机不在本教程范围
    
+   推荐盒子商：`Hetzner`、`Netcup`、`BuyVM`等，其中BuyVM的附加硬盘I/O较低，建议刷流时限制在`3`个任务以内
    

### 部署步骤

> 以后有空可能会写个shell脚本，目前就这样吧

1.  基础安装
    

```
apt update && apt -y upgrade && apt -y autoremove && apt install -y curl vim sudo xfsprogs && mkdir Downloads&& chmod -R 777 ./Downloads
```

2.  安置刷流环境
    

```
bash <(wget -qO- https://raw.githubusercontent.com/jerry048/Dedicated-Seedbox/main/Install.sh) <用戶名稱> <用戶密碼> <緩存大小(單位:MiB)>
示例：
bash <(wget -qO- https://raw.githubusercontent.com/jerry048/Dedicated-Seedbox/main/Install.sh) admin adminadmin 512
```

建议选择qBittorrent `4.3.8` ，安装 `bbrx` 等选项

3.  修复DNS缺失（选做）
    

```
sudo chattr -i /etc/resolv.conf
rm /etc/resolv.conf  && echo "nameserver 8.8.8.8" > /etc/resolv.conf && echo "nameserver 1.1.1.1" > /etc/resolv.conf && chattr +i /etc/resolv.conf
```

4.  其他相关教程
    

+   [Buyvm VPS挂载外挂硬盘（Block Storage Slabs存储块）方法和刷PT流程](https://vpsceping.org/955.html)
    
+   [Linux磁盘挂载及格式化文件系统格式为xfs](https://blog.csdn.net/qq_38860027/article/details/126953476)
    
+   [Hetzner Cloud使用Volume给主硬盘扩容无缝合并及保姆级PT盒子刷流教程 不到10€/月实现AMD 2核/2G/160G/10g带宽@无限流量](https://vpsceping.org/1023.html)
    

* * *