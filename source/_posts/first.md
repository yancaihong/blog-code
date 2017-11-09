---
title: 在GitHub上部署Hexo博客
date: 2017-11-04 23:02:37
tags: 环境搭建
---
### 第一步 登录GitHub，创建一个新的仓库，用来存储博客源码

### 第二步 打开终端，查看当前目录

``` bash
$ pwd 
```
  
查看当前目录下的子目录
  
``` bash
$ ls
```

进入想要放置代码的目录，输入以下命令（其中的 SSH address 指第一步中创建好的仓库的ssh地址）：

``` bash
$ git clone <SSH address>
```

### 第三步 为了提高安装依赖包的效率，需要安装cnpm，输入以下命令（其中，sudo 命令用来以其他身份来执行命令）：

``` bash
$ sudo npm install -g cnpm --registry=https://registry.npm.taobao.org
```
  
接着安装模块
  
``` bash
$ cnpm install
```

### 第四步 安装并初始化hexo

``` bash
$ cnpm install -g hexo-cli
```
``` bash
$ hexo init
```

此时，输入以下命令即可在浏览器中访问 http://localhost:4000

``` bash
$ hexo server
```

### 第五步 开发自己的第一篇博客

``` bash
$ hexo new <title>
```

命令执行结束，source文件夹下会出现 <title>.md 的文件，可以编辑此文件来撰写自己的文章

### 第六步 GitHub创建一个新的仓库，用来部署博客，仓库名称必须为 <yourname>.github.io（其中，yourname 是GitHub账号的名称）

### 第七步 安装 hexo-deployer-git

``` bash
$ npm install hexo-deployer-git --save
```

修改配置，_config.yml 文件，修改以下部分
  deploy:
    type: git
    repo: <repository url>  ## 第六步创建的仓库 SSH 地址
    branch: [branch]  ## 分支
    
### 第八步 部署到GitHub上

先清除
  
``` bash
$ hexo clean
```

生成文件 （generate）

``` bash
$ hexo g
```

部署至GitHub （deploy）

``` bash
$ hexo d
```

完成！