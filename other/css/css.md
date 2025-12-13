# Css 常用样式


## 单行文本超出显示省略号
:::demo
```vue
<div class='demo__css-1 demo-flex'>
  <div :class='{ "demo__css-1__div--show" : isShow }'>
    卡耐基曾经说过，我们若已接受最坏的，就再没有什么损失。这不禁令我深思要想清楚
  </div>
  <button class='demo-btn' @click='switchShow'>{{ isShow ? '显示' : '隐藏' }}</button>
</div>

<script>
  export default {
    data() {
      return {
        isShow: true
      }
    },
    methods: {
      switchShow: function() {
        this.isShow = !this.isShow
      }
    }
  }
</script>

<style lang='scss'>
.demo__css-1 > div {
  width: 150px;
  border: 1px solid #333;
  box-sizing: border-box;
  padding: 3PX;
}
.demo__css-1__div--show {
  text-overflow: ellipsis;
  white-space: nowrap;
  overflow: hidden;
}
</style>
```
:::

## 多行文本超出显示省略号

:::demo 只支持 webkit 内核的浏览器
```vue
<div class='demo__css-2 demo-flex'>
  <div :class='{ "demo__css-2__div--show" : isShow }'>
    卡耐基曾经说过，我们若已接受最坏的，就再没有什么损失。这不禁令我深思要想清楚
  </div>
  <button class='demo-btn' @click='switchShow'>{{ isShow ? '显示' : '隐藏' }}</button>
</div>

<script>
  export default {
    data() {
      return {
        isShow: true
      }
    },
    methods: {
      switchShow: function() {
        this.isShow = !this.isShow
      }
    }
  }
</script>

<style lang='scss'>
.demo__css-2 > div {
  width: 150px;
  border: 1px solid #333;
  box-sizing: border-box;
  padding: 3PX;
}
.demo__css-2__div--show {
  display: -webkit-box;
  -webkit-box-orient: vertical;
  -webkit-line-clamp: 2; /* 超出2行显示省略号，调整数值即可 */
  overflow: hidden;
  word-break: break-all;
}
</style>
```
:::

## 对号✔️
将div设置为长方形、只显示 右边框 + 下边框、旋转45度即可。
::: demo
```html
<div class='demo__css-3'></div>

<style>
.demo__css-3 {
  width: 8px;
  height: 18px;
  border-width: 0 4px 4px 0;
  border-style: solid;
  border-color: #16C60C;
  transform: rotate(45deg);
}
</style>
```
:::


## 圆弧
将圆看成正方形。分别裁剪一左一右的长方形、旋转左边长方形 指定角度即可

将 400*400的正方形 裁剪为 200*200的长方形。实际宽高还是400*400，只是显示200*200的宽高。

主要是利用这点来实现的！可能说的比较模糊...  快去动手试一试、一试便知！
:::demo
```html
<div class='demo__css-4'>
  <div class="demo__css-4__arc"></div>
  <div class="demo__css-4__circle"></div>
</div>

<style>
.demo__css-4__circle {
  width: 200px;
  height: 200px;
  border: 3px solid #ededed;
  background-color: #ededed;
  border-radius: 50%;
  box-sizing: border-box;
}

.demo__css-4__arc {
  width: 200px;
  height: 200px;
  position: absolute;
  clip: rect(0 200px 200px 100px);
  animation: myarc 3s linear infinite;
}
.demo__css-4__arc::after {
  content: '';
  width: 100%;
  height: 100%;
  position: absolute;
  clip: rect(0 100px 200px 0);
  background-color: #16C60C;
  transform: rotate(90deg); /* 控制显示度数区域 */
  border-radius: 50%;
  box-sizing: border-box;
  border: 3px solid #16C60C;
}
@keyframes myarc {
  from { transform: rotateZ(0);}
  to   { transform: rotateZ(360deg);}
}
</style>
```
:::



## 隐藏滚动条

:::demo 只兼容PC端浏览器和个别移动端浏览器，微信浏览器不兼容
```vue
<div class="demo__css-5__outer">
  <div class="demo__css-5__inner">
    <div class="demo__css-5__content">
      <div class="demo__css-5__page">
        人性到底是什么样的？五个小时前接到一个电话，再次把我带入了痛苦的记忆……
那一段段悲伤往事犹如滔滔洪水连绵不绝，压的喘不过气来，迫使我不得不跪下来祈求上苍:怜悯我及父亲，让我不再遭受挫折和磨难；让正义感恩之剑插在父亲面前，不要再让他像疯狗那般到处与人争执、到处告状闹事。
多少年来，一直很同情弱者，总觉得一些弱势群体很可怜可悲，可一了解这些所谓的弱势群体才发现，一些人干尽坏事、丧尽天良，现在自己的立场考虑问题，为了蝇头小利到处闹访、缠访、告状，完全不顾及子女的工作、生活，也不考虑子女是否会受到牵连。这样的弱者，我想问你:这般自私自利、倔强、贪婪，家人和社会如何挽救你？如何同情你可怜你？你的所作所为使子女后半生活在自卑、痛苦当中，你可否考虑过子女的感受？你霸占农村家庭成员的房产、地产、财物，家人顾忌面子争不过你，让你占有，长年甚至是几十年的占有还是换不来你的良知，你视家人的谦让理所当然，不但不感恩反而觉得本来就是自己的，你这样对家人也就罢了，可你的猖狂之心却不停作祟，鼓动你近两年不停闹访、缠访、告状。家人劝不住你，你觉得自己很牛X，奈何你不得，可你想过没有:你无休止的闹腾不断地透支子女的自尊心和在单位中的形象？呜呼，何等悲哀，你自己胡作非为你意识不到对子女的负面影响吗？难道非要让政府制裁把你送进监狱才能悔改吗？六十多岁的人了，每年地承包出去领取一万至四万不等的租金，生活无忧无虑，还不知足，我的理解是好日子可能快过到头了。
      </div>
    </div>
  </div>
</div>

<style>
.demo__css-5__outer {
  width: 300PX;
  height: 300PX;
  position: relative;
  overflow: hidden;
  border: 1px solid #333;
}
.demo__css-5__inner {
  position: absolute;
  left: 0;
  overflow-x: hidden;
  overflow-y: scroll;
}
.demo__css-5__content {
  width: 300PX;
  height: 300PX;
}
.demo__css-5__page {
  padding: 5PX;
  text-align: justify;

}
</style>

```
:::demo