### 3D Magic Cube 

#### 1. 3D Magic Cube

1. 创建项目

- 创建项目目录： 3d_magic_cube-master

- 创建css、imgs目录

- 创建index.html和index.css

2. HTML代码

- 创建.box,

  ```html
  <div class="box"></div>
  ```
- 为魔方创建六面

  ```html
  <ul class="front"></ul>
  <ul class="back"></ul>
  <ul class="left"></ul>
  <ul class="right"></ul>
  <ul class="top"></ul>
  <ul class="bottom"></ul>
  ```

- 为每个面创建9个按键

  ```html
  <li>1</li>
  <li>2</li>
  <li>3</li>
  <li>4</li>
  <li>5</li>
  <li>6</li>
  <li>7</li>
  <li>8</li>
  <li>9</li>
  ```

3. CSS代码

- 将魔方居中: 采用Flex弹性布局

  1)元素body声明Flex布局

    ```css
    body {display: flex;}
    ```
  2)Flex布局规定了主轴方向，默认为水平轴，设置主轴居中

    ```css
    body {justify-content: center}
    ```
  3)设置交叉轴居中

    ```css
    body {align-items: center}
    ```
  4)body默认宽度(width: 100%)，为body高度设置为100vh,即100%;

    ```css
    body {min-height: 100vh}
    ```
- .box元素样式设置

  1)transform-style 属性规定如何在 3D 空间中呈现被嵌套的元素：

  |attribute|description|
  |flat|子元素将不保留其 3D 位置|
  |preserve-3d|	子元素将保留其 3D 位置|

  ```css
  .box {transform-style: preserve-3d;}
  ```

- ul设置魔方六个面

  1)取消ul序号

    ```css
    ul {list-style: none;}
    ```

  2)设置每个面的宽高

    ```css
    ul {
      	width: 210px;
	      height: 210px;
    }
    ```

  3)为ul设置内边距

    ```css
    ul {padding: 5px;}
    ```
  4)为了设置六个面，需要将ul脱离文档流，此处采用了绝对定位，为了实现绝对定位，需要将父元素设置为相对定位

  ```css
  .box {position: relative}
  ul {position: absolute}
  ```
  5)ul六面的选取方法

    - 采用类选择器

    ```css
    .front {}
    ```
    - 采用伪类选择器

    ```css
    ul:nth-child(1){}
    或者
    ul:nth-of-type(1){}
    ```

  6)transform变换

    - 详见[[]]()
  
  7)背景透明设置

  ```css
  ul {background: transparent;}
  ```
  
  8)设置魔方的六个面

    - 正面设置

    ```css
    .front {
      transform: translateZ(120px);
    }
    ```
    或者
    ```css
    ul:nth-child(1) {
      transform: translateZ(120px);
    }
    ```

    - 背面设置

    ```css
    .back {
      transform: translateZ(120px);
    }
    ```
    或者
    ```css
    ul:nth-child(2) {
      transform: translateZ(-120px);
    }
    ```

    - 左面设置

    ```css
    .left {
      transform: rotateY(-90deg) translateZ(120px);
    }
    ```
    或者
    ```css
    ul:nth-child(3) {
      transform: rotateY(-90deg) translateZ(120px);
    }
    ```

    - 右面设置

    ```css
    .right {
      transform: rotateY(90deg) translateZ(120px);
    }
    ```
    或者
    ```css
    ul:nth-child(4) {
      transform: rotateY(90deg) translateZ(120px);
    }
    ```

    - 顶面设置

   ```css
    .top {
      transform: rotateX(90deg) translateZ(120px);
    }
    ```
    或者
    ```css
    ul:nth-child(5) {
      transform: rotateX(90deg) translateZ(120px);
    }
    ```

    - 底面设置

    ```css
    .bottom {
      transform: rotateX(-90deg) translateZ(120px);
    }
    ```
    或者
    ```css
    ul:nth-child(6) {
      transform: rotateX(-90deg) translateZ(120px);
    }
    ```
- li设置每一个单面

  1)设置按键颜色

    ```css
    .front li {
      background: red;
    }

    .back li {
      background: green;
    }

    .left li {
      background: blue;
    }

    .right li {
      background: purple;
    }

    .top li {
      background: yellow;
    }

    .bottom li {
      background: darkcyan;
    }
    ```
  2)li通用样式

    ```css
    li {
      /* 宽度 */
      width: 60px;
      /* 高度 */
      height: 60px;
      /* 字体颜色 */
      color: white;
      /* 字体大小 */
      font-size: 28px;
      /* 左浮动 */
      float: left;
      /* 外边距 */
      margin: 5px;
      /* 设置圆角 */
      border-radius: 20px;
      /* 文字水平居中 */
      text-align: center;
      /* 文字垂直居中 */
      line-height: 60px;
    }
    ```
- 定义动画

  ```css
  /* 定义动画 */
  @keyframes rotate {
    0% {
      transform: rotateY(0deg) rotateX(0deg) rotateZ(0deg);
    }

    20% {
      transform: rotateY(30deg) rotateX(40deg) rotateZ(20deg);
    }

    40% {
      transform: rotateY(-60deg) rotateX(-40deg) rotateZ(-20deg);
    }

    60% {
      transform: rotateY(145deg) rotateX(80deg) rotateZ(10deg);
    }

    80% {
      transform: rotateY(90deg) rotateX(60deg) rotateZ(-20deg);
    }

    100% {
      transform: rotateY(135deg) rotateX(-45deg) rotateZ(30deg);
    }
  }
  ```

- 调用动画： box调用

  ```css
  .box {
    animation: rotate 10s linear infinite alternate;
  }
  ```
- 为box设置透视

  ```css
  body {perspective: 10000px;}
  ```

4. 尺寸计算

- li

  1) width/height = 60px
  2) margin: 5px
  3) 单行计算： 3 x 60px + (2 x 5px) x 3 = 210px

- ul 

  1) width/height = 210px
  2)为了使边沿舒展，padding: 5px;

#### 2. 3D Magic Cube for Vue

1. HTML

- Vue实例对象

  1) Vue引入

    ```html
		<script src="js/vue.js"></script>
    ```

  2) 创建Vue实例对象

    ```html
    <script>
      const app = new Vue({
        el: "#app",
        data: {
          list: ["front","back","left","right","top","bottom"]
        }
      })
    </script>
    ```
  3) v-for循环

  - ul 

    ```html
		<ul v-for="item in list" :class="item"></ul>
    ```

  - li

    ```html
    <li v-for="item in 9" >{{item}}</li>
    ```

#### 3. 源码

[[3d_animation]](https://github.com/web-oyster/3d_animation)

#### 4.参考文档

[[六、其他 CSS 属性和特性]](https://web-oyster.github.io/2020/10/28/CSS/Tutorial/%E5%85%AD%E3%80%81%E5%85%B6%E4%BB%96%20CSS%20%E5%B1%9E%E6%80%A7%E5%92%8C%E7%89%B9%E6%80%A7/)

[[十二、Transform 变换]](https://web-oyster.github.io/2020/10/28/CSS/Tutorial/%E5%8D%81%E4%BA%8C%E3%80%81%E5%8F%98%E6%8D%A2/)

#### 5. 联系方式

[[Email]](yuanmin8888@outlook.com)

