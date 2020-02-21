> 地址：`https://www.bilibili.com/video/av77217003?p=101`



float-left --->> 


display: block  --- 超链接


text-aglin
vertical-aglin


```html

   <ul class="shop-cart">
                <li><a href="javascript:;">
                    <i class="fas fa-shopping-cart"></i>
                    购物车（0）
                </a></li>
   </ul>

```

因为鼠标移入有个弹出层 -- 所以这个 hover 应该绑定给 ul (公共父元素)
这样鼠标在弹出层的时候也不会消失


```css
   /*  不行的 -- display none 会不占位置  */
    /* display: none; */
    visibility: hidden;

```


> 注意：
> 下拉层的话 --- 我们应该想到，让它出现的时候
> 是别的元素盖住它，还是它盖住别的元素 ---- 设置一个比较高的层级 `z-index: 9999;`


<br>

发现没有生效 -- 优先级不够  

<br>

有错误时，F12 多看看

<br>

banner 宽度问题 ---- 

```css

/*  设置 banner   */
.banner{
    /*  宽度已经设置了  */
    position: relative;
}

.banner .img-list li{
    /*  开启绝对定位 --- 脱离文档流  */
    position: absolute;
}

.banner img{
    width: 100%;
    vertical-align: top;
}
```

<br>

雪碧图 --->  使用 background-image 
通过修改偏移量 ` background-position: 水平 垂直;` 


<br>

<br>

```css
/*  设置 回到顶部的元素  */
.back-top{
    width: 26px;
    height: 206px;
    background-color: #bfa;

    /*  开启固定定位  */
    position: fixed;
    /*  固定定位是根据可视视口进行定位的 ， 但是现在可视视口大小是不固定的 */

    /*  定位纵向的位置  */
    bottom: 60px;
    
    /*  
        布局的等式
        （只是针对本例说的）
            left + margin-left + width + margin-right + right = 视口宽度
                如果填 margin-right 去定位 -- 是不行的

            auto    0             26         0            60  =  视口宽度
    */

    right: 50%;  /* 将 right 值设置为视口宽度的 50% */

    /*
        auto  0  26  0  50% = 视口宽度
        
        auto + x  0  26 -x 50% = 视口宽度 ✔

        margin-right -- 影响的是别的元素的位置 --(= maring-bottom
    */
    margin-right: -639px;
         
}

```


<br>

<br>


```css
.ad .imgs img{
    /*  跟随父元素一样大  */
    width: 100%;
    /*  设置图片不要沿着基线对齐  */
    vertical-align: top; 
}
```


<br>

<br>

```css
/*  设置图标字体  */
.ad .shortcut i{
    /*  这样就独占一行了  */
    display: block;
    /*  可设置水平居中  */
    
}


```


<br>

<br>

距离 -- 发现元素过大了
看看是不是有外边距折叠问题

> 外边距折叠问题 --- 子元素会传递给父元素 ( 上外边距 )  --- 方式一 在父元素中解决 -- clearfix 

> 方式二 给父元素 ---  开启 BFC


<br>

<br>


**`伪类before after元素 !!!`**
> 好像是不会撑开元素


