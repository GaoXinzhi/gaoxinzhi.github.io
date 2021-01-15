---
title: "ROS软件包"
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
excerpt: "创建新的ros包并列出依赖关系"
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

# ros软件包

## catkin软件包

成为一个catkin软件包要有几个要求:

* 要有一个符合catkin规范的package.xml文件。提供有关软件包的元信息。
* 必须有一个 catkin 版本的  CMakeLists.txt 文件
* 必须有自己的目录。软件包不能嵌套。

```shell
最简单的软件包目录
my_package/
  CmakeLists.txt
  package.xml
```

具体如何创建catkin工作空间可以参见[ros文件系统]]({{ site.url }}/ros/ROS-file-system)。 创建完的catkin工作空间里面可以用来创建ros包。

## 创建catkin软件包

使用catkin_create_pkg创建新的catkin软件包。
首先切换到刚才创建的空白catkin工作空间中的源文件空间目录。

```shell
这是catkin工作空间的基本目录结构：
workspace_folder/        -- WORKSPACE
  src/                   -- SOURCE SPACE
    CMakeLists.txt       -- 'Toplevel' CMake file, provided by catkin
    package_1/
      CMakeLists.txt     -- CMakeLists.txt file for package_1
      package.xml        -- Package manifest for package_1
    ...
    package_n/
      CMakeLists.txt     -- CMakeLists.txt file for package_n
      package.xml        -- Package manifest for package_n
```

```shell
cd ~/catkin_ws/src
```
 
 使用catkin_create_pkg创建一个名为beginnner_tutorials的新软件包，这个软件包依赖于std_msg、roscpp和rospy:

 ```shell
 基本用法:
 catkin_create_pkg <package_name> [depend1] [depend2] [depend3]
 示例：
catkin_create_pkg beginner_tutorials std_msgs rospy roscpp
```

上述命令的高级用法见[catkin/commands/catkin_create_pkg](http://wiki.ros.org/catkin/commands/catkin_create_pkg)

## 软件包的依赖关系

### 一级依赖和间接依赖

软件包之间存在依赖关系，可以使用rospack查看依赖关系

```shell
rospack depends beginner_tutorials
除了上面的rospack depends之外还有很多depend命令可以查阅官方文档
```

rospack列出的关系都存储在package.xml文件中。

自定义软件包详细见[官方文档](http://wiki.ros.org/cn/ROS/Tutorials/CreatingPackage)




