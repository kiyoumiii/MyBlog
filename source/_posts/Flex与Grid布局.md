---
title: Flex与Grid布局
date: 2025-02-21 13:52:57
categories:
- [前端开发]
tags:
- [前端]
---

# Flex布局与Grid布局

1. flex 布局又称为弹性布局。

- 当我们给一个容器元素设置 display:flex; 时，这个容器就变成了 flex 容器，容器中所有直接子元素就成了容器成员（flex 项目）。
- flex 容器默认存在两根轴：水平的主轴和垂直的交叉轴，flex 布局主要是围绕这两根轴来进行布局的。
- 所以 flex 布局相对于 grid 网格布局来说，他更适合一维布局（单行或单列布局）

父容器属性：flex-direction， justify-content， align-items， align-content
子容器属性：order， flex-grow， flex-shrink， flex-basis， align-self

2. Grid 布局又称为网格布局。

- 当我们给一个元素加上 display:grid;时，我们称这个元素为容器，元素中所有直接子元素称为子项或项目。
- Grid 布局则是将容器划分成行和列，产生单元格，然后指定项目所在的单元格，可以看作是二维布局。
- 划分网格的线，称为"网格线"（grid line）。水平网格线划分出行，垂直网格线划分出列。
- 设为网格布局以后，容器子元素（项目）的float、display: inline-block、display: table-cell、vertical-align和column-*等设置都将失效。

父容器属性：grid-template-columns， grid-template-rows， grid-gap， grid-auto-flow， grid-auto-columns， grid-auto-rows， justify-items， align-items， justify-content， align-content
子容器属性：grid-column-start， grid-column-end， grid-row-start， grid-row-end， justify-self， align-self

3. 经典问题

### 经典问题：

#### ask: flex=1是什么意思

#### answer: flex: 1 是 CSS Flexbox 布局中的一个属性值，用于控制弹性容器内子元素的伸缩行为。

具体含义
flex 是 flex-grow、flex-shrink 和 flex-basis 的简写。

flex: 1 等同于 flex: 1 1 0，表示：

flex-grow: 1：子元素会按比例分配剩余空间。

flex-shrink: 1：子元素在空间不足时会缩小。

flex-basis: 0：子元素的初始大小为 0。

效果
子元素会根据 flex-grow 的值分配剩余空间。

如果多个子元素都有 flex: 1，它们将平分剩余空间。


#### ask: flex 布局设置水平垂直居中
#### answer: 给 flex 容器添加以下三个属性，就可以实现子项水平垂直居中：

display: flex; // 容器为 flex 布局
justify-content: center; // 子项在主轴（水平居中）
align-items: center; // 子项在交叉轴（垂直居中）


#### ask: 如何解决 flex 布局 7 个元素使用 space-between 最后一行两边分布的问题？
#### answer: 如果我们每一行显示的个数为 n，那我们可以最后一行子项的后面加上 n-2 个 span 元素，span 元素的宽度和其它子项元素宽度一样，但不用设置高度。

为什么是添加 n-2 个 span 元素呢 ？

当最后一行只有 1 个子元素时，他会默认靠左，不用处理
当最后一行子元素正好时，我们就不用关心这个问题。
所以要去掉这两种情况，只需要加 n-2 个 span 元素就好

#### ask: flex 实现 8 个元素分两行排列 每行 4 个平均分布-自适应
#### answer: 给父元素设置 display: flex; flex-wrap: wrap; 子元素设置 flex: 1 0 25%;

给父容器添加如下属性：

display: flex; // flex 布局
flex-wrap: wrap; // 换行
给子项添加如下样式：

flex-basis: 25%; // 项目占据主轴（父容器宽）的空间。
flex-grow: 0; // 不放大
flex-shrink: 0; // 缩小
以上三个属性，也可以简写在 flex: 0 0 25%;

####  当容器为 flex 时，其子元素没有指定高度时，其高度默认为父元素高度。

#### ask: 圣杯布局
#### answer: 拥有 header 和 footer，中间是主内容行;left 和 right 分别固定了宽度，center 会随着整体布局宽度的变化而进行伸缩

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="UTF-8">
		<meta name="viewport" content="width=device-width, initial-scale=1.0">
		<meta http-equiv="X-UA-Compatible" content="ie=edge">
		<title>圣杯布局</title>
		<style type="text/css">
			body {
				min-width: 550px;
			}

			#header {
				background-color: #999999;
			}
			
			#middle{
				/* 2.把中间部分留出左右元素的宽度 */
				padding-left: 200px;
				padding-right: 150px;
			}
			
			#middle .column{
				float: left;
				height: 200px;
			}
			
			#left{
				width: 200px;
				background-color: #FFFF00;
				/* 4. 向左移动center的宽度 */
				margin-left: -100%;
				/* 5. 再向左移动自身宽度，露出被覆盖的center块 */
				position: relative;
				right: 200px;
			}
			
			#center{
				width: 100%;
				background-color: pink;
			}
			
			#right{
				/* 3.margin-right让右方元素覆盖自身，达到消除自身宽度的目的，浮动到center上面去 */
				margin-right: -150px;
				width: 150px;
				background-color: #CCCCCC;
			}
			
			#footer {
				background-color: #999999;
			}
			
			.clearfix:after{
				display: table;
				content: '';
				clear: both;
			}
		</style>
	</head>
	<body>
		<div id="header">header</div>
		<div id="middle" class="clearfix">
			<div id="center" class="column">
				center
			</div>
			<div id="left" class="column">
				left
			</div>
			<div id="right" class="column">
				right
			</div>
		</div>
		<div id="footer">footer</div>
	</body>
</html>

```


#### ask: 双飞翼布局
#### answer: left 和 right 固定宽度; 中间 main 会随着整体布局宽度的变化而伸缩

```html
<!DOCTYPE html>
<html>
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>双飞翼布局</title>
    <style type="text/css">
        body {
            min-width: 550px;
        }
        .col {
			/* 1.设置浮动 */
			float: left;
        }

        #main {
            width: 100%;
            height: 200px;
            background-color: #FFC0CB;
        }
        #main-wrap {
			/* 2.将 main 左右内边距留出 left 和 right 的宽度 */
			margin: 0 200px 0 150px;
        }

        #left {
            width: 150px;
            height: 200px;
            background-color: #FFFF00;
			/* 3.left 向左偏移 main 的宽度 */
			margin-left: -100%;
        }
        #right {
            width: 200px;
            height: 200px;
            background-color: #cccccc;
			/* 4.right 向左偏移自身宽度 */
			margin-left: -200px;
        }
    </style>
</head>
<body>
    <div id="main" class="col">
        <div id="main-wrap">
            main
        </div>
    </div>
    <div id="left" class="col">
        left
    </div>
    <div id="right" class="col">
        right
    </div>
</body>
</html>
```

#### ask: 圣杯布局与双飞翼布局异同比较
#### answer: 

| 维度          | 双飞翼布局                | 圣杯布局                  |
|---------------|-------------------------|---------------------------|
| **边距控制**  | 通过外层 `margin` 实现   | 通过内层 `padding` 实现    |
| **元素偏移**  | 左右均向左偏移           | 左侧左偏移，右侧右偏移      |
| **视觉重心**  | 主内容居中              | 主内容靠左                  |
| **适用场景**  | 广告位/侧边栏固定展示    | 两侧内容灵活布局          |

双飞翼：均使用 margin-left，左：向左偏移main的宽度；右：向左偏移自身宽度 

圣杯:左：使用 margin-left（向左偏移main的宽度）; 右：margin-right（取消自身宽度）