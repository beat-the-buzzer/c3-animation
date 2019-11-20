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