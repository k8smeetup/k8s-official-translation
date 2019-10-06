# 本地构建测试站点

## Step1. 下载 website 文档

```bash
git clone https://github.com/kubernetes/website.git
```

## Step2. 切换翻译分支

```bash
cd website
git checkout release-1.16
```

## Step3. 本地构建镜像

```bash
$ make docker-image
docker build . --tag kubernetes-hugo --build-arg HUGO_VERSION=0.58.3
Sending build context to Docker daemon 3.584 kB
Step 1/7 : FROM alpine:latest
 ---> 961769676411
Step 2/7 : MAINTAINER Luc Perkins <lperkins@linuxfoundation.org>
 ---> Using cache
 ---> ff58e0dae7fe
Step 3/7 : RUN apk add --no-cache     curl     git     openssh-client     rsync     build-base     libc6-compat
 ---> Using cache
 ---> 251404d9db2e
Step 4/7 : ARG HUGO_VERSION
 ---> Using cache
 ---> f63f9a7be288
Step 5/7 : RUN mkdir -p /usr/local/src &&     cd /usr/local/src &&     curl -L https://github.com/gohugoio/hugo/releases/download/v${HUGO_VERSION}/hugo_extended_${HUGO_VERSION}_Linux-64bit.tar.gz | tar -xz &&     mv hugo /usr/local/bin/hugo &&     addgroup -Sg 1000 hugo &&     adduser -Sg hugo -u 1000 -h /src hugo
 ---> Running in 33fc2c8d40c3

  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100   629    0   629    0     0   2885      0 --:--:-- --:--:-- --:--:--  2872
100 12.0M  100 12.0M    0     0  7944k      0  0:00:01  0:00:01 --:--:-- 20.5M
 ---> cb1b6fc15918
Removing intermediate container 33fc2c8d40c3
Step 6/7 : WORKDIR /src
 ---> 16ea20870369
Removing intermediate container f426d22bc92b
Step 7/7 : EXPOSE 1313
 ---> Running in 4bd794e98708
 ---> 5415ba8e281e
Removing intermediate container 4bd794e98708
Successfully built 5415ba8e281e
```

如果本地编译有困难，可以直接使用我已经编译好的镜像

```bash
# golang 版本
# docker pull quay.io/caicloud/kubernetes-hugo:0.58.3-go
docker pull quay.io/caicloud/kubernetes-hugo:0.58.3
docker tag quay.io/caicloud/kubernetes-hugo:0.58.3 kubernetes-hugo
```

## Step4. 本地构建预览效果

本地构建需要至少 2CPU/4G 的计算资源，建议在 4CPU/8G 或更高配置的环境里编译构建..

```bash
$ make docker-serve
docker run --rm --interactive --tty --volume /Users/dxwsker/works/github/issueflow/errbot-plugin/errbot/repository/website:/src -p 1313:1313 kubernetes-hugo hugo server --buildFuture --bind 0.0.0.0
Building sites … WARN 2019/10/06 14:55:47 Content directory "/src/content/en/docs/reference/kubernetes-api" have both index.* and _index.* files, pick one.
WARN 2019/10/06 14:55:47 Content directory "/src/content/en/docs/reference/kubernetes-api" have both index.* and _index.* files, pick one.
WARN 2019/10/06 14:55:47 Content directory "/src/content/en/docs/reference/kubernetes-api" have both index.* and _index.* files, pick one.

                   |  EN  |  ZH  |  KO  |  JA  |  FR  |  DE  |  ES  |  PT  |  ID
+------------------+------+------+------+------+------+------+------+------+------+
  Pages            | 1069 |  208 |  270 |  136 |  206 |  103 |  144 |   25 |   83
  Paginator pages  |  296 |    7 |    0 |    0 |    0 |    0 |    0 |    0 |    0
  Non-page files   |  439 |  181 |  151 |  215 |  107 |   67 |   78 |   12 |   42
  Static files     | 1012 | 1012 | 1012 | 1012 | 1012 | 1012 | 1012 | 1012 | 1012
  Processed images |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0
  Aliases          |    5 |    1 |    0 |    0 |    1 |    1 |    1 |    1 |    0
  Sitemaps         |    2 |    1 |    1 |    1 |    1 |    1 |    1 |    1 |    1
  Cleaned          |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0 |    0

Total in 52727 ms
Watching for changes in /src/{archetypes,assets,content,data,i18n,layouts,static}
Watching for config changes in /src/config.toml
Environment: "development"
Serving pages from memory
Running in Fast Render Mode. For full rebuilds on change: hugo server --disableFastRender
Web Server is available at http://localhost:1313/ (bind address 0.0.0.0)
Press Ctrl+C to stop

```

浏览器打开 `http://localhost:1313/zh/` 查看效果..

## Step5. 翻译并查看翻译效果

hugo 默认开启了实时预览效果，只要有翻译的内容，浏览器会实时刷新..


## 修复本地 build 问题

```bash
$ make docker-serve
docker run --rm --interactive --tty --volume /Users/dxwsker/works/github/issueflow/errbot-plugin/errbot/repository/website:/src -p 1313:1313 kubernetes-hugo hugo server --buildFuture --bind 0.0.0.0
Building sites … WARN 2019/10/06 15:01:27 Content directory "/src/content/en/docs/reference/kubernetes-api" have both index.* and _index.* files, pick one.
WARN 2019/10/06 15:01:27 Content directory "/src/content/en/docs/reference/kubernetes-api" have both index.* and _index.* files, pick one.
WARN 2019/10/06 15:01:27 Content directory "/src/content/en/docs/reference/kubernetes-api" have both index.* and _index.* files, pick one.
Total in 37702 ms
Error: Error building site: "/src/content/en/docs/tutorials/clusters/apparmor.md:126:1": failed to render shortcode "capture": failed to process shortcode: "/src/layouts/shortcodes/code.html:14:16": execute of template failed: template: shortcodes/code.html:14:16: executing "shortcodes/code.html" at <readFile $filename>: error calling readFile: runtime error: invalid memory address or nil pointer dereference
make: *** [docker-serve] Error 255
```

解决方案: https://github.com/kubernetes/website/pull/16708