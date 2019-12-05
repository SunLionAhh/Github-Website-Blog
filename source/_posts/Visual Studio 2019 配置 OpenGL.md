---
title: Visual Studio 2019 配置 OpenGL
top: false
cover: false
toc: true
mathjax: false
date: 2019-11-07 21:50:28
author: qin nian
img:
coverImg:
password: 
summary: VS2019，跟我左边画一条龙
tags: 
- OpenGL
categories: Computer Graphics
---

## 1. 下载VS2019

去[官网](https://visualstudio.microsoft.com/zh-hans/downloads/)，选择 `VS 2019` 社区版进行下载。

![选择Community](https://pic.superbed.cn/item/5dc2d2298e0e2e3ee93f3d7b.jpg)

## 2. 下载 GLEW

去[官网](http://glew.sourceforge.net/)，下载 Binaries Windows 32-bit and 64-bit。

![下载 GLEW](https://pic.superbed.cn/item/5dc2d3e58e0e2e3ee93f91c2.jpg)

## 3. 下载GLFW

去[官网](http://www.glfw.org/download.html)，下载 `Windows pre-compiled binaries 32-bit`（64 位会出现莫名其妙的问题）

![下载GLFW](https://pic.superbed.cn/item/5dc2d49d8e0e2e3ee93fafd4.jpg)

## 4. 配置 OpenGL

### 4.1 新建 C++ 空项目

打开 vs2019，`文件 —> 新建 -> 项目 -> 空项目` ，命名为 `OpenGLExercise01`

![新建 C++ 空项目](https://ae01.alicdn.com/kf/H2e49b6b7207e4cb9be68e99a24cbe4adB.jpg)

### 4.2 创建 main. cpp 源文件

右侧 `解决方案资源管理器` 下，`源文件 —> 添加 —> 新建项` ，创建名为 `main.cpp`源文件

### 4.3 开始配置 OpenGL

#### 4.3.1 添加 include 文件

- 右键项目 `OpenGLExercise` ，在弹出的选项中，单击 `属性`

- 点击 `C/C++ —> 常规 —> 附加包含目录 —> 编辑`

  ![找到编辑1](https://pic.superbed.cn/item/5dc2de7e8e0e2e3ee940ffe3.jpg)

- 点击添加头文件。分别添加下载的 `glew` 和 `glfw` 文件夹下的 `include` 文件夹 (include 文件夹下是我们需要的头文件)，点击 `确定`

   ![添加include文件](https://pic.superbed.cn/item/5dc2dfe58e0e2e3ee9411d2f.jpg)

#### 4.3.2 添加 lib 文件

- 点击 `链接器 —> 常规 —> 附加包含目录 —> 编辑`

    ![找到编辑2](https://pic.superbed.cn/item/5dc2e2458e0e2e3ee9417479.jpg)

- 分别添加下载的 `glew` 和 `glfw` 文件夹下的 `lib` 文件夹。

  - 当添加 `glew` 时，当选到 `lib` 文件夹后请继续选择，`lib -> Release -> Win32` , 请选择 `Win32` 后点击 “选择文件夹”（x64 会有莫名其妙的问题）

  - 当添加 `glfw` 时，请选择对应版本，2019 版本请选择 `lib-vc2019`

  ![添加lib文件](https://ae01.alicdn.com/kf/Hb0fe1313ad4943b797cbdd59b5781188m.jpg)

#### 4.3.3 添加库依赖项

- 点击 `链接器 —> 输入 —> 附加依赖项 —> 编辑`

  ![找到编辑3](https://puui.qpic.cn/fans_admin/0/3_1192510060_1573053768870/0)

- 输入如下:

    opengl32.lib

    glfw3.lib

    glew32s.lib

  ![添加输入](https://ae01.alicdn.com/kf/H776c29d1cce246318c26973b322882f6b.jpg)

- 最后确定

## 5. 程序调试

### 5.1 初步运行

在之前的 main.cpp 中添加如下代码：（即初始化一个 OpenGL 窗口）

    #include<iostream>
    #define GLEW_STATIC
    #include <GL/glew.h>
    #include<GLFW\glfw3.h>

    using namespace std;

    int main(int argc, char** argv[])
    {
    /*glewExperimental = GL_TRUE;
    if (glewInit()!=GLEW_OK)
      {
      cout << "failed to initalize GLEW" << endl;
      return -1;
      }*/

      glfwInit();//初始化
      glfwWindowHint(GLFW_CONTEXT_VERSION_MAJOR, 3);//配置GLFW
      glfwWindowHint(GLFW_CONTEXT_VERSION_MINOR, 3);//配置GLFW
      glfwWindowHint(GLFW_OPENGL_PROFILE, GLFW_OPENGL_CORE_PROFILE);//
      glfwWindowHint(GLFW_RESIZABLE, GL_FALSE);

      GLFWwindow* window = glfwCreateWindow(800, 600, "LearnOpenGL", nullptr, nullptr);
      if (window==nullptr)
      {
        cout << "Failed to create GLFW window" << endl;
        glfwTerminate();
        return -1;
      }
      glfwMakeContextCurrent(window);
      while (!glfwWindowShouldClose(window))
      {
        glfwPollEvents();
        glfwSwapBuffers(window);
      }
      glfwTerminate();
      return 0;


    }

![窗口显示](https://ae01.alicdn.com/kf/H524182b59ab441b1bd3031fa4738d9c5u.jpg)

### 5.2 解决库冲突

当我们关掉程序回到 “错误列表” 中会发现

![出现问题](https://ae01.alicdn.com/kf/H5ff3c8a718bf4ba3bf4421889ba4c59d0.jpg)

点击属性，找到“编辑”

![解决库冲突](https://puui.qpic.cn/fans_admin/0/3_1409075683_1573191343465/0)

输入如下：

``` bash
MSVCRT.lib
LIBCMT.lib
```

最后，点击一下右下角的应用，再点击确定。

![完善](https://puui.qpic.cn/fans_admin/0/3_15881579_1573191547079/0)

注：如果往后还有库冲突，解决方法同理。

### 5.3 解决引言中的链接错误

出现警告：`glew32s.lib(glew.obj) : warning LNK4099: 未找到 PDB“vc120.pdb”(使用“glew32s.lib(glew.obj)”或在“F:\QinNian'GitHub\Computer_Graphics\OpenGL_Learn\01_入门\01_OpenGL 环境配置\OpenGLExercise01\Debug\vc120.pdb”中寻找)；正在链接对象，如同没有调试信息一样`

如果确认不需要`PDB`, 即不需要调试开源库, 完全可以在设置里将`/Zi`或`/ZI`去掉, 这样即能消除`warning`也能提升开源库编译速度

将 `glew` 工程配置成不生成调试信息，或把调试信息直接生成到`.obj`文件中（而非`.pdb`文件）即可.

`项目属性 --> 配置属性 --> C/C++ --> 常规 --> 调试信息格式`

>空表示不生成调试信息，
>
>`C7`把调试信息直接生成到`.obj`文件中
>
>默认的`Zi`生成`.pdb`文件

![调试信息格式](https://ae01.alicdn.com/kf/H544488a404b3411c998ef5bdf8cc3462N.jpg)

## 6. 写在最后

我哭了，终于弄好了！！！

![成功](https://ae01.alicdn.com/kf/H544488a404b3411c998ef5bdf8cc3462N.jpg)
