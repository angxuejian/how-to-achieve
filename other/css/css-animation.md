# Css Animation 常用动画

## X Y Z 轴旋转动画
rotateX：定义沿着 X 轴的 3D 旋转。

rotateY：定义沿着 Y 轴的 3D 旋转。

rotateZ：定义沿着 Z 轴的 3D 旋转。

::: demo
```vue
<div class='demo__css-animation-1 demo-flex'>
  <div :class='className'></div>
  <button class='demo-btn' @click='switchShow'>{{ isShow ? '暂停': '播放' }}</button>
</div>

<script>
  export default {
    data() {
      return {
        isShow: true,
        className: ''
      }
    },
    methods: {
      switchShow: function() {
        this.isShow = !this.isShow
        let str = 'demo__css-animation-1--'
        this.className = str + (this.isShow ? 'play' : 'stop')
      }
    }
  }
</script>

<style>
  .demo__css-animation-1 > div {
    width: 100PX;
    height: 100PX;
    background-color: #ededed;
    animation: rotate1 3s linear infinite; /* 动画名称 时长 动画速度 动画播放次数 */
  }
  @keyframes rotate1 {
    from {
      /* transform: rotateX(0deg); */
      /* transform: rotateY(0deg); */

      transform: rotateZ(0deg);
    }
    to {
      /* transform: rotateX(360deg); */
      /* transform: rotateY(360deg); */

      transform: rotateZ(360deg);
    }
  }

  /* 暂停播放动画 */
  .demo__css-animation-1--stop {
    animation-play-state: paused !important; 
  }

  /* 继续播放动画 */
  .demo__css-animation-1--play {
    animation-play-state: running !important;
  }
</style>
```
:::


## 淡出/闪烁/弹起

::: demo
```vue
<div class='demo-flex'>
  <div :class='className'>淡入/淡出</div>
  <button @click='switchShow' class='demo-btn'>{{ isShow ? '淡出' : '淡入'}}</button>
</div>

<script>
  export default {
    data() {
      return {
        isShow: true,
        className: ''
      }
    },
    methods: {
      switchShow: function() {
        this.isShow = !this.isShow
        let str = 'demo__css-animation-2__'
        this.className = str + (this.isShow ? 'fead-in' : 'fead-out')
      }
    }
  }
</script>

<style>
.demo__css-animation-2__fead-in {
  animation: feadin 0.5s forwards; /* 动画名称 时长 保持最后一帧的状态*/
}

@keyframes feadin {
  from {
    opacity: 0;
  }
  to {
    opacity: 1;
  }
}

.demo__css-animation-2__fead-out {
  animation: feadout 0.5s forwards;
}

@keyframes feadout {
  from {
    opacity: 1;
  }
  to {
    opacity: 0;
  }
}
</style>
```
:::

::: demo
```vue
<div class='demo__css-animation-2__flash'></div>

<style>
.demo__css-animation-2__flash {
  width: 100PX;
  height: 100PX;
  background-color: #ededed;
  text-align: center;
  line-height: 100PX;
  border-radius: 50%;
  animation: flash 1s linear infinite;
}

@keyframes flash {
  0% {
    opacity: 0.3;
  }
  50% {
    opacity: 1;
  }
  100% {
    opacity: 0.3;
  }
}

</style>
```
:::


::: demo
```vue
<div class='demo-flex'>
  <div :class="['demo__css-animation-5', className]"></div>
  <button @click='switchShow' class='demo-btn'>{{ isShow ? '弹出' : '弹起'}}</button>
</div>

<script>
  export default {
    data() {
      return {
        isShow: true,
        className: ''
      }
    },
    methods: {
      switchShow: function() {
        this.isShow = !this.isShow
        let str = 'demo__css-animation-5__'
        this.className = str + (this.isShow ? 'barrage-in' : 'barrage-out')
      }
    }
  }
</script>

<style>
.demo__css-animation-5 {
  width: 200PX;
  height: 100PX;
  background-color: #ededed;
}

.demo__css-animation-5__barrage-in {
  animation: bar-scale-in 0.5s ease forwards;
  opacity: 0;
  transform-origin: bottom left;
  transform: scale(0.1);
}
@keyframes bar-scale-in {
  50% {
    opacity: 0.5;
    transform: scale(1.05);
  }
  100% {
    transform: scale(1);
    opacity: 1;
  }
}

.demo__css-animation-5__barrage-out {
  animation: bar-scale-out 0.5s ease forwards;
  opacity: 1;
  transform-origin: bottom left;
  transform: scale(1);
}
@keyframes bar-scale-out {
  0% {
    opacity: 0.8;
    transform: scale(0.8);
  }
  100% {
    transform: scale(0);
    opacity: 0.2;
  }
}

</style>
```
:::

## 上/下/左/右 滑动

translateX：为 左右方向、从左到右 0% - 100%

translateY：为 上下方向、从上到下 0% - 100%

::: demo
```vue
<div>
  <button style='margin-left: 0;' @click='switchShow' class='demo-btn'>{{ isShow ? '右滑' : '左滑'}}</button>
  <div :class='["demo__css-animation-3", className]'></div>
</div>

<script>
  export default {
    data() {
      return {
        isShow: true,
        className: ''
      }
    },
    methods: {
      switchShow: function() {
        this.isShow = !this.isShow
        let str = 'demo__css-animation-3__slide-'
        this.className = str + (this.isShow ? 'left' : 'right')
      }
    }
  }
</script>

<style>
.demo__css-animation-3 {
  width: 100PX;
  height: 100PX;
  background-color: #ededed;
  margin-top: 20PX;
}

.demo__css-animation-3__slide-right {
  animation: slideright 1s forwards;
}
@keyframes slideright {
  from {
    transform: translateX(0);
  }
  to {
    transform: translateX(200%);
  }
}

.demo__css-animation-3__slide-left {
  animation: slideleft 1s forwards;
}
@keyframes slideleft {
  from {
    transform: translateX(200%);
  }
  to {
    transform: translateX(0%);
  }
}
</style>
```
:::


## 进入/退出 缩放

::: demo
```vue
<div class='demo-flex'>
  <div :class='["demo__css-animation-4", className]'></div>
  <button @click='switchShow' class='demo-btn'>{{ isShow ? '退出' : '进入'}}</button>
</div>

<script>
  export default {
    data() {
      return {
        isShow: true,
        className: ''
      }
    },
    methods: {
      switchShow: function() {
        this.isShow = !this.isShow
        let str = 'demo__css-animation-4__'
        this.className = str + (this.isShow ? 'zoom-in' : 'zoom-out')
      }
    }
  }
</script>

<style>
.demo__css-animation-4 {
  width: 100PX;
  height: 100PX;
  border-radius: 50%;
  background-color: #ededed;
}

.demo__css-animation-4__zoom-in {
  animation: zoomin 1s forwards;
}
@keyframes zoomin {
  from {
    transform: scale(0.1);
    opacity: 0;
  }
  to {
    transform: scale(1);
    opacity: 1;
  }
}

.demo__css-animation-4__zoom-out {
  animation: zoomout 1s forwards;
}
@keyframes zoomout {
  from {
    transform: scale(1);
    opacity: 1;
  }
  to {
    transform: scale(0.1);
    opacity: 0;
  }
}
</style>
```
:::

