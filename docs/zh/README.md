# 介绍

可以先看更清晰直观的视频教程 <br >
https://search.bilibili.com/all?keyword=APIJSON&from_source=webtop_search&spm_id_from=333.851
![image](https://user-images.githubusercontent.com/5738175/135413311-0207ec13-f7ea-4767-9e34-1a6d08438295.png)

其它各种官方和第三方文档见首页相关推荐 <br >
https://github.com/Tencent/APIJSON#%E7%9B%B8%E5%85%B3%E6%8E%A8%E8%8D%90

## 接口开发

首先是看名字 APIJSON，API 是说这个项目是属于接口开发的项目，JSON 是指传输数据格式是 JSON 格式。介于各位看官的水平高低不齐，这里就先为没有项目经验朋友啰嗦两句接口开发的内容。有经验的朋友可以跳到 “功能说明” 继续查看。

## 功能说明

一个接口的开发（本文档暂时只提供 Java 版本），比如 Java 用 SpringBoot，Mybatis 来开发一般来说就像下面这个流程

![home 1](../.vuepress/public/assets/home1.png)

部署上这个项目后，流程变成了这样

![home 2](../.vuepress/public/assets/home2.png)

换句话说，使用这个项目作为后端的支持的话，是不需要对每个表写增删改等接口的，只需在该项目连接的数据里进行表的创建，以及配置接口权限即可。无需进行过多的开发，哪怕是要改结构也仅仅只需要修改表字段而已。想想仅仅是部署一个后端项目，现在需要写的接口就基本写好了，直接调用就行了，是不是挺爽的。

说这么多，咱们直接开干吧！
