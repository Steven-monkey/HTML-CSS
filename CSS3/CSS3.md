# 							CSS3

- #### 属性选择器（属性器权重是10）

  ```html
      <style>
          button {
              cursor: pointer
          }
        //属性选择器
          button[disabled] {
              color: indianred;
          }
        //属性选择器 type
      </style>
  </head>
  
  <body>
    <!--disabled是禁止点击按钮-->
      <button>点我</button>
      <button>点我</button>
      <button>点我</button>
      <button disabled>点我</button>
      <button disabled>点我</button>
  </body>
  ```

  ```css
  //属性选择器（type）
  input[type='search'] {
              background-color: red;
          }
  //属性选择器（span[type^="icon"]）以icon开头
  //属性选择器（span[type$="icon"]）以icon结尾
  //属性选择器（span[type*="icon"]）含有icon就行
  
  <span class="icon1"></span>
  <span class="icon2"></span>
  <span class="icon3"></span>
  ```

- #### 结构伪类选择器

  ```css
  /*第一个li*/
  ul li:first-child {
    background-color: #888888;
  }
  /*最后一个li*/
  ul li:last-child {
    background-color: #78788;
  }
  /*第N个li*/
  ul li:nth-child(n) {
    background-color: #888888;
  }
  /*ul中偶数行li*/
  ul li:nth-child(even) {
    background-color: #888888;
  }
  /*ul中奇数行li*/
  ul li:nth-child(odd) {
    background-color: #888888;
  }
  /*n可以是任意数字，需要第几行开始，就让n等于当前行*/
  /*ul中偶数行li n是从0开始计算*/
  ul li:nth-child(2n) {
    background-color: #888888;
  }
  /*ul中奇数行li n是从0开始计算*/
  ul li:nth-child(2n+1) {
    background-color: #888888;
  }
  /*ul中从第5行之后的li*/
  ul li:nth-child(n+5) {
    background-color: #888888;
  }
  /*ul中从第5行之前的li*/
  ul li:nth-child(-n+5) {
    background-color: #888888;
  }
  /*选择指定类型的元素 第一个span元素*/
  div span:firs-of-type {
    background-color: purple;
  }
  /*选择指定类型的元素 最后一个span元素*/
  div span:last-of-type {
    background-color: purple;
  }
  /*选择指定类型的元素 span标签中的第二个元素*/
  div span:nth-of-type(2) {
    background-color: purple;
  }
  ```

  #### 伪类选择器需要注意的点

  ```css
      <style>
  				/*这样是选择不出来标签的，因为div里面的第一个标签是p.*/
          div span:nth-child(1) {
              background-color: pink;
  				}
  				/*这里可以选出第一个span标签*/
  				div span:nth-child(2) {
              background-color: pink;
          }
      </style>
  </head>
  
  <body>
      <div>
          <p>我是P标签</p>
          <span>我是span标签</span>
          <span>我是span标签</span>
          <span>我是span标签</span>
      </div>
  </body>
  ```

- #### 伪元素选择器案例--使用字体图标

  ```html
  <header>
    <style>
   @font-family{
        /*字体图标的内容*/
      }
      p::after{
        content:'\es08'  /* ‘\’ 转义字符 */
      }
    </style>
  </header>
  <body>
    <p></p>
  </body>
  ```

- #### 2D转换

  ```html
      <style>
          div:nth-child(1) {
              width: 200px;
              height: 200px;
              background-color: pink;
            /*不影响其他盒子移动*/
              transform: translate(50px, 50px);
            /*移动了自身盒子的一半 移动了100px*/
              transform: translateX(50%);
          }
  
          div:nth-child(2) {
              width: 200px;
              height: 200px;
              background-color: purple;
          }
      </style>
  </head>
  
  <body>
      <div></div>
      <div></div>
  </body>
  ```

- #### 2D转换--定位

  ```html
      <style>
          * {
              margin: 0;
              padding: 0;
          }
  
          div:nth-child(1) {
              position: relative;
              width: 500px;
              height: 500px;
              background-color: pink;
          }
  
          p {
              background-color: purple;
              width: 100px;
              height: 100px;
              position: absolute;
              top: 50%;
              left: 50%;
            /*让盒子水平居中，垂直居中*/
            /*走自身的一半*/
              transform: translate(-50%, -50%);
          }
      </style>
  </head>
  
  <body>
      <div>
          <p></p>
      </div>
  </body>
  ```

- #### 2D转换旋转--实例（代码实现小图标）

  ```html
     <style>
          div {
              position: relative;
              width: 250px;
              height: 50px;
              border: 1px solid #000;
          }
  
          div::after {
              content: '';
              position: absolute;
              top: 10px;
              right: 15px;
              width: 15px;
              height: 15px;
              border-bottom: 1px solid red;
              border-right: 1px solid red;
              transform: rotate(45deg);
            	/*谁做动画给谁加*/
              transition: all .4s;
          }
       		/*逻辑问题*/
          div:hover::after {
              transform: rotate(225deg);
          }
      </style>
  </head>
  
  <body>
      <div></div>
  </body>
  ```

- #### 2D转换--中心点

  ```html
      <style>
          div {
              width: 200px;
              height: 200px;
              background-color: purple;
              margin: 100px auto;
              transition: all 1s;
            /*可以加方位词、百分比、px像素*/
            /*默认是50% 50%*/
              transform-origin: left bottom;
          }
          div:hover {
              transform: rotate(360deg);
          }
      </style>
  </head>
  
  <body>
      <div></div>
  </body>
  ```

- #### 2D转换--案例

  ```html
      <style>
          div {
              width: 200px;
              height: 200px;
              border: 1px solid red;
              overflow: hidden;
              float: left;
              margin: 10px;
          }
  
          div::after {
              content: '武汉加油';
              display: inline-block;
              background-color: greenyellow;
              width: 100%;
              height: 100%;
              transform: rotate(180deg);
              transform-origin: left bottom;
              transition: all 0.4s;
          }
  
          div:hover::after {
              transform: rotate(0);
          }
      </style>
  </head>
  
  <body>
      <div></div>
  </body>
  ```

- #### 2D转换--缩放

  - 不会影响其他盒子
  - 可以设置中心点

  ```html
      <style>
          div {
              width: 200px;
              height: 200px;
              background-color: purple;
              margin: 200px auto;
              transition: all 0.2s;
          }
  
          div:hover {
            /*scale(2)---宽高都扩大原来的2倍*/
              transform: scale(2);
   					/*scale(1,2)---宽不变，高扩大原来的2倍*/
            	transform:scale(1,2)
            /*scale(0.5,0.5) 缩小了原来的0.5倍*/
              transform:scale(0.5,0.5)
          }
      </style>
  </head>
  
  <body>
      <div></div>
  </body>
  ```

- #### 动画

  ```css
  <style>	
  				/*move 动画的名称*/
          @keyframes move {
            /* 0%---from */
              0% {
                  transform: translateX(0);
              }
            /* 100%--to */
              100% {
                  transform: translateX(1000px);
              }
          }
  
          div {
              width: 200px;
              height: 200px;
              background-color: hotpink;
              /* 动画的名称 */
              animation-name: move;
              /* 动画持续的时间 */
              animation-duration: 5s;
              /* 运动曲线 */
              animation-timing-function: ease;
              /* 何时开始 */
              animation-delay: 1s;
              /*  重复次数-iteration 次数-count 无限循环-infinite */
              animation-iteration-count: infinite;
              /* 是否反方向播放 默认：Nomal*/
              animation-direction: alternate;
              /* 动画结束后的状态 */
              animation-fill-mode: backwards;
          }
      </style>
  ```

  

