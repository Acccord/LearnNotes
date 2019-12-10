## CSS属性介绍

```
  display: none/flex/inline/block/inline-block/grid;  
    //改变自身
    //none -> 元素隐藏，同时隐藏所占区域
    //flex ->
    //inline -> 行内元素；1多个占一行；2不可以设置宽高；
    //block -> 默认，块级元素；1，自己占一行；2可以设置宽高
    //inline-block -> 行内块元素；1多个占一行；2可以设置宽高
    //grid -> 

  position:static/relative;
    //改变自身和周围环境
    //absolute -> 【绝对定位】脱离文档；会寻找父控件有没有position属性，如果一直没有则会找寻到html根页面
    //fixed -> 【固定定位】与绝对定位相似，不过定位基准不是父组件，而是屏幕
    //static -> 【普通流】默认属性；
    //relative -> 【相对定位】改变自身位置，不会排挤其他控件

  text-align: center; 
    //center -> 控制内组件水平居中

  visibility: visible/hidden;
    //hidden -> 元素不可见，占用空间；类似于Android invisiable
    //visible -> 元素可见

```
其他笔记
```
flex-direction: 决定是横还是竖 

 1>row：从左到右的水平方向为主轴(默认值)

 2>row-reverse：从右到左的水平方向为主轴

 3>column：从上到下的垂直方向为主轴

 4>column-reverse：从下到上的垂直方向为主轴

justify-content: 是在横向上做改变

 1>flex-start：主轴起点对齐(默认值)

 2>flex-end：主轴结束点对齐

 3>center：在主轴中居中对齐

 4>space-between：两端对齐，除了两端的子元素分别靠向两端的容器之外，其他子元素之间的间隔都相等

 5>space-around：每个子元素之间的距离相等，两端的子元素距离容器的距离也和其它子元素之间的距离相同

align-items: 是在纵向上做改变

 1>stretch 填充整个容器(默认值)

 2>flex-start 侧轴的起点对齐 （这里我们手动设置下子 view 的高度，来看的明显一些）

 3>flex-end 侧轴的终点对齐

 4>center 在侧轴中居中对齐

 5>baseline 以子元素的第一行文字对齐

flex-wrap: 是否换行

  1>nowrap：不换行（默认）

  2>wrap：换行

  3>wrap-reverse：换行，第一行在最下面

order: 可以控制子元素的排列顺序，默认为0
```
