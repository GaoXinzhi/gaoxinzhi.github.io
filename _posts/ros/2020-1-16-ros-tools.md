---
title: "ROS工具"
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
tags: c++ ros 机器人 python ros工具  #调整文章的标签
categories: ros # 调整文章的分类
excerpt: "ros中除了服务和话题之外便于开发所提供的一些工具"
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

# ros工具

## rqt_console 和 rqt_logger_level

rqt_console连接到了ROS的日志框架，以显示节点的输出信息。rqt_logger_level允许我们在节点运行时改变输出信息的详细级别，包括Debug、Info、Warn和Error`。

用法:

```shell
rosrun rqt_console rqt_console
rosrun rqt_logger_level rqt_logger_level
```

启动之后可以按照需要进行设置。其中日志记录器级别可以有以下顺序：

```shell
Fatal （致命）
Error （错误）
Warn  （警告）
Info  （信息）
Debug （调试）
```

## roslaunch

roslaunch可以用来启动定义在launch（启动）文件中的节点。

用法：

```shell
roslaunch [package] [filename.launch]
```

首先在软件包目录下创建一个launch文件夹，将launch文件放在launch文件夹下。（不放也行，标准）。文件创建完成后可以用上面的命令进行启动。

launch文件举例如下：

```xml
<launch>
  <!--创建两个分组，用ns（namespace）来区分两个分组中都有sim的turtlesim节点可以同时启动两个模拟器，防止名称冲突。-->
  <group ns="turtlesim1">
    <node pkg="turtlesim" name="sim" type="turtlesim_node"/>
  </group>
  <group ns="turtlesim2">
    <node pkg="turtlesim" name="sim" type="turtlesim_node"/>
  </group>
  <!--启动模仿节点-->
  <node pkg="turtlesim" name="mimic" type="mimic">
    <remap from="input" to="turtlesim1/turtle1"/>
    <remap from="output" to="turtlesim2/turtle1"/>
  </node>
</launch>
```

上面的launch文件启动的节点产生的计算图为：
![rqt_graph]({{site/url}}/assets/postimage/ros/roslaunch.png){: .align-center}

## 创建ros消息和服务

详细的ros消息和服务内容介绍还是看[官方文档](http://wiki.ros.org/cn/ROS/Tutorials/CreatingMsgAndSrv)吧。

### rosmsg 和 rossrv

除了下面这些还有很多例子，比如如何创建msg格式最好是去[官网](http://wiki.ros.org/cn/ROS/Tutorials/CreatingMsgAndSrv)上看看。

```shell
rosmsg show [message type] 显示msg格式
```

```shell
rossrv show [service type]
```
