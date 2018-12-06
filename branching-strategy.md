# 翻译过程中的分支管理

分支管理主要是提供多任务翻译的参考指引，方便译者借鉴使用。
本文档主要讨论怎么做分支策略。

需要理解和注意以下几点：
- 三个代码仓库
- 任务不要交叉
- 分支策略

## 三个 repo
git 是一个分布式版本管理系统。在翻译过程中，我们会涉及到三个代码仓库。
1. website repo，也就是upstream repo，你需要 `git remote add upstream` 将其配置为 upstream repo
2. fork repo，如果你从这里 clone 的话，也就是对应的 origin repo
3. local repo，所有的分支管理都是从这里发起的。

## 一个任务一个分支
因为我们讨论的是文档翻译，所以这里讨论的文档是单个的文章（也包含附带所需的源文件）。
一个任务一个分支的目的是，保证在 PR merge的时候不会发生冲突。
换言之，PR merge 不存在先后关系，可以独立进行。

## 分支策略

假设文档为 `x1`，已经完成 PR 提交操作（`website:release-1.12 <- fork:zh-trans-x1`），下面是可能存在的相关分支。

```
website:    release-1.12
fork:       release-1.12    zh-trans-x1
local:      release-1.12    zh-trans-x1
```

这里的故事可以分为以下几步：

1. 在 Github UI 上完成 fork 操作，所以，`website:release-1.12` 对应到 `fork:release-1.12`
2. `git clone` 到本地，所以 `fork:release-1.12` 对应到 `local:release-1.12`
3. 创建 `local:zh-trans-x1` 分支并翻译
4. 提交 commit，并推送到 `fork:zh-trans-x1`
5. Github UI 发起 PR （`website:release-1.12 <- fork:zh-trans-x1`）

这里需要注意的是，`website:release-1.12` 和 `fork:release-1.12` 经常会
不一致（`website:release-1.12` 是 source of truth 会有很多 fork 来的 commits），
这并不是什么大的问题（虽然不好看）。

有了上面的认识，下面就是一步一步的命令行，假定上面的 `zh-trans-x1` 已经被合并，需要开始新的 `zh-trans-x2` 翻译：

1. `git checkout release-1.12`
2. `git pull upstream release-1.12`
3. `git checkout -b zh-trans-x2`
3. (translating)
4. `git add . && git commit -m 'zh-trans: add x2'`
5. `git push origin zh-trans-x2` # origin is your fork
6. via Github UI (`website:release-1.12 <- fork:zh-trans-x2`)
