---
title: centOS：宝塔+docker+青龙
date: 2021-11-29 15:20:08
categories:
tags:
description:
---


更新与安装docker
sudo yum check-update
curl -fsSL https://get.docker.com/ | sh
sudo systemctl start docker
sudo systemctl status docker
sudo systemctl enable docker

图形化docker
putty + XShell
windows安装Xming 
看任务栏Xming 
设置SSH隧道 x11转发设置 localhost:0.0
连接服务器
yum -y install xorg-x11-xauth

测试图形界面
yum -y install firefox gedit
浏览器和编辑器
gedit
firefox
都可以成功打开
问题：未找到libGL.so.1
网络上install libgl1-mesa-glx
库里只能搜到 mesa-lib...
选了一个就行了


docker+青龙
加docker源 不然偶尔、经常找不到 whyour、
docker pull whyour/qinglong


最后需要注意企业微信设置，可能默认是只在企业微信内收到提醒



<!-- gdscripts
Secret=qQztXrHqC5Dq2719qCh2c4DEhJjMHcMV9ADBB1Pyt78

ww40e5ef0140a60a6d,qQztXrHqC5Dq2719qCh2c4DEhJjMHcMV9ADBB1Pyt78,@all,1000002,2ojYQJmbRmJafbfjIbQBUqQMLpFc_4MXc-nNn5awJwvv1SeLXkZ81nqWYKE2S9vD4&

2m_771b09jFchZT3eApIH1NRGgNqgDBGIZ4V5S5Ifh1p4PTIKAq8f_9J4UMPFwU1K

pt_key=AAJhpMBHADBrkGqq5xplSKNf2F37hpRI9F_uYs_mM-Qjibbnj3LHmd45D7H26dBXe1z5bMg5DVQ; pt_pin=jd_5af7f58bd49ef;
-->

宝塔
提示python

参考：
[青龙面板从零教程（一）](https://blog.csdn.net/weixin_42565036/article/details/117569495)
[centos安装图形x11 使用ssh转发](https://blog.csdn.net/weixin_42131601/article/details/113707277?utm_medium=distribute.pc_relevant.none-task-blog-2~default~baidujs_title~default-0.highlightwordscore&spm=1001.2101.3001.4242.1)
[找不到libGL.so库](https://blog.csdn.net/weixin_34910922/article/details/108589361?utm_medium=distribute.pc_relevant.none-task-blog-2~default~baidujs_title~default-0.no_search_link&spm=1001.2101.3001.4242.1)
[docker青龙面板安装与使用](https://zhuanlan.zhihu.com/p/387337954)
[Docker青龙+扫码Cookie](https://blog.csdn.net/qq_36010453/article/details/119334451)
[Linux Centos安装宝塔面板](https://www.cnblogs.com/wentutu/p/8549050.html)
[Centos7防火墙放行指定IP和端口](https://blog.csdn.net/m0_37911384/article/details/101545992)
[企业微信API](https://work.weixin.qq.com/api/doc/90000/90135/91039)
[青龙面板配置企业微信应用推送](http://www.dwf135.cn/2235.html)
