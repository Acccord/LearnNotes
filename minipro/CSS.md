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
