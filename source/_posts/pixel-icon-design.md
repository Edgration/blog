---
title: 像素图标设计（updating⏳）
date: 2020-06-03 21:26:51
tags:
- CSS
categories:
- 前端
---
<link href="/scss/pixel-icon-design/base.css" rel="stylesheet"></link>

> 一切来源于生活，看到或想到感兴趣的东西，仅仅用自己想要的形式表现出来。

定义一个固定宽高的元素块，如：`5px x 5px`的正方形块。使用CSS属性`box-shadow`对元素块添加多个阴影效果，单独对每个阴影效果设置不同的`颜色`以及`X、Y轴偏移量`，最后拼接成想要的图案。

## slime

<i class="pixel-slime"></i>

<details>
  <summary>显示代码</summary>

  ```html HTML
  <i class="pixel-slime"></i>
  ```

  ```scss SCSS
  .pixel-slime {
    height: 100px;
    width: 105px;
    position: relative;
    display: inline-block;
    margin: 20px;
    &::before {
      content: "";
      position: absolute;
      background: 0 0;
      width: 5px;
      height: 5px;
      top: -5px;
      left: -5px;
      box-shadow: 65px 5px rgb(91, 155, 213), 55px 10px rgb(91, 155, 213), 60px 10px rgb(91, 155, 213), 70px 10px rgb(91, 155, 213), 40px 15px rgb(91, 155, 213), 45px 15px rgb(91, 155, 213), 50px 15px rgb(91, 155, 213), 75px 15px rgb(91, 155, 213), 30px 20px rgb(91, 155, 213), 35px 20px rgb(91, 155, 213), 80px 20px rgb(91, 155, 213), 20px 25px rgb(91, 155, 213), 25px 25px rgb(91, 155, 213), 85px 25px rgb(91, 155, 213), 90px 25px rgb(91, 155, 213), 15px 30px rgb(91, 155, 213), 95px 30px rgb(91, 155, 213), 10px 35px rgb(91, 155, 213), 100px 35px rgb(91, 155, 213), 10px 40px rgb(91, 155, 213), 100px 40px rgb(91, 155, 213), 5px 45px rgb(91, 155, 213), 105px 45px rgb(91, 155, 213), 5px 50px rgb(91, 155, 213), 105px 50px rgb(91, 155, 213), 5px 55px rgb(91, 155, 213), 105px 55px rgb(91, 155, 213), 5px 60px rgb(91, 155, 213), 105px 60px rgb(91, 155, 213), 5px 65px rgb(91, 155, 213), 105px 65px rgb(91, 155, 213), 5px 70px rgb(91, 155, 213), 105px 70px rgb(91, 155, 213), 10px 75px rgb(91, 155, 213), 100px 75px rgb(91, 155, 213), 10px 80px rgb(91, 155, 213), 100px 80px rgb(91, 155, 213), 15px 85px rgb(91, 155, 213), 95px 85px rgb(91, 155, 213), 20px 90px rgb(91, 155, 213), 25px 90px rgb(91, 155, 213), 85px 90px rgb(91, 155, 213), 90px 90px rgb(91, 155, 213), 30px 95px rgb(91, 155, 213), 35px 95px rgb(91, 155, 213), 75px 95px rgb(91, 155, 213), 80px 95px rgb(91, 155, 213), 40px 100px rgb(91, 155, 213), 45px 100px rgb(91, 155, 213), 50px 100px rgb(91, 155, 213), 55px 100px rgb(91, 155, 213), 60px 100px rgb(91, 155, 213), 65px 100px rgb(91, 155, 213), 70px 100px rgb(91, 155, 213), 65px 10px rgb(221, 235, 247), 55px 15px rgb(221, 235, 247), 60px 15px rgb(221, 235, 247), 70px 15px rgb(221, 235, 247), 50px 20px rgb(221, 235, 247), 75px 20px rgb(221, 235, 247), 80px 25px rgb(221, 235, 247), 85px 30px rgb(221, 235, 247), 90px 30px rgb(221, 235, 247), 15px 35px rgb(221, 235, 247), 100px 55px rgb(221, 235, 247), 100px 60px rgb(221, 235, 247), 85px 65px rgb(221, 235, 247), 15px 60px rgb(221, 235, 247), 40px 20px rgb(242, 247, 252), 45px 20px rgb(242, 247, 252), 30px 25px rgb(242, 247, 252), 35px 25px rgb(242, 247, 252), 20px 30px rgb(242, 247, 252), 25px 30px rgb(242, 247, 252), 95px 35px rgb(242, 247, 252), 95px 40px rgb(242, 247, 252), 100px 45px rgb(242, 247, 252), 100px 50px rgb(242, 247, 252), 25px 50px rgb(242, 247, 252), 20px 60px rgb(242, 247, 252), 70px 55px rgb(242, 247, 252), 80px 65px rgb(242, 247, 252), 65px 15px rgb(189, 215, 238), 55px 20px rgb(189, 215, 238), 60px 20px rgb(189, 215, 238), 65px 20px rgb(189, 215, 238), 70px 20px rgb(189, 215, 238), 40px 25px rgb(189, 215, 238), 45px 25px rgb(189, 215, 238), 50px 25px rgb(189, 215, 238), 55px 25px rgb(189, 215, 238), 60px 25px rgb(189, 215, 238), 65px 25px rgb(189, 215, 238), 70px 25px rgb(189, 215, 238), 75px 25px rgb(189, 215, 238), 30px 30px rgb(189, 215, 238), 35px 30px rgb(189, 215, 238), 40px 30px rgb(189, 215, 238), 45px 30px rgb(189, 215, 238), 50px 30px rgb(189, 215, 238), 55px 30px rgb(189, 215, 238), 60px 30px rgb(189, 215, 238), 65px 30px rgb(189, 215, 238), 70px 30px rgb(189, 215, 238), 75px 30px rgb(189, 215, 238), 80px 30px rgb(189, 215, 238), 20px 35px rgb(189, 215, 238), 25px 35px rgb(189, 215, 238), 30px 35px rgb(189, 215, 238), 35px 35px rgb(189, 215, 238), 40px 35px rgb(189, 215, 238), 45px 35px rgb(189, 215, 238), 50px 35px rgb(189, 215, 238), 55px 35px rgb(189, 215, 238), 60px 35px rgb(189, 215, 238), 65px 35px rgb(189, 215, 238), 70px 35px rgb(189, 215, 238), 75px 35px rgb(189, 215, 238), 80px 35px rgb(189, 215, 238), 85px 35px rgb(189, 215, 238), 90px 35px rgb(189, 215, 238), 15px 40px rgb(189, 215, 238), 20px 40px rgb(189, 215, 238), 25px 40px rgb(189, 215, 238), 30px 40px rgb(189, 215, 238), 35px 40px rgb(189, 215, 238), 40px 40px rgb(189, 215, 238), 45px 40px rgb(189, 215, 238), 50px 40px rgb(189, 215, 238), 55px 40px rgb(189, 215, 238), 60px 40px rgb(189, 215, 238), 65px 40px rgb(189, 215, 238), 70px 40px rgb(189, 215, 238), 75px 40px rgb(189, 215, 238), 80px 40px rgb(189, 215, 238), 85px 40px rgb(189, 215, 238), 90px 40px rgb(189, 215, 238), 10px 45px rgb(189, 215, 238), 15px 45px rgb(189, 215, 238), 20px 45px rgb(189, 215, 238), 25px 45px rgb(189, 215, 238), 30px 45px rgb(189, 215, 238), 90px 45px rgb(189, 215, 238), 95px 45px rgb(189, 215, 238), 10px 50px rgb(189, 215, 238), 15px 50px rgb(189, 215, 238), 20px 50px rgb(189, 215, 238), 95px 50px rgb(189, 215, 238), 10px 55px rgb(189, 215, 238), 15px 55px rgb(189, 215, 238), 10px 60px rgb(189, 215, 238), 10px 65px rgb(189, 215, 238), 10px 70px rgb(189, 215, 238), 15px 75px rgb(189, 215, 238), 15px 80px rgb(189, 215, 238), 20px 85px rgb(189, 215, 238), 25px 85px rgb(189, 215, 238), 30px 90px rgb(189, 215, 238), 35px 90px rgb(189, 215, 238), 100px 65px rgb(189, 215, 238), 100px 70px rgb(189, 215, 238), 95px 75px rgb(189, 215, 238), 95px 80px rgb(189, 215, 238), 85px 85px rgb(189, 215, 238), 90px 85px rgb(189, 215, 238), 75px 90px rgb(189, 215, 238), 80px 90px rgb(189, 215, 238), 40px 95px rgb(189, 215, 238), 45px 95px rgb(189, 215, 238), 50px 95px rgb(189, 215, 238), 55px 95px rgb(189, 215, 238), 60px 95px rgb(189, 215, 238), 65px 95px rgb(189, 215, 238), 70px 95px rgb(189, 215, 238), 20px 55px rgb(180, 198, 231), 35px 45px rgb(180, 198, 231), 40px 45px rgb(180, 198, 231), 45px 45px rgb(180, 198, 231), 50px 45px rgb(180, 198, 231), 55px 45px rgb(180, 198, 231), 60px 45px rgb(180, 198, 231), 65px 45px rgb(180, 198, 231), 70px 45px rgb(180, 198, 231), 75px 45px rgb(180, 198, 231), 80px 45px rgb(180, 198, 231), 85px 45px rgb(180, 198, 231), 35px 50px rgb(180, 198, 231), 40px 50px rgb(180, 198, 231), 45px 50px rgb(180, 198, 231), 50px 50px rgb(180, 198, 231), 55px 50px rgb(180, 198, 231), 60px 50px rgb(180, 198, 231), 65px 50px rgb(180, 198, 231), 70px 50px rgb(180, 198, 231), 75px 50px rgb(180, 198, 231), 80px 50px rgb(180, 198, 231), 85px 50px rgb(180, 198, 231), 90px 50px rgb(180, 198, 231), 35px 55px rgb(180, 198, 231), 40px 55px rgb(180, 198, 231), 45px 55px rgb(180, 198, 231), 50px 55px rgb(180, 198, 231), 55px 55px rgb(180, 198, 231), 60px 55px rgb(180, 198, 231), 65px 55px rgb(180, 198, 231), 80px 55px rgb(180, 198, 231), 85px 55px rgb(180, 198, 231), 90px 55px rgb(180, 198, 231), 95px 55px rgb(180, 198, 231), 25px 60px rgb(180, 198, 231), 30px 60px rgb(180, 198, 231), 35px 60px rgb(180, 198, 231), 40px 60px rgb(180, 198, 231), 45px 60px rgb(180, 198, 231), 50px 60px rgb(180, 198, 231), 55px 60px rgb(180, 198, 231), 60px 60px rgb(180, 198, 231), 65px 60px rgb(180, 198, 231), 80px 60px rgb(180, 198, 231), 85px 60px rgb(180, 198, 231), 90px 60px rgb(180, 198, 231), 95px 60px rgb(180, 198, 231), 15px 65px rgb(180, 198, 231), 20px 65px rgb(180, 198, 231), 25px 65px rgb(180, 198, 231), 30px 65px rgb(180, 198, 231), 90px 65px rgb(180, 198, 231), 95px 65px rgb(180, 198, 231), 15px 70px rgb(180, 198, 231), 20px 70px rgb(180, 198, 231), 90px 70px rgb(180, 198, 231), 95px 70px rgb(180, 198, 231), 35px 65px rgb(142, 169, 219), 40px 65px rgb(142, 169, 219), 45px 65px rgb(142, 169, 219), 50px 65px rgb(142, 169, 219), 55px 65px rgb(142, 169, 219), 60px 65px rgb(142, 169, 219), 65px 65px rgb(142, 169, 219), 70px 65px rgb(142, 169, 219), 75px 65px rgb(142, 169, 219), 35px 70px rgb(142, 169, 219), 40px 70px rgb(142, 169, 219), 45px 70px rgb(142, 169, 219), 50px 70px rgb(142, 169, 219), 55px 70px rgb(142, 169, 219), 60px 70px rgb(142, 169, 219), 65px 70px rgb(142, 169, 219), 70px 70px rgb(142, 169, 219), 75px 70px rgb(142, 169, 219), 80px 70px rgb(142, 169, 219), 85px 70px rgb(142, 169, 219), 35px 75px rgb(142, 169, 219), 40px 75px rgb(142, 169, 219), 25px 70px rgb(142, 169, 219), 20px 75px rgb(142, 169, 219), 25px 75px rgb(142, 169, 219), 20px 80px rgb(142, 169, 219), 25px 80px rgb(142, 169, 219), 30px 80px rgb(142, 169, 219), 50px 75px rgb(142, 169, 219), 55px 75px rgb(142, 169, 219), 65px 75px rgb(142, 169, 219), 70px 75px rgb(142, 169, 219), 75px 75px rgb(142, 169, 219), 80px 75px rgb(142, 169, 219), 85px 75px rgb(142, 169, 219), 90px 75px rgb(142, 169, 219), 45px 80px rgb(142, 169, 219), 60px 80px rgb(142, 169, 219), 65px 80px rgb(142, 169, 219), 70px 80px rgb(142, 169, 219), 75px 80px rgb(142, 169, 219), 80px 80px rgb(142, 169, 219), 85px 80px rgb(142, 169, 219), 90px 80px rgb(142, 169, 219), 30px 85px rgb(142, 169, 219), 35px 85px rgb(142, 169, 219), 40px 85px rgb(142, 169, 219), 45px 85px rgb(142, 169, 219), 50px 85px rgb(142, 169, 219), 55px 85px rgb(142, 169, 219), 60px 85px rgb(142, 169, 219), 65px 85px rgb(142, 169, 219), 70px 85px rgb(142, 169, 219), 75px 85px rgb(142, 169, 219), 80px 85px rgb(142, 169, 219), 40px 90px rgb(142, 169, 219), 45px 90px rgb(142, 169, 219), 50px 90px rgb(142, 169, 219), 55px 90px rgb(142, 169, 219), 60px 90px rgb(142, 169, 219), 65px 90px rgb(142, 169, 219), 70px 90px rgb(142, 169, 219), 30px 70px rgb(248, 203, 173), 30px 75px rgb(248, 203, 173), 35px 80px rgb(248, 203, 173), 40px 80px rgb(248, 203, 173), 45px 75px rgb(248, 203, 173), 50px 80px rgb(248, 203, 173), 55px 80px rgb(248, 203, 173), 60px 75px rgb(248, 203, 173), 30px 50px rgb(64, 64, 64), 25px 55px rgb(64, 64, 64), 30px 55px rgb(64, 64, 64), 75px 55px rgb(64, 64, 64), 70px 60px rgb(64, 64, 64), 75px 60px rgb(64, 64, 64);
    }
  }
  ```
</details>

---

## orange

<i class="pixel-orange"></i>

<h2 class="to-be-continued headerlink" id="To be continued">To be continued<dot></dot></h2>
