---
title: "ROS节点"
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
tags: c++ ros 机器人 python ros结点  #调整文章的标签
categories: ros # 调整文章的分类
excerpt: "ros图的概念以及一些其他的命令行工具的使用"
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

# ros节点

## 图概念

计算图（Computation Graph）是一个由ROS进程组成的点对点网络，它们能够共同处理数据。ROS的基本计算图概念有节点（Nodes）、主节点（Master）、参数服务器（Parameter Server）、消息（Messages）、服务（Services）、话题（Topics）和袋（Bags），它们都以不同的方式向图（Graph）提供数据。

* 节点（Nodes）：节点是一个可执行文件，它可以通过ROS来与其他节点进行通信。
* 消息（Messages）：订阅或发布话题时所使用的ROS数据类型。
* 话题（Topics）：节点可以将消息发布到话题，或通过订阅话题来接收消息。
* 主节点（Master）：ROS的命名服务，例如帮助节点发现彼此。
* rosout：在ROS中相当于stdout/stderr（标准输出/标准错误）。
* roscore：主节点 + rosout + 参数服务器（会在以后介绍）。

## 节点

节点本质上就是ros软件包的一个可执行文件，ros节点使用ros客户端库与其他节点通信。节点可以发布或订阅话题，也可以提供或者使用服务。

## 客户端库

ros客户端库可以让用不同编程语言编写的节点相互通信。比如rospy和roscpp

## roscore

ros主节点，使用ros必须打开。

## rosnode

rosnode显示当前正在运行的ros节点信息。

```shell
rosnode list
输出：/rosout
```

rosout节点用来收集和记录节点的调试输出，所以一直在运行。

```shell
下面的命令可以返回某个指定节点信息
rosnode info /rosout
```

## rosrun

rosrun可以用包名直接运行软件包内的节点。用法：

```shell
rosrun [package_name] [node_name] [__name:==alias(重命名)]
下面的命令可以用来测试节点状态
rosnode ping my_turtle
```

