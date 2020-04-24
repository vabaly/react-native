# React Native 学习笔记

## 开发需要用到的东西

### iOS

都是通过 `brew` 安装

- watchman，不知道为什么不是个 NPM 包，也不知道为什么用这个，**也许是二进制文件工具性能比其他工具好很多，从而加快热更新速度**
- cocoapods，脚手架创建项目的时候，需要安装一些原生模块，项目本身要用到，所以需要这个东西。

### Android

- watchman
- JDK：`brew cask install adoptopenjdk/openjdk/adoptopenjdk8`

### 开发环境的搭建

直接看[官方文档](https://reactnative.cn/docs/getting-started)，不过有以下几点官方文档没有提到：

- 安卓开发工具要安装 Google Play 的条款

    > Go to Configure > SDK Manager in your Android Studio. Select SDK Tools tab and install Google Play Licensing Library

### Expo

**下面是我对 Expo 的理解，可能基于知识的限制，还不是很正确：**

Expo App 是一个编译好的  App，支持监听通过无线网络传给 App 的指令，这个指令是 Expo 的开发工具或套件发出来的，指令的作用是告诉 Expo 调用原生硬件，而这个能力本身就编译进 Expo App 中了，所以支持。**本质上还是 React Native 打包的 App 支持这些能力。**

## JavaScriptCore

## 需要注意的与 Web 开发的区别

- Web 的基础组件是 `div` 等这种原生标签，并且不需要引入，RN 是它提供的基础组件，需要引入
- CSS 样式改成 JS 对象的写法，并且需要用 StyleSheet.create 方法去创建样式对象，同时只能通过 `style` 属性传入
- 尺寸都是没有单位的，**这个计算可能还得深入研究一下**
- 布局只有 Flex 布局，不支持 `display`，`flex-direction` 默认是 `column`，[所有组件都支持的 CSS 属性只有这些](https://reactnative.cn/docs/layout-props)，其他各组件可能有自己支持的样式属性
- React Native 有个类似于 `html` 标签的元素，它占满整个屏幕，但是是个 `flex` 盒子，且遵循 `flex-direction` 默认值为 `column` 的设定，以及和 Web 一样 `align-items` 默认值是 `stretch`，所以显得它的子元素宽度为 100%，当然，这个根元素不可操作

## 需要注意的事项

- 组件可能有部分属性只在特定平台生效
- 页面跳转需要用 React Navigation 或其他库
- require 图片时，路径必须是常量字符串，因为是编译时执行
- 非图片资源，比如视频必须写明尺寸，不能用 flex 属性
- 引用网络图片、base 64 图片时要指明图片大小，因为 React Native 从设计上想避免图片抖动
- 背景图无法使用 `backgroundImage`，需要用 `ImageBackground` 组件
- 不要在开发模式下去测试性能，不准确


## 技巧

- 不同平台的代码可以使用文件后缀名来区分
- 给图片名字加上 @2x、@3x 结尾的另外两张图片，App 在运行时会根据屏幕分辨率自动选一张，代码引用的时候无需写 @nx
- TouchWithoutFeedback 组件的 hitSlop 属性可以扩大点击范围而不影响布局
- InteractionManager 接口可以将代码放到交互结束后执行，从而不阻塞交互

## 常用 API

- 

## 复杂的原生组件

这些组件可能需要经常看看：

- Image 组件：https://reactnative.cn/docs/images

    `source` 属性接收对象，如果是用 `require`，那么编译时 `require` 也会被转成对象

- Animated 组件：https://reactnative.cn/docs/animations

## 调试时的注意事项

- 新增资源或者改原生代码都不会热更新哦，需要手动重启

## 性能问题

[一些可能的情况可以看官网上的说明](https://reactnative.cn/docs/performance)

- 性能问题的本质就是某一个过程占用过多帧的时间，阻塞了下一个过程的进行，对于前端来说，经常是 JavaScript 线程耗时太多了

## 可能比较少用到的功能

- 无障碍功能相关的组件属性和 API：https://reactnative.cn/docs/accessibility#双指双击事件-onmagictap-ios





