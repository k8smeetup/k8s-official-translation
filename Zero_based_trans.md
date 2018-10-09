
# 适用于零基础的新人指引教程

本篇主要包含如下内容：

- 注册 `Github` 账户
- 注册 CNCF/CLA 会员
- 领取翻译任务
- Fork 翻译库并切换分支翻译
- 向上游指定分支提交 PR

## Step1. 注册 `Github` 账户



## Step2. 注册 `CNCF/CLA` 会员

## Step3. 领取翻译任务

## Step4. `Fork` 翻译库并切换分支翻译

## Step5. 向上游指定分支提交 `PR`


下文待整理

```bash
任务地址：[翻译任务](https://docs.google.com/spreadsheets/d/1cF5ULp0-_Sw8HqiZXCk6nfBC0nq5NM-QboZ4tV7EopA/edit#gid=196779105)


译者在本地，克隆代码库
打开 https://github.com/译者账户/kubernetes-docs-zh

```bash
mkdir work
cd work
git clone https://github.com/译者账户/kubernetes-docs-zh.git
```

翻译文件，看一下翻译过的文件

```bash
cd ~/work/kubernetes-docs-zh
git status
```

添加修改过的文件至暂存区

```bash
// 例如翻译的文件是 cn/docs/setup/index.md
mkdir -p  content/en/docs/setup
cp content/en/docs/setup/index.md content/cn/docs/setup/

// 开始翻译此文档
vi content/cn/docs/setup/index.md
git add content/cn/docs/setup/index.md
```
提交到自己的本地库
```
// 翻译文件命名规则：文件夹间隔用 - 连接线代替，后面跟pr标志并加上文件版本日期
git commit -m 'cn-pr-trans-setup-index'
// push 到译者的github仓库 (输入用户名+密码)
git push
```

在译者的代码库创建PR

```bash
git add content/cn/docs/setup/index.md
git commit -m 'cn-pr-trans-setup-index-fix'
git push
```

参与翻译，首先需要有自己的 GITHUB 账户，先注册 GITHUB 账户
Fork [kubernetes-docs-zh](https://github.com/kubernetes/kubernetes-docs-zh) 代码库到译者自己的 Github 账户

#### 多版本翻译更新

更新翻译代码库
git remote add upstream https://github.com/kubernetes/kubernetes-docs-zh
git remote -v

git fetch upstream
git merge upstream/master
# 如果有代码冲突，解决冲突重新提交
git add .
git commit -m 'update-2018-10-02'
# 查看远程分支
git branch -a
# 拉取翻译分支 k8s 1.10
git checkout upstream/release-1.10-zh
git checkout -b release-1.10-zh
# 拉取翻译分支 k8s 1.11
git checkout upstream/release-1.11-zh
git checkout -b release-1.11-zh
# # 拉取翻译分支 k8s 1.12
git checkout upstream/release-1.12-zh
git checkout -b release-1.12-zh


git push --set-upstream origin release-1.10-zh:release-1.10-zh
git push --set-upstream origin release-1.11-zh:release-1.11-zh
git push --set-upstream origin release-1.12-zh:release-1.12-zh
f0f029d4e6e5aa8c641dedb5a28836b0149d8a67

➜  brucehex git:(release-1.12-zh) git push origin release-1.11-zh:release-1.11-zh
Username for 'https://github.com': brucehex
Password for 'https://brucehex@github.com':
Counting objects: 2384, done.
Delta compression using up to 2 threads.
Compressing objects: 100% (2054/2054), done.
Writing objects: 100% (2384/2384), 40.01 MiB | 1.42 MiB/s, done.
Total 2384 (delta 259), reused 1782 (delta 241)
remote: Resolving deltas: 100% (259/259), done.
remote:
remote: Create a pull request for 'release-1.11-zh' on GitHub by visiting:
remote:      https://github.com/brucehex/kubernetes-docs-zh/pull/new/release-1.11-zh
remote:
To https://github.com/brucehex/kubernetes-docs-zh.git
 * [new branch]      release-1.11-zh -> release-1.11-zh

 ```