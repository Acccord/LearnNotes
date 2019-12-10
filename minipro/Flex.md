## 一、Flex布局是什么？
Flex是Flexible Box的缩写，意为”弹性布局”，用来为盒状模型提供最大的灵活性。
任何一个容器都可以指定为Flex布局。
``` css
  .box{
    display: flex;
  }
```
 行内元素也可以使用Flex布局。
 ``` css
  .box{
    display: inline-flex;
  }
 ```
 
## 基本概念
采用Flex布局的元素，称为Flex容器（flex container），简称”容器”。它的所有子元素自动成为容器成员，称为Flex项目（flex item），简称”项目”。<br>
容器默认存在两根轴：水平的主轴（main axis）和垂直的交叉轴（cross axis）。主轴的开始位置（与边框的交叉点）叫做main start，结束位置叫做main end；交叉轴的开始位置叫做cross start，结束位置叫做cross end。<br>
项目默认沿主轴排列。单个项目占据的主轴空间叫做main size，占据的交叉轴空间叫做cross size。<br>

## 容器的属性
- flex-direction 决定主轴的方向【水平/竖直】
  - row（默认值）：主轴为水平方向，起点在左端。
  - row-reverse：主轴为水平方向，起点在右端。
  - column：主轴为垂直方向，起点在上沿。
  - column-reverse：主轴为垂直方向，起点在下沿。
``` css
  .box {
    flex-direction: row | row-reverse | column | column-reverse;
  }
```
- flex-wrap
- flex-flow
- justify-content
- align-items
- align-content
