# a native-js slider
# 一个无缝轮播图的小轮子 ( ͡° ͜ʖ ͡°)•ॢ

## 前言
自己弄这个轮子是来自之前vue做一个音乐播放器项目时，用到了一个第三方vue组件better-scroll，当时参考这个文档做轮播图的时候，发现slider-item真实渲染出来的多了两个节点，向作者提问了下，回答当传入 snap:{loop:true} 的时候，前后各 clone 一个节点，保证可以无缝循环轮播，那么多克隆这两个节点是怎么实现无无缝轮播图呢，查阅了相关原理，就做了下这个轮子。


## demo:
![demo](https://github.com/ZhangMingZhao1/a-native-js-slider/blob/master/demoGIF.gif)


## 原理：
1. 所谓的无缝就是利用了两个辅助节点，eg：

5 1 2 3 4 5 1

其中首尾5,1就是辅助节点，为了实现过渡，当真实的5节点滑动到下一节点1时，其实是滑到了辅助1节点，此时再瞬间将位置指向真正的1节点，因为是相同的节点，此时外界就看不到发生的变化。

2. 利用了float和overflow，外界container设置成一张图片的大小，设置voerflow超出部分为hidden，第一个节点辅助节点5的left为0px，下一个就是真实的节点1为-600px(假设图片宽600px)，后面依次推。通过控制容器的left值来实现轮播。(向右偏移left值越来越小)

## 功能
1. 无缝轮播
2. 自动播放，鼠标hover状态时停止自动播放，且浮现左右控制箭头，移开则消失。
3. 焦点dot的状态随图片轮播亮起和熄灭。且可以点击dot来自由切换跳转到相应的图片。
4. 轮播间隔时间和图片切换时间在代码里直接改相关时间常量即可。

## 在线demo
[链接](https://zhangmingzhao1.github.io/a-native-js-slider/index.html)

## 有时间可以再用CSS3实现一遍
