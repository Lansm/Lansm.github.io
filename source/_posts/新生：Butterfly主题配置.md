---
title: 新生：Butterfly主题更替
categories:
  - 博客设置
tags:
  - Butterfly
  - Hexo
  - Git
  - Blog
  - CDN
  - 又拍云
abbrlink: bd4fbb72
date: 2020-11-20 12:46:21
description: Just write
cover: https://img.thaddeus.ink/self_images/anime_imgs/r233.png
---
### 重新启动

疫情后大家都有着自己的经历，新的生活节奏或者人生路上的一些小插曲，对于我们的未来走向都有着一定的影响。
说这些，只是为自己这么久没有打开博客，找到一个合适的借口。
前面查阅浏览资料时，不经意之间打开了[Cxsz](https://www.singlelovely.cn/)的友链[C1oudust](https://c1oudust.cn/)的友链[YML](https://menglei.xyz/)，突然感觉，哎哟不错哦。
这个博客主题第一时间就吸引到了我，然后就到了这里。
但是当我准备按照以前的步骤进行，以为只是简单地换个主题改个配置。但是不巧的是换了台笔记本。
问题来了，hexo搭建博客从走一遍？
这也太麻烦了，于是按照上一篇的步骤[备份hexo防止换电脑掉数据之类](https://blog.csdn.net/wxl1555/article/details/79293159)进行，却发现下载下来的主题文件夹是个空的。
不能接受，找了半天找不到错误，又去搜了老久的关于新环境写hexo博客的文章，最后找到了，[使用hexo，如果换了电脑怎么更新博客](https://www.zhihu.com/question/21193762)用户`直上云霄`的回答。
> 1. 搭建流程：  
创建仓库->分支master和hexo->设置hexo默认->git clone ……github.io.git  
->本地github.io文件夹下Git Bash执行 `npm install hexo`,`npm install`,`hexo init`,  
`npm install hexo-deployer-git` 此时分支显示为hexo  
->修改`_config.yml` 中deploy参数，分支应为master  
->`git add .` , `git commit -m "..."` , `git push origin hexo`   
->`hexo g -d` 生成并部署到github
> 2. 日常改动流程  
依次执行 `git add .` , `git commit -m "xxx"` , `git push origin hexo` 推送至github(hexo)  
然后执行 `hexo g -d` 发布网站到master分支  
虽然两个过程顺序调转一般不会出问题？
> 3. 丢失本地资料后流程  
使用 git clone git... 默认分支hexo  
本地新拷贝的github.io文件夹下 Git Bash执行 `npm install hexo`,`npm install`  
`npm install hexo-deployer-git` 此时分支显示为hexo  

其它的都是没有什么问题的，但是有一点：

> 注意，如果你之前克隆过`theme`中的主题文件，那么应该把主题文件中的`.git`文件夹删掉，因为`git`不能嵌套上传，最好是显示隐藏文件，检查一下有没有，否则上传的时候会出错，导致你的主题文件无法上传，这样你的配置在别的电脑上就用不了了。 

王德发…… 之前下载和上传忘了这茬
在以前没有将主题文件保存到`hexo`目录下，都是直接`git clone`下来直接改的，新版本`hexo`可以有`_config.butterfly.yml`这样，存于`hexo`根目录却覆盖原主题配置文件。
相关`Butterfly`主题配置，请看开发人员官方博客[Butterfly](https://butterfly.js.org/)。
下面记录一下遇到的上面没说的或者我新遇到的。

### qq跳转链接
用在了侧边栏的社交连接中，一搜就有
>网页版本点击跳转到添加好友界面：（直接用下面的链接地址，将`qq号`改成自己的即可）
>http://wpa.qq.com/msgrd?v=3&uin=1019678874&site=qq&menu=yes

### git clone 报错
>error: RPC failed;curl 18 transfer closed with outstanding read data remaining
>直接`https`改成`ssh`方式`clone`就行了,提前将`git`的`ssh`配置好。

### 主题同步更新
如果使用`git clone`直接使用主题，在自定义后不方便进行对比更新主题，因为只能够存在一个`.git`文件夹。
因此使用`git fork`再`git clone`自己库中主题，新建分支存储自己的修改主题文件。
`remote`查看远程信息，添加远程仓库，使用自己`fork`的目标，`fetch`和`pull`的区别使用是个重点。
从`upstream`源仓库拉取更新后`merge`进行对比合并，最后`push`推给自己的仓库。
结果就是主题更新可以正常同步，按需合并到自己的单独分支，实现自定义。
详情对比[fork他人的项目后，再同步更新别人的提交](https://blog.csdn.net/qq1332479771/article/details/56087333?utm_medium=distribute.pc_relevant.none-task-blog-BlogCommendFromBaidu-1.control&depth_1-utm_source=distribute.pc_relevant.none-task-blog-BlogCommendFromBaidu-1.control)

```bash
git remote -v
git remote add upstream git@github.com:username/rep.git
git fetch upstream
git merge upstream/master
git push
```
### 音乐功能
主题内置了音乐aplayer功能，在主题配置文件中inject里进行底部插入，默认代码已经完成了歌单，只需要更改id和音乐app类型即可。其它选项可以对比查看[aplayer官方文档](https://github.com/MoePlayer/hexo-tag-aplayer/blob/master/docs/README-zh_cn.md)
可通过音乐app的歌单分享链接进行查看对应id，建议链接中找不到id时换其他分享方式试一试。我自己就是PC分享和Android分享不一致才发现这个问题的。
导航栏的音乐页面是一个正常的自定义页面，官方提供下面代码添加了播放器页面。
```javascript
{% meting "7787176167" "tencent" "playlist" "theme:#FF4081" "mode:circulation" "mutex:true" "listmaxheight:340px" "preload:auto" %}
```
### 又拍云CDN与云存储
u1s1，又拍云人工客服挺给力，基本秒回我解决问题。关于DNS解析配置，HTTPS访问问题，SSL证书配置，CDN加速问题，都是问他解决的。还有送的代金券和又拍云联盟的免费流量，基本够用了。
就说一下干了什么吧。
- 申请免费SSL证书实现HTTPS
- 通过二级域名进行云存储绑定
- 上传图片等文件
- CDN加速

### Butterfly其它美化
- [Butterfly主题优雅更换背景](https://www.antmoe.com/posts/7198453/index.html)
- [butterfly主题优雅魔改系列（持续更新）](https://www.antmoe.com/posts/a811d614/index.html)
- [血小板Live2d](https://menglei.xyz/2020/11/05/%E4%B8%BB%E9%A2%98%E7%BE%8E%E5%8C%96%E5%A4%87%E5%BF%98/)
