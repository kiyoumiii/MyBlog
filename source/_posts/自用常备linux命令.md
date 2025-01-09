---
title: 自用常备linux命令
date: 2024-12-28 18:43:12
categories:
- [计算机科学]
tags:
- [linux]
---

## 自用的一些常备linux命令

基本命令如cd ls pwd mkdir rm cp mv touch等

以及如下这些：

``` bash
# 查看设备空间使用情况
df -h
```

``` bash
# 查看本计算节点使用情况
top
```

``` bash
# 查看文件的生成时间戳
stat <filename>
```

``` bash
# 查看进程
ps -ef | grep 'work12.sh'
```

``` bash
# 杀死进程
kill <pid>
```

``` bash
# 杀死用户为<username>的进程
pkill -u <username>
```

``` bash
# 查看CPU核数
nproc
```

``` bash
# 运行任务
nohup taskset -c 0-1 sh work1.sh >/dev/null 2>&1 &
nohup taskset -c 2-3 sh work2.sh >/dev/null 2>&1 &
nohup taskset -c 4-5 sh work3.sh >/dev/null 2>&1 &
nohup taskset -c 6-7 sh work4.sh >/dev/null 2>&1 &
nohup taskset -c 8-9 sh work5.sh >/dev/null 2>&1 &
nohup taskset -c 10-11 sh work6.sh >/dev/null 2>&1 &
nohup taskset -c 12-13 sh work7.sh >/dev/null 2>&1 &
nohup taskset -c 14-15 sh work8.sh >/dev/null 2>&1 &
nohup taskset -c 16-17 sh work9.sh >/dev/null 2>&1 &
nohup taskset -c 18-19 sh work10.sh >/dev/null 2>&1 &
nohup taskset -c 20-21 sh work11.sh >/dev/null 2>&1 &
nohup taskset -c 22-23 sh work12.sh >/dev/null 2>&1 &
```

清除原本的minimized_pdb文件，以及，查看当下文件中minimized_pdb文件数量的命令：

``` bash
find . -type f -name '*_minimized.pdb' -exec rm -f {} +
find . -type f -name '*_minimized.pdb' | wc -l
```

限时60s，并指定每个任务占据核的编号

``` bash
# 前8个任务，每个任务使用2个核心
timeout 60s taskset -c 0-1 sh work1.sh &
timeout 60s taskset -c 2-3 sh work2.sh &
timeout 60s taskset -c 4-5 sh work3.sh &
timeout 60s taskset -c 6-7 sh work4.sh &
timeout 60s taskset -c 8-9 sh work5.sh &
timeout 60s taskset -c 10-11 sh work6.sh &
timeout 60s taskset -c 12-13 sh work7.sh &
timeout 60s taskset -c 14-15 sh work8.sh &

# 后8个任务，每个任务使用1个核心
timeout 60s taskset -c 16 sh work9.sh &
timeout 60s taskset -c 17 sh work10.sh &
timeout 60s taskset -c 18 sh work11.sh &
timeout 60s taskset -c 19 sh work12.sh &
timeout 60s taskset -c 20 sh work13.sh &
timeout 60s taskset -c 21 sh work14.sh &
timeout 60s taskset -c 22 sh work15.sh &
timeout 60s taskset -c 23 sh work16.sh &

# 等待所有后台任务完成
wait
```

查看当下文件夹下每个文件占据多少空间

``` bash
du -h --max-depth=1 | sort -hr
```

常用的一套命令

``` bash
find . -type f -name '*_center.pdb' | wc -l
rsync -auvh *_center.pdb ../recon11_5w_center/
vim get(tab补全)
module load Anaconda3
conda activate
vim minimi_dihe(tab补全)
module load NAMD/CPU/2.14
ps -ef | grep 'work12.sh'
find . -type f -name '*_minimized.pdb' | wc -l

rsync -auvhz *_minimized.pdb zhaomiaomiao@XXXLab:/mnt/sto2/zhaomiaomiao/select_trainset_241203/mini4w_reconset/mini_pdbs/recon1_4w_pdb/

rsync -auvhz *.log zhaomiaomiao@XXXLab:/mnt/sto2/zhaomiaomiao/select_trainset_241203/mini4w_reconset/mini_logs/recon1_4w_log/
```

另一套命令

``` bash
module load CUDA/11.0.0
module load VMD/1.9.3
vmd -dispdev none -e hbb_align2initial.tcl.txt
```