## Flex布局是什么？
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
- flex-direction 【决定主轴的方向 水平/竖直】
  - row（默认值）：主轴为水平方向，起点在左端。
  - row-reverse：主轴为水平方向，起点在右端。
  - column：主轴为垂直方向，起点在上沿。
  - column-reverse：主轴为垂直方向，起点在下沿。
``` css
  .box {
    flex-direction: row | row-reverse | column | column-reverse;
  }
```

- flex-wrap 【如何换行】
  - nowrap（默认）：不换行。
  - wrap：换行，第一行在上方。
  - wrap-reverse：换行，第一行在下方。
``` css
  .box{
    flex-wrap: nowrap | wrap | wrap-reverse;
  }
```

- flex-flow 【flex-direction属性和flex-wrap属性的简写形式】
``` css
  .box {
    /*flex-flow: <flex-direction> || <flex-wrap>;*/
    flex-flow: row nowrap;
  }
```

- justify-content 【在主轴上的对齐方式】
  - flex-start（默认值）：左对齐
  - flex-end：右对齐
  - center： 居中
  - space-between：两端对齐，项目之间的间隔都相等。
  - space-around：每个项目两侧的间隔相等。所以，项目之间的间隔比项目与边框的间隔大一倍。
``` css
  .box { 
    justify-content: flex-start | flex-end | center | space-between | space-around;
  }
```
  
- align-items 【交叉轴的对齐方式】
  - flex-start：交叉轴的起点对齐。
  - flex-end：交叉轴的终点对齐。
  - center：交叉轴的中点对齐。
  - baseline: 项目的第一行文字的基线对齐。
  - stretch（默认值）：如果项目未设置高度或设为auto，将占满整个容器的高度。
``` css
  .box {
    align-items: flex-start | flex-end | center | baseline | stretch;
  }
```

- align-content 【多根轴线的对齐方式。如果项目只有一根轴线，该属性不起作用】
  - flex-start：与交叉轴的起点对齐。
  - flex-end：与交叉轴的终点对齐。
  - center：与交叉轴的中点对齐。
  - space-between：与交叉轴两端对齐，轴线之间的间隔平均分布。
  - space-around：每根轴线两侧的间隔都相等。所以，轴线之间的间隔比轴线与边框的间隔大一倍。
  - stretch（默认值）：轴线占满整个交叉轴。
``` css
  .box {
    align-content: flex-start | flex-end | center | space-between | space-around | stretch;
  }
```

## 子元素属性
- order
> 定义项目的排列顺序。数值越小，排列越靠前，默认为0。
``` css
  .item {
    /*order: <integer>;*/
    order: 0;
  }
```

- flex-grow
> 分蛋糕，即分剩余空间的比例，默认0为不分配
``` css
  .item {
    flex-grow: <number>; /* default 0 */
  }
```

- flex-shrink
> 项目的缩小比例，默认为1，即如果空间不足，该项目将缩小。
> 如果所有项目的flex-shrink属性都为1，当空间不足时，都将等比例缩小。如果一个项目的flex-shrink属性为0，其他项目都为1，则空间不足时，前者不缩小。
负值对该属性无效。
``` css
  .item {
    flex-shrink: <number>; /* default 1 */
  }
```

- flex-basis
> flex-basis属性定义了在分配多余空间之前，项目占据的主轴空间（main size）。浏览器根据这个属性，计算主轴是否有多余空间。它的默认值为auto，即项目的本来大小。
> 它可以设为跟width或height属性一样的值（比如350px），则项目将占据固定空间。
``` css
  .item {
    flex-basis: <length> | auto; /* default auto */
  }
```

- flex
> flex属性是flex-grow, flex-shrink 和 flex-basis的简写，默认值为0 1 auto。后两个属性可选。
> 该属性有两个快捷值：auto (1 1 auto) 和 none (0 0 auto)。
``` css
  .item {
    flex: none | [ <'flex-grow'> <'flex-shrink'>? || <'flex-basis'> ]
  }
```

- align-self
> 可覆盖父容器的align-items属性。默认值为auto，表示继承父元素的align-items属性，如果没有父元素，则等同于stretch。
``` css
  .item {
    align-self: auto | flex-start | flex-end | center | baseline | stretch;
  }
```
