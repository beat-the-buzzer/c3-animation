#### Transition基础

1、属性名称（property）

2、过渡时间（duration）和延迟时间（delay）

3、时间函数（timing-function）

```css
.box {
  width: 100px;
  height: 100px;
  background: #000;
}
.demo-1 {
  /* 属性名 过渡时间 时间函数 延时*/
  /* 时间函数 linear ease */
  /* 鼠标放在元素上延时两秒后，宽度匀速从100px增长到500px */
  transition: width 2s linear 2s;
}
.demo-1:hover {
  width: 500px;
}
```

上面的例子中，矩形宽度平缓增长，看起来有一点卡顿，我们可以去修改时间函数。实际上，linear和easa都是`贝塞尔曲线（cubic-bezier）`的特殊情况，我们可以在控制台上去调试运动的曲线，从而达到我们想要的运动，如下图所示：

我们可以点击控制台上的时间函数：

![https://gitee.com/beat-the-buzzer/pictures/raw/master/c3-animation/c3-animation-02.png](https://gitee.com/beat-the-buzzer/pictures/raw/master/c3-animation/c3-animation-02.png)

我们可以调整运动曲线，得到bezier属性值：

![https://gitee.com/beat-the-buzzer/pictures/raw/master/c3-animation/c3-animation-03.png](https://gitee.com/beat-the-buzzer/pictures/raw/master/c3-animation/c3-animation-03.png)

注意事项

1、display: none;不能和transition一起使用

transition需要读取元素的初始属性值，display为none的情况下，很多属性都读不到

2、transition后面尽量不要跟all

transition需要去检查元素属性的变化，如果使用all，就会把所有的属性都去检查一遍，造成大量资源的浪费

3、解决闪动问题，使用3D属性

perspective、backface-visibility、translate3d(0,0,0)

