---
title: "ROS主题"
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
tags: c++ ros 机器人 python ros主题  #调整文章的标签
categories: ros # 调整文章的分类
excerpt: "ros中的话题以及rostopic等命令工具"
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

# ros主题

## rqt_graph

rqt_graph用动态的图显示了系统中正在发生的事情。

```shell
rosrun rqt_graph rqt_graph
```

将会打开一个窗口：
![rqt_graph]({{site/url}}/assets/postimage/ros/rqt_graph_turtle_key.png){: .align-center}
在这个窗口里面，ros节点分别是蓝色和绿色的，话题是红色显示的。

## rostopic工具

常见的rostopic命令及作用。有很多不仅局限于下面这些。

```shell
查看帮助
rostopic -h
显示某个话题上发布数据
rostopic echo 
[topic]
列出当前已被订阅和发布的所有话题
rostopic list -v
查看帮助
rostopic list -h
```

## ros消息

查看一个主题上的消息类型。

```shell
rostopic type [topic]
```

将数据发布到某个正在广播的话题上。

```shell
rostopic pub [topic] [msg_type] --[args]
```

上面命令的参数实际上是使用的[YAML语法](http://wiki.ros.org/ROS/YAMLCommandLine)

报告数据发布的速率

```shell
rostopic hz [topic]
```

## rqt_plot

rqt_plot命令可以在滚动时间图上显示发布到某个话题上的数据。

```shell
rosrun rqt_plot rqt_plot
```

自行添加并绘制需要的数据即可。