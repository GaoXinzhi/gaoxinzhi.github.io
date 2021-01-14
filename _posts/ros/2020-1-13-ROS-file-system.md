---
title: "ROS文件系统"
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
tags: c++ ros 机器人 python # 调整文章的标签
categories: ros # 调整文章的分类
excerpt: "ros文件系统中的一些概念和命令行工具"
# classes: wide # 如果没有右面的导航栏的话将内容进行右填充如果有右侧导航栏会很难看

# 开始的大图片以及上面的文字

header:
  teaser: ../postimage/ros/ros.jpeg #预览时显示的图片
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

# ros文件系统

## ros工作空间的构建

构建代码如下：其中catkin_ws是要构建的包的名称。这个目录也就成了一个新的ros包目录。

```shell
mkdir -p ~/catkin_ws/src
cd ~/catkin_ws/
catkin_make
```

创建完该包目录之后，在路径下应该会出现一个devel文件夹，**随便source一个setup.bash将当前工作空间设置在环境的最顶层。**

```shell
source devel/setup.bash
```

执行完之后需要确保ros的包环境变量ROS_PACKAGE_PATH包含该路径。

```shell
echo $ROS_PACKAGE_PATH
/home/用户名称/catkin_ws/src:/opt/ros/版本名称/share
```

## ros文件工具

ros提供的专用命令行工具

### rospack

用法:这条命令可以输出查找到特定包的路径，除了find之外其实还有很多命令可以自行尝试。

```shell
rospack [find] [package_name]
```

### roscd

用法：这条命令可以切换到ros的特定包的目录下。但是这条命令只能切换到那些路径已经包含到ROS_PACKAGE_PATH环境变量中的软件。

``` shell
roscd [location/package_name]
```

下面的命令可以查看ros日志文件目录。

```shell
roscd log
```

### rosls

用法：可以直接按软件包名执行ls命令。

```shell
rosls [locationname[/subdir]]
```



