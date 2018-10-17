
# 适用于零基础的新人指引教程

本篇主要包含如下内容：

- 注册 `Github` 账户
- 注册 CNCF/CLA 会员
- 领取翻译任务
- Fork 翻译库并切换分支翻译
- 向上游指定分支提交 PR

### Step1. 准备工作

注册翻译账户

- `Github` 账户
- `CNCF/CLA` 会员

### Step2. 领取任务并翻译

- 领取翻译任务
- Fork 代码库
- 克隆代码翻译

#### 领取翻译任务
打开[翻译任务](https://docs.google.com/spreadsheets/d/1k49XTmtEkhjeh9M118fwwcXVfHvCe-DCy6sVVRQAxBk/edit#gid=1294143213)，领取翻译任务：

并认领一篇翻译任务：
![](./image/2018-10-17-19-32-00.png)

#### Fork 翻译库并切换分支翻译

![](./image/2018-10-17-16-57-49.png)

![](./image/2018-10-17-16-58-38.png)

![](./image/2018-10-17-16-59-20.png)

![](./image/2018-10-17-16-59-52.png)

![](./image/2018-10-17-17-05-04.png)

![](./image/2018-10-17-17-05-41.png)


#### 克隆代码翻译

准备本地翻译目录 `brucehex`,进入并 `clone` 代码

```bash
➜  brucehex git clone https://github.com/brucehex/website.git
Cloning into 'website'...
remote: Enumerating objects: 25, done.
remote: Counting objects: 100% (25/25), done.
remote: Compressing objects: 100% (17/17), done.
remote: Total 87507 (delta 8), reused 16 (delta 7), pack-reused 87482
Receiving objects: 100% (87507/87507), 129.35 MiB | 2.64 MiB/s, done.
Resolving deltas: 100% (56085/56085), done.
```

查看远程分支

```bash
# 查看远程分支
git branch -a
```
![](./image/2018-10-17-19-44-28.png)

- 翻译 `master` 分支
- 翻译 `release-1.12` 分支
- 翻译 `release-1.11` 分支
- 翻译 `release-1.10` 分支

##### 翻译 `master` 分支

```bash
git checkout master
```

##### 翻译 `release-1.12` 分支

```bash
git checkout release-1.12
```

##### 翻译 `release-1.11` 分支

```bash
git checkout release-1.11
```

##### 翻译 `release-1.10` 分支


```bash
git checkout release-1.10
```


### Step5. 向上游指定分支提交 `PR`

