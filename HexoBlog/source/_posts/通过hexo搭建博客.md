---
title: 通过hexo搭建博客
date: 2018-03-07 00:02:40
tags:
---
# mac下 hexo+github 分分钟搭建博客

# 环境依赖
## [安装git](https://git-scm.com/download/)
## [安装node.js](http://nodejs.cn/download/)
## 安装hexo 
`npm install -g hexo`
在桌面自定义一个文件夹HEXO（安装hexo的路径）在此路径下
*初始化*
`hexo init`
*安装依赖包*
`npm install`
*hexo环境已经搭建完毕现在我们就可以用hexo迅速自动创建博客了，里面默认有一个hello.md想看效果的话终端输入下面两条指令：*
`hexo g`
`hexo s`
*浏览器输入localhost:4000，可以看到默认的hello博客，也可以新创建一个:*
`hexo new "myblog"`
*myblog.md在HEXO/source/_posts路径下可以看到，我们就可以用markdown软件编辑了，非常方便，每次创建新的博客都要*
`hexo clean`
`hexo g`
`hexo deploy`
*就是清除hexo上次自动构建时环境中的缓存文件和本次生成新的文件，在本地查看还可以让hexo启动本地服务*
`hexo s`
*在localhost:4000中查看，本地的我们学会了接下来就是关联到github远端了*
# hexo发布在github 上（关联）
登录到你的github，新建一个repository。新建repository，仓库名字应当为 “你的github用户名.github.io”。
将此仓库克隆下来，记住克隆的网址（例如“https://github.com/chrisdapen/chrisdapen.github.io.git”）
克隆后，将桌面的HEXO文件夹拷贝到克隆的repository中。修改其中的“_config.yml”文件。在最后一行添加替换（repository 后就是我们克隆仓库的 https）

```
deploy:
  type: git
  repository:
            github: https://github.com/chrisdapen/chrisdapen.github.io.git
  branch: master
```
将修改后的所有文件push到远端。然后本地repository中的HEXO文件路径执行
```
hexo clean 
hexo g
hexo deploy
```
执行hexo deploy 时可能会报错ERROR Deployer not found: git 或者 ERROR Deployer not found: github
解决方法： npm install hexo-deployer-git –-save
然后再把本地有变化的文件提交到远端 重新执行
```
hexo clean 
hexo g
hexo deploy
```
此时就已经ok 了。我们等待hexo deploy执行完毕，就可以在浏览器输入“https://chrisdapen.github.io/” 进行访问我们的hexo 博客了。 
https://你的仓库名字也就是github用户名.github.io/
# 切换主题
搜自己喜欢的主题。然后在 clone到hexo的themes 文件夹下。 
然后修改hexo的“_config.yml”文件。。

```
# Extensions
## Plugins: https://hexo.io/plugins/
## Themes: https://hexo.io/themes/
theme: next
```
再次执行
```
hexo clean
hexo g
hexo deploy
```
耐心等待hexo deploy执行完毕（因为要部署的文件比较多。所以可能会比较慢，需要几分钟）部署成功后再次访问 
https://你的仓库名字也就是github用户名.github.io/
# 发布博客
发布一篇博客很简单在“hexo\source_posts” 目录下将编辑好的.md 文件（博客只支持.md文件。也就是使用markdown 编写的文件）复制进去，然后提交到远端。再次执行

```
hexo clean
hexo g
hexo deploy
```
就把写好的博客放上去了。
 


