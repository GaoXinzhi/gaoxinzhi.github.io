---
title: "ROS服务"
layout: single
author_profile: true
read_time: true
comments: true
share: true
related: true
show_date: true
# toc: true
# toc_label: "My Table of Contents"
# toc_icon: "file-alt"
tags: c++ ros 机器人 python ros服务  #调整文章的标签
categories: ros # 调整文章的分类
excerpt: "ros中的service以及命令工具"
# classes: wide # 如果没有右面的导航栏的话将内容进行右填充如果有右侧导航栏会很难看

# 开始的大图片以及上面的文字

header:
  teaser: ../assets/postimage/ros/ros.jpeg #预览时显示的图片
#   overlay_image: ../assets/images/back.webp
#   # overlay_filter: rgba(255, 0, 0, 0.5)  #可以调整一些图像的色彩等
#   caption: "Photo credit: [**Unsplash**](https://unsplash.com)"
#   actions:
#     - label: "More Info"
#       url: "https://unsplash.com"

#这是作者栏那个位置的导航格如果想用这个东西先将上面的author_profile关掉

# sidebar: 
#   - title: "Title"
#     image: http://placehold.it/350x250
#     image_alt: "image"
#     text: "Some text here."
#   - title: "Another Title"
#     text: "More text here."
# 如果想一个更骚点的导航栏，像教程里的那样，参见 https://mmistakes.github.io/minimal-mistakes/docs/layouts/#custom-sidebar-navigation-menu
---

# ros服务

服务（Services）是节点之间通讯的另一种方式。服务允许节点发送一个请求（request）并获得一个响应（response）。

## rosservice

常见的rosservice命令

```shell
rosservice list     输出活跃服务的信息
rosservice call [service] [args]    用给定的参数调用服务
rosservice type [service]    输出服务的类型
rosservice find     按服务的类型查找服务
rosservice uri      输出服务的ROSRPC uri
```

## rosparam(参数服务器)

rosparam能让我们在ROS参数服务器（Parameter Server）上存储和操作数据。参数服务器能够存储整型（integer）、浮点（float）、布尔（boolean）、字典（dictionaries）和列表（list）等数据类型。rosparam使用YAML标记语言的语法。一般而言，YAML的表述很自然：1是整型，1.0是浮点型，one是字符串，true是布尔型，[1, 2, 3]是整型组成的列表，{a: b, c: d}是字典。

用法：

```shell
rosparam set [param_name] value    设置参数
rosparam get [param_name] value    获取参数
rosparam load [file_name.yaml] [namespace]    从文件中加载参数
rosparam dump [file_name.yaml] [namespace]    向文件中转储参数
rosparam delete     删除参数
rosparam list       列出参数名
```
