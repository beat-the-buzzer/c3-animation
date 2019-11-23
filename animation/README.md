#### Animation基础

1、动画名称（name）--@keyframes

2、过渡时间（duration）和延迟时间（delay）

3、时间函数（timing-function）

```css
.box {
  width: 100px;
  height: 100px;
  background: #000;
}
.demo-1 .cell {
  width: 200px;
  height: 200px;
  background: red;
}

.demo-1:hover .cell{
  animation: move 2s linear;
}

@keyframes move{
  100% {
    transform: translateX(200px);
  }
}
```

4、播放次数（iteration-count）

5、播放方向（direction），是否轮流播放和反向播放

6、停止播放的状态（fill-mode），是否暂停（play-state）

注意事项：

1、解决了transition和display:none的冲突问题

2、实现跳动的元素

下面是一个Demo，实现物体的自由落体运动。

自由落体运动的关键在于时间函数，选择合适的时间函数会让物体运动得更加逼真。

首先，我观察了一下系统自带的时间函数：

linear：动画从头到尾的速度是相同的

![https://gitee.com/beat-the-buzzer/pictures/raw/master/c3-animation/c3-animation-04.png](https://gitee.com/beat-the-buzzer/pictures/raw/master/c3-animation/c3-animation-04.png)

ease：默认。动画以低速开始，然后加快，在结束前变慢

![https://gitee.com/beat-the-buzzer/pictures/raw/master/c3-animation/c3-animation-05.png](https://gitee.com/beat-the-buzzer/pictures/raw/master/c3-animation/c3-animation-05.png)

ease-in: 动画以低速开始

![https://gitee.com/beat-the-buzzer/pictures/raw/master/c3-animation/c3-animation-06.png](https://gitee.com/beat-the-buzzer/pictures/raw/master/c3-animation/c3-animation-06.png)

ease-out: 动画以低速结束

![https://gitee.com/beat-the-buzzer/pictures/raw/master/c3-animation/c3-animation-07.png](https://gitee.com/beat-the-buzzer/pictures/raw/master/c3-animation/c3-animation-07.png)

ease-in-out: 动画以低速开始和结束

![https://gitee.com/beat-the-buzzer/pictures/raw/master/c3-animation/c3-animation-08.png](https://gitee.com/beat-the-buzzer/pictures/raw/master/c3-animation/c3-animation-08.png)

观察这些轨迹，我发现，贝塞尔曲线最终就是物体的位移轨迹，我们可以通过修改控制点的方式来修改位移。

显然，自由落体运动是初速度为0，加速度为g的匀加速直线运动，所以最终的位移曲线应该是一个定点在原点，开口向上的抛物线。

大致在浏览器上画了一个差不多的曲线，值得注意的是，由于自由落体的初速度为0，初始位置的切线必然和x轴平行，得到了贝塞尔曲线的函数方程：

![https://gitee.com/beat-the-buzzer/pictures/raw/master/c3-animation/c3-animation-09.png](https://gitee.com/beat-the-buzzer/pictures/raw/master/c3-animation/c3-animation-09.png)

最终运行效果：

[https://beat-the-buzzer.github.io/c3-animation/](https://beat-the-buzzer.github.io/c3-animation/)

