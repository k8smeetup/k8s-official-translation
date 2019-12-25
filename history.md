# Kubernetes 本地化工作历史记录

## 翻译进程主要有两个阶段：

### 前情概要

翻译项目在 `2017/7/17` 启动至 `2018/4/15` 都是基于上游 `Master` 分支去翻译，当时上游的文档是基于 `jekyll` 构建，无法提供多语言的支持。为此从 `2018/4/15` 开始，为期三/四个月，将文档库由 `jekyll` 切换至 `hugo` 构建，由于同步信息的时效比较差，翻译项目陷于停滞。由于迁移和翻译基于 `master` 分支的副作用，造成很多翻译过的文档无法合入。

基于 `KUBECON` 在上海的契机, 多语言版本提上日程，原有的任务领取方式已经不能满足要求，而且`Google 任务表` 领取也不方便，因此目前新的流程应运而生。

经社区成员讨论一致决定基于目前最新的 `release-1.16` 分支作为基准翻译分支，大家提交 `PR` 时,不要选择 `Master` 分支。

### 第一阶段：基于 [website](https://github.com/kubernetes/website) 仓库的 `master` 分支进行翻译

主要的上游工作仓库是 [kubernetes-docs-zh](https://github.com/kubernetes-retired/kubernetes-docs-zh)

- 时间区间：2017/07/17 - 2018/4/15 
- 成果输出：翻译图表 [DashBoard](https://k8smeetup.github.io/chart)，附每周的翻译[文章汇总](report/contribution-stage1.md)。
- 任务领取：基于 Google Docs [任务表]((https://docs.google.com/spreadsheets/d/1k49XTmtEkhjeh9M118fwwcXVfHvCe-DCy6sVVRQAxBk/edit#gid=1294143213))协作
  
- 此阶段：
  - 通过 Google 在线 EXCEL 表格实现任务管理
  - 任务存储到 PGSQL 数据库中

### 第二阶段：基于 [website](https://github.com/kubernetes/website) 仓库的 relese-1.14 分支进行翻译

主要的上游工作仓库是 [website](https://github.com/kubernetes/website)

- 时间区间：2018/11/13 - 2019/10/1
- 成果输出：
    - [Merged PR 列表](https://github.com/kubernetes/website/pulls?utf8=%E2%9C%93&q=is%3Apr+is%3Amerged+label%3Alanguage%2Fzh+)
    - 进度展示图 [DashBoard](https://k8smeetup.github.io/k8s-official-translation/index-2.html)
    - 每周的[翻译文章汇总](report/contribution-stage2.md)
    - 每周的[更新文章汇总](report/contribution-stage2-update.md)
- 任务领取：全部基于 Github 即有功能实现，通过 [website-tasks](https://github.com/k8smeetup/website-tasks/issues) 仓库实现

- 此阶段：
  - 通过 Github API V3 实现任务管理 - (管理任务是个很消耗时间的工作)
  - 任务存储到 PGSQL 数据库中

#### 201908-09 时间段的翻译进度

- 进度展示图 [DashBoard](https://k8smeetup.github.io/k8s-official-translation/index-201908_09.html)

### 第三阶段：基于 [website](https://github.com/kubernetes/website) 仓库的 relese-1.16 分支进行翻译

- 时间区间：2019/10/1 - 2019/12/8
- 成果输出：
    - [Merged PR 列表](https://github.com/kubernetes/website/pulls?utf8=%E2%9C%93&q=is%3Apr+is%3Amerged+label%3Alanguage%2Fzh+)
    - 进度展示图 [DashBoard](https://k8smeetup.github.io/k8s-official-translation/index-3.html)
    - 每周的[翻译文章汇总](report/contribution-stage3.md)
    - 每周的[更新文章汇总](report/contribution-stage3-update.md)
- 任务领取：全部基于 Github 即有功能实现，通过 [website-tasks](https://github.com/k8smeetup/website-tasks/issues) 仓库实现
  - release-1.16 issue task 基于[此 PR 构建](https://github.com/kubernetes/website/pull/16805)

- 此阶段：
  - 重构代码，通过 Github API V4 实现任务管理(任务创建速度提升了数十个数量级，且不会出现超时问题)
  - 任务存储到 PGSQL 数据库中