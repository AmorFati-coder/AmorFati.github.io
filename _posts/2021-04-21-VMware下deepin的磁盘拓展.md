---
title: VMware下deepin的磁盘拓展
date: 2021-04-21
categories: Debug
tags: disk
description: 需要扩容，但碰到各种问题
---

## 系统

- win 10
- deepin20
- VMware16

## 问题解决

> 仅用于个人问题的记录

- VMware扩充虚拟硬盘

- 进入deepin进行操作

  ### 删除已有硬盘分区

  ```shell
  fdisk /dev/sda
  Command (m for help): d
  Selected partition 1
  
  Command (m for help): d
  No partition is defined yet!
  
  Command (m for help): w
  ```

  - 选择d：删除分区
  - 选择w：保存

  ### 分区

  ```shell
  fdisk /dev/sda
  
  <<'COMMENT'
  Command (m for help): n
  Partition type:
     p   primary (0 primary, 0 extended, 4 free)
     e   extended
  Select (default p): p
  Partition number (1-4, default 1): 1
  First sector (2048-31703039, default 2048): 
  Using default value 2048
  Last sector, +sectors or +size{K,M,G} (2048-31703039, default 31703039): 
  Using default value 31703039
  
  Command (m for help): w
  ```

  - 选择n：创建分区
  - 选择p：主分区
  - 选择e：逻辑分区
  - Partition number：分区个数。这里选择分为一个区
  - First sector：第一块扇区号。这里以2048为开始
    - With the death of the legacy BIOS (ok, its not quite dead yet) and its replacement with EFI BIOS, a special boot partitionis needed to allow EFI systems to boot in EFI mode. Starting the first partition at sector 2048 leaves 1Mb for the EFI boot code. Modern partitioning tools do this anyway and fdisk has been updated to follow suit. 大意为，由于EFI的兴起，要给EFI 代码留磁盘最开始的1M空间
  - Last sector：最后一块扇区号。这里默认代表全部的扇区，也可以制定大小，例如`+1024m`，即分出`1G`空间
  - 选择w：保存退出

### 格式化

```shell
mkfs -t ext4 /dev/sda1
resize2fs /dev/sda1
```

### 重启deepin解决问题

## 参考资料

https://o-my-chenjian.com/2017/05/10/Play-Disk-On-Linux/