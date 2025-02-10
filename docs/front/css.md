## css 面试题

### 说说你对盒子模型的理解?

CSS盒子模型（Box Model）是CSS布局中的一个重要概念，它规定了元素在页面中占据的空间是如何计算和布局的。每个HTML元素都可以视为一个矩形盒子，这个盒子由四部分组成：

01. **内容（Content）**：
   - 内容区域是盒子的核心部分，它包含了元素的实际内容，如文本、图像等。可以通过 `width` 和 `height` 属性来设置内容区域的尺寸。

02. **内边距（Padding）**：
   - 内边距位于内容区域和边框之间，是透明的可填充空间。通过 `padding-top` 、 `padding-right` 、 `padding-bottom` 和 `padding-left` 属性来设置各方向的内边距大小。内边距增加了盒子的总尺寸，即盒子在内容区域的基础上扩大了内边距的总和。

03. **边框（Border）**：
   - 边框包裹在内边距和内容区域之外，可通过 `border-width` 、 `border-style` 和 `border-color` 属性来定义边框的宽度、样式和颜色。边框也会影响盒子的总尺寸。

04. **外边距（Margin）**：
   - 外边距是盒子最外层的空间，它不影响盒子本身的尺寸，但影响盒子与其他盒子之间的距离。通过 `margin-top` 、 `margin-right` 、 `margin-bottom` 和 `margin-left` 属性来设置各方向的外边距大小。外边距是透明的，不影响背景色的显示，主要用于布局和分隔元素。

CSS盒子模型有两种计算模式：
* **W3C标准盒模型**（也称为默认盒模型）：元素的总宽度和总高度等于内容宽度（height/width）加上内边距（padding）加上边框（border）的总和。
* **怪异盒模型（Quirks Mode）**（IE传统盒模型）：元素的总宽度和总高度只包括内容宽度（height/width）和边框（border），内边距（padding）并不计入总尺寸，因此在设置元素的宽高时，内边距会增加实际的总尺寸，导致布局上的差异。

在现代浏览器中，可以通过 `box-sizing` 属性来控制盒子模型的计算方式， `box-sizing: content-box` 遵循标准盒模型， `box-sizing: border-box` 则表示元素的总尺寸包括了边框和内边距，这对于响应式设计和精准布局控制十分有用。

### 谈谈你对BFC的理解?

CSS中的BFC（Block Formatting Context）是一种布局渲染规则，它决定了在一个特定上下文中块级元素如何排列、计算尺寸和与其他元素相互作用。创建了BFC的元素将会拥有一个独立的布局环境，其内部元素布局不受外部元素的影响，同时也不会影响到外部元素。

BFC的主要特性包括：

01. **内部块状元素垂直堆叠**：
   - 在BFC内部的块级元素（包括匿名块级盒子）会在垂直方向上一个接一个地放置，垂直方向的距离由 `margin` 属性决定，而不会重叠。

02. **计算高度时包含浮动元素**：
   - BFC可以包含浮动元素。即使内部的子元素设置了浮动，BFC也会计算其高度，因此可以解决浮动元素引起的父元素高度塌陷问题。

03. **阻止外边距折叠**：
   - 相邻的两个BFC上下边距不会折叠，除非它们之间存在间隙（例如，由空隙、注释或其他非BFC元素引起）。

04. **内部元素与外部元素的边距不会重叠**：
   - BFC内部元素的 `margin` 不会与BFC外部元素的 `margin` 相接触，从而避免了一些意外的布局效果。

创建BFC的方法包括但不限于：
* 设置`overflow`属性为`auto`或`scroll`（默认值不是`visible`）。
* 设置`display`属性为`flex`或`grid`。
* 设置`position`属性为`absolute`或`fixed`（并且`z-index`不是`auto`）。
* `float`属性不为`none`。

BFC在布局中的应用广泛，例如用于清除浮动、防止垂直外边距折叠、实现两栏布局、以及解决一些布局难题等。理解并熟练运用BFC可以帮助开发者更好地掌控CSS布局，实现更加精准和灵活的设计效果。

### 什么是响应式设计? 响应式设计的基本原理是什么? 如何做?

响应式设计（Responsive Design）是一种网页设计方法论，旨在使网站或应用程序能够自动适应不同设备（如桌面电脑、平板电脑、手机等）的屏幕尺寸和方向，提供最佳用户体验。响应式设计的目标是创建流畅的、一致的视觉体验，不论用户使用何种设备访问，都能获得合适的界面布局和内容展现。

响应式设计的基本原理：

01. **流动布局（Fluid Grids）**：
   - 采用百分比代替固定像素值来定义元素的宽度，从而使布局能够随着窗口大小变化而流动调整。

02. **媒体查询（Media Queries）**：
   - 利用CSS3的媒体查询功能，根据设备视窗宽度、设备像素比等因素来应用不同的CSS样式规则。
   - 当设备的特性（如屏幕宽度）满足特定条件时，相应的样式表或样式规则将生效。

03. **可伸缩图片和媒体（Flexible Images & Media）**：
   - 图像和其他媒体资源的尺寸也应该能根据容器大小进行调整，可以通过CSS属性如max-width: 100%来实现自适应缩放。

04. **弹性字体（Elastic Typography）**：
   - 字体大小有时也采用相对单位（如em或rem），使其根据屏幕大小和分辨率进行适配。

实施响应式设计的具体步骤包括：

* 设计阶段：采用响应式设计思维，摒弃固定的像素布局，转向流体布局设计。
* 开发阶段：
   - 使用百分比、em/rem单位来设置元素尺寸。
   - 使用媒体查询编写不同屏幕尺寸下的样式规则。
   - 使用max-width等属性确保图片和其他媒体元素自适应容器尺寸。
* 测试阶段：在多种设备和屏幕尺寸下进行测试，确保布局和功能在不同环境下都能正常工作。

例如：

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <style>
        body {
            font-size: 16px;
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
        }

        .content {
            padding: 2rem;
            box-sizing: border-box;
        }

        img {
            max-width: 100%;
            height: auto;
        }

        @media (min-width: 768px) {
            .sidebar {
                float: right;
                width: 30%;
            }

            .main-content {
                width: 70%;
            }
        }
    </style>
</head>

<body>
    <div class="container">
        <div class="sidebar">侧边栏内容...</div>
        <div class="main-content">
            <div class="content">主要内容...</div>
            <img src="image.jpg" alt="响应式图片">
        </div>
    </div>
</body>

</html>
```

在这个示例中， `.container` 的宽度采用了最大宽度限制以适应不同屏幕尺寸， `.sidebar` 和 `.main-content` 在屏幕宽度至少为768px时会采用响应式布局，图片则始终保持其容器的100%宽度。通过这种方式，网页布局和内容可以随着屏幕大小的变化而灵活调整。

### 元素水平垂直居中的方法有哪些? 如果元素不定宽高呢?

元素水平垂直居中的方法有很多种，对于不定宽高的元素也可以实现居中，以下是一些常用的方法：

01. **Flex布局**：
   - 当元素不定宽高时，可以利用Flex布局轻松实现水平垂直居中。设置父容器为弹性布局，并通过 `justify-content` 和 `align-items` 属性来实现居中对齐。

   

```css
   .parent {
       display: flex;
       justify-content: center;
       /* 水平居中 */
       align-items: center;
       /* 垂直居中 */
   }
```

02. **Grid布局**：
   - 使用Grid布局，只需一行代码就可以使子元素在网格容器中水平和垂直居中。

   

```css
   .parent {
       display: grid;
       place-items: center;
   }
```

03. **绝对定位与Transform**：
   - 当元素不定宽高时，可以使用绝对定位结合 `transform` 属性来实现居中。

   

```css
   .parent {
       position: relative;
   }

   .child {
       position: absolute;
       top: 50%;
       left: 50%;
       transform: translate(-50%, -50%);
   }
```

04. **CSS Grid布局结合fr单位**：
   - 如果元素的宽度和高度不确定，但希望占满可用空间，可以使用CSS Grid布局和 `fr` 单位来分配空间，并居中内容。

   

```css
   .parent {
       display: grid;
       place-items: center;
       height: 100vh;
       /* 或者任意高度 */
       width: 100vw;
       /* 或者任意宽度 */
   }

   .child {
       grid-area: 1 / 1;
       /* 子元素自动填充满并居中 */
   }

   /* 或者使用grid-template-columns和grid-template-rows */
   .parent {
       display: grid;
       grid-template-columns: 1fr;
       grid-template-rows: 1fr;
       justify-items: center;
       align-items: center;
   }
```

05. **CSS calc()配合margin-auto**：
   - 如果浏览器支持 `calc()` 函数，可以尝试计算负边距配合 `margin: auto` 来实现居中。

   

```css
   .parent {
       position: relative;
   }

   .child {
       position: absolute;
       top: calc(50% -
               /* half of dynamic height */
           );
       left: calc(50% -
               /* half of dynamic width */
           );
       transform: translate(-50%, -50%);
       /* 或者 */
       margin: auto;
       top: 0;
       bottom: 0;
       left: 0;
       right: 0;
   }
```

注意，在使用最后一种方法时，因为元素的宽高是未知的，所以直接用 `calc()` 可能较难实现，但可以通过JavaScript动态计算元素的宽高后再设置样式，或者结合CSS变量和JavaScript来动态更新样式实现居中。

### 如何实现两栏布局, 右侧自适应? 三栏布局中间自适应呢?

两栏布局，右侧自适应的实现方法：

**方法一：Flex布局**

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <style>
        .container {
            display: flex;
        }

        .left-column {
            width: 200px;
            /* 左侧固定宽度 */
            background-color: #f0f0f0;
        }

        .right-column {
            flex-grow: 1;
            /* 自动填充剩余空间 */
            background-color: #e0e0e0;
        }
    </style>
</head>

<body>
    <div class="container">
        <div class="left-column">左侧固定宽度</div>
        <div class="right-column">右侧自适应宽度</div>
    </div>
</body>

</html>
```

**方法二：浮动布局**

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <style>
        .container {
            overflow: hidden;
            /* 清除浮动 */
        }

        .left-column {
            float: left;
            width: 200px;
            background-color: #f0f0f0;
        }

        .right-column {
            margin-left: 200px;
            /* 设置左侧与固定宽度栏相等的外边距 */
            background-color: #e0e0e0;
        }
    </style>
</head>

<body>
    <div class="container">
        <div class="left-column">左侧固定宽度</div>
        <div class="right-column">右侧自适应宽度</div>
    </div>
</body>

</html>
```

三栏布局，中间自适应的实现方法：

**方法一：Flex布局**

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <style>
        .container {
            display: flex;
        }

        .left-column {
            width: 200px;
            background-color: #f0f0f0;
        }

        .middle-column {
            flex: 1;
            /* 自动填充剩余空间 */
            background-color: #e0e0e0;
        }

        .right-column {
            width: 200px;
            background-color: #d0d0d0;
        }
    </style>
</head>

<body>
    <div class="container">
        <div class="left-column">左侧固定宽度</div>
        <div class="middle-column">中间自适应宽度</div>
        <div class="right-column">右侧固定宽度</div>
    </div>
</body>

</html>
```

**方法二：CSS Grid布局**

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <style>
        .container {
            display: grid;
            grid-template-columns: 200px 1fr 200px;
        }

        .column {
            padding: 1rem;
            border: 1px solid #ccc;
        }

        .left-column {
            background-color: #f0f0f0;
        }

        .middle-column {
            background-color: #e0e0e0;
        }

        .right-column {
            background-color: #d0d0d0;
        }
    </style>
</head>

<body>
    <div class="container">
        <div class="column left-column">左侧固定宽度</div>
        <div class="column middle-column">中间自适应宽度</div>
        <div class="column right-column">右侧固定宽度</div>
    </div>
</body>

</html>
```

这些方法可以实现在不同屏幕尺寸下，两侧栏宽度固定，中间栏根据剩余空间自适应调整宽度的布局效果。根据项目需求和浏览器兼容性要求，可以选择适当的方法。

### css选择器有哪些? 优先级? 哪些属性可以继承?

CSS选择器有多种类型，用于精确匹配和选择HTML文档中的元素。以下是主要的选择器类型：

01. **基本选择器**：
   - 标签选择器（Element selectors）：如 `div` 、 `p` 等，匹配所有具有指定标签名称的元素。
   - 类选择器（Class selectors）：以 `.` 开头，如 `.class-name` ，匹配所有class属性包含指定类名的元素。
   - ID选择器（ID selectors）：以 `#` 开头，如 `#id-name` ，匹配ID属性为指定ID值的唯一元素。
   - 属性选择器（Attribute selectors）：根据元素的属性及属性值来选择，如 `[attr=value]` 、 `[attr~=value]` 等。

02. **组合选择器**：
   - 后代选择器（Descendant selectors）：两个选择器之间用空格分隔，如 `div p` ，匹配所有属于 `div` 元素后代的 `p` 元素。
   - 子元素选择器（Child selectors）：两个选择器之间用 `>` 分隔，如 `div > p` ，匹配所有直接位于 `div` 元素之下的 `p` 子元素。
   - 相邻兄弟选择器（Adjacent sibling selectors）：两个选择器之间用 `+` 分隔，如 `p + ul` ，匹配紧接在 `p` 元素之后的同级 `ul` 元素。
   - 一般兄弟选择器（General sibling selectors）：两个选择器之间用 `~` 分隔，如 `p ~ ul` ，匹配所有跟在 `p` 元素之后的同级 `ul` 元素。

03. **伪类和伪元素选择器**：
   - 伪类选择器：如 `:hover` 、 `:active` 、 `:focus` 、 `:first-child` 、 `:nth-child(n)` 等，用于匹配元素在特定状态或符合特定条件时的表现。
   - 伪元素选择器：如 `::before` 、 `::after` 、 `::first-letter` 、 `::first-line` 等，用于在元素内部生成内容。

04. **层级选择器（CSS Selectors Level 4）**：
   - `:has()` ：匹配含有特定子元素的选择器。
   - `:is()` 和 `:where()` ：根据一组选择器中的任一选择器匹配元素。

优先级：
CSS选择器的优先级是由权重决定的，权重由四个部分构成（从左到右依次是内联样式、ID选择器、类选择器和其他选择器如属性选择器、伪类等、标签选择器）：

* 内联样式（如`style`属性）：权重为1000。
* ID选择器：每个ID选择器权重为100。
* 类选择器、属性选择器、伪类选择器：每个这类选择器权重为10。
* 标签选择器和伪元素选择器：每个这类选择器权重为1。

如果一个选择器中含有多个同类型的选择器，则权重叠加。当权重相同时，后者优先级更高。!important声明可以覆盖所有优先级，具有最高优先级。

可继承的属性：
并非所有CSS属性都可以继承，以下是一些常见的可继承属性：

* 字体属性：`font-family`、`font-size`、`font-weight`、`font-style`、`line-height`（部分浏览器不继承）
* 文本相关属性：`color`、`text-align`、`letter-spacing`、`word-spacing`、`text-transform`、`white-space`、`text-decoration`（仅`text-decoration-color`和`text-decoration-line`在CSS3中可继承）
* 列表样式属性：`list-style-type`、`list-style-position`、`list-style-image`
* 其他：`cursor`、`visibility`（在CSS2中可继承，但在CSS3中不建议这样做）

请注意，具体哪些属性可继承还取决于浏览器的实现，以及CSS规范的版本。

### css中，有哪些方式可以隐藏页面元素? 区别?

CSS中有多种方式可以隐藏页面元素，以下是其中一些常见方法及其区别：

01. **display: none**
   

```css
   .hide {
       display: none;
   }
```

   - **特点**：这是最彻底的隐藏方式，隐藏元素后，元素不再参与文档流布局，不占用任何空间，也不接受任何交互（如点击事件）。
   - **影响**：由于元素不在文档流中，其他元素会填充其原本的空间。

02. **visibility: hidden**
   

```css
   .hide {
       visibility: hidden;
   }
```

   - **特点**：元素被隐藏，但仍然占用原来的空间，不影响布局。
   - **影响**：虽然看不见元素，但元素仍存在于页面上，只是不可见，元素本身仍然可以接收到交互事件，只是用户无法看到交互反馈。

03. **opacity: 0**
   

```css
   .hide {
       opacity: 0;
   }
```

   - **特点**：通过降低元素的透明度使其不可见，但元素仍旧保留其尺寸和布局空间。
   - **影响**：元素仍然是交互的，用户可以触发hover、click等事件，因为元素实际并未从视图层消失，只是变得透明。

04. **position: absolute; left: -9999px; top: -9999px;**
   

```css
   .hide {
       position: absolute;
       left: -9999px;
       top: -9999px;
   }
```

   - **特点**：通过绝对定位将元素移动到屏幕视野之外，以此达到隐藏的目的。
   - **影响**：元素虽然在可视区域外，但仍存在于DOM中并占据一定的空间，但它对正常文档流的影响较小，且可以保持交互能力。

05. **height: 0; width: 0; overflow: hidden;**
   

```css
   .hide {
       height: 0;
       width: 0;
       overflow: hidden;
   }
```

   - **特点**：对于块级元素或行内块元素，将其高度和宽度设为0，并配合overflow属性隐藏溢出内容，可以有效隐藏元素。
   - **影响**：这会压缩元素自身到无可见大小，但如果元素内部还有内容，可能需要额外处理以确保内容也被隐藏。

每种方法都有其适用场景：
* **display: none** 常用于完全移除元素对页面布局和交互的影响，比如切换菜单项的可见性。
* **visibility: hidden** 适用于暂时隐藏元素但保持其所在空间不变，例如隐藏辅助信息，但仍需保持屏幕阅读器可访问。
* **opacity: 0** 当需要做淡入淡出动画或其他视觉特效时较为常用。
* **position 移动** 方法常用于需要保持元素在DOM中但暂时移出视线的情况，可能会对SEO造成一定影响，因为搜索引擎爬虫可能认为这种隐藏是有意为之。
* **调整尺寸** 方法适合于不需要元素内容但想保留元素结构的情况下隐藏，防止内容意外溢出。

### 如何实现单行/多行文本溢出的省略样式?

在CSS中，可以通过 `text-overflow` 属性与 `overflow` 属性结合来实现文本溢出时的省略样式。具体实现根据不同场景分为单行文本溢出省略和多行文本溢出省略。

### 单行文本溢出省略（ellipsis）

```css
.single-line-ellipsis {
    overflow: hidden;
    /* 隐藏超出部分 */
    white-space: nowrap;
    /* 禁止换行 */
    text-overflow: ellipsis;
    /* 显示省略号(...) */
}
```

使用示例：

```html
<p class="single-line-ellipsis">这是一个很长很长的句子，超过容器宽度就会显示省略号...</p>
```

### 多行文本溢出省略（CSS3）

CSS3新增了 `line-clamp` 属性，可以配合 `-webkit-line-clamp` （兼容Webkit内核浏览器）以及 `display: -webkit-box` 和 `-webkit-box-orient: vertical` 实现多行文本溢出省略：

```css
.multi-line-ellipsis {
    display: -webkit-box;
    /* 必须结合的属性，将对象作为弹性伸缩盒子模型显示 */
    -webkit-box-orient: vertical;
    /* 必须结合的属性，设置或检索伸缩盒对象的子元素的排列方式 */
    overflow: hidden;
    /* 隐藏超出的内容 */
    text-overflow: ellipsis;
    /* 显示省略号 */
    -webkit-line-clamp: 3;
    /* 设置显示的行数 */
    line-height: 1.5em;
    /* 为了计算总高度，假设每行的高度 */
    max-height: 4.5em;
    /* 总高度 = 行数 * 每行高度 */
}

/* 对非Webkit内核浏览器的模拟支持，例如Firefox */
.multi-line-ellipsis {
    display: -moz-box;
    -moz-box-orient: vertical;
    line-clamp: 3;
}

/* 注意：对于非Webkit内核浏览器，目前尚无标准方案，通常需要借助JS实现 */
```

使用示例：

```html
<p class="multi-line-ellipsis">这是一个很长很长的段落，超过指定的三行就会显示省略号...</p>
```

请注意， `-webkit-line-clamp` 是非标准的WebKit专有属性，IE及非WebKit的浏览器（如Firefox）并不支持。若要获得跨浏览器的多行文本省略效果，可能需要借助JavaScript或者伪元素模拟实现。

### css如何画一个三角形? 原理是什么?

在CSS中，最常见且简单的方法是通过边框（border）来创建一个三角形，其原理基于以下几点：

01. 创建一个空的HTML元素，比如`<div>`，并设置其尺寸为0。
02. 为这个元素设置一个较大的边框宽度（border-width）。
03. 将不需要显示的边框颜色设置为透明（transparent），而将需要构成三角形的边框颜色设置为可见的颜色。
04. 通过调整边框的宽度和颜色，只留下一个顶点相连的三条边，其他边不可见，这样就形成了一个三角形的视觉效果。

以下是具体的CSS代码示例，用于创建一个向下的等腰直角三角形：

```css
.triangle-down {
    width: 0;
    height: 0;
    border-style: solid;
    border-width: 0 10px 10px 10px;
    /* 上下左右边框宽度，上为0 */
    border-color: transparent transparent red transparent;
    /* 四个边框颜色，上边框透明，下边框红色 */
}
```

在这个例子中，元素本身没有实际内容区域（width和height都是0），但它的下边框形成了一个红色的等腰直角三角形。

原理说明：
* 由于元素本身没有内容区域，所有边框从中心点出发向外延伸。
* 当上下两边框宽度为0时，只有左右两个宽边框形成垂直线段。
* 设置其中一个宽边框颜色为背景色（这里是红色），另一个保持透明，这样只有红色的一边可见。
* 结果是呈现出了由两个相邻的垂直边框形成的等腰直角三角形。

除了这种方法，还可以利用 `linear-gradient` 、 `conic-gradient` 结合 `background-clip` 或者 `clip-path` 属性来创建三角形效果，以及通过 `transform: rotate()` 和 `overflow: hidden` 结合伪元素来间接创建三角形。不过，利用边框创建三角形是最直观且无需额外图形处理的一种方法。

### 如何使用css完成视差滚动效果?

CSS 视差滚动效果通常用来模拟3D立体空间中的深度感，使背景图像与前景内容以不同速度滚动，从而产生动态的视觉体验。要实现CSS视差滚动效果，可以通过多种技术和属性组合来达到目的，下面是一些基本的方法：

#### 方法1 - 使用 `background-attachment: fixed;`

**适用于单层背景图像**

这是最简单的一种视差效果，它可以使背景图像相对于视口固定位置，而非随内容滚动：

```css
.parallax-background {
    background-image: url('your-background-image.jpg');
    background-attachment: fixed;
    background-position: center;
    background-repeat: no-repeat;
    background-size: cover;
}
```

#### 方法2 - 利用 `transform: translateZ()` 或 `translate3d()`

**适用于多层背景或元素**

对于更复杂的多层视差效果，可以结合JavaScript监听滚动事件，然后动态改变各层元素的位置。例如：

```css
.parallax-layer {
    position: relative;
    z-index: 1;
    /* 可以调整层叠顺序 */
}

/* 第一层背景滚动慢 */
.first-layer {
    background-image: url('first-layer.jpg');
    height: 100vh;
    background-attachment: fixed;
    background-position: center;
    background-repeat: no-repeat;
    background-size: cover;
}

/* 第二层内容滚动快 */
.second-layer {
    position: absolute;
    top: 0;
    left: 0;
    right: 0;
    height: 100vh;
    transform: translateZ(-1px) scale(1);
    /* 调整translateZ的值控制视差程度 */
}

/* 更复杂的，使用JavaScript动态计算偏移量 */
.js-parallax-element {
    will-change: transform;
    transform: translateY(calc(var(--scroll-offset) * parallaxFactor));
    /* 这里的parallaxFactor是视差因子，可以根据滚动距离动态计算 */
}
```

JavaScript部分示例（假设使用IntersectionObserver API和Scroll Event监听滚动位置变化）：

```javascript
// 获取元素
const parallaxElement = document.querySelector('.js-parallax-element');

// 监听滚动事件
window.addEventListener('scroll', function() {
    const scrollPosition = window.pageYOffset || document.documentElement.scrollTop;
    const parallaxSpeed = 0.5; // 视差速度，可调整

    // 计算并应用位移
    const offset = scrollPosition * parallaxSpeed;
    parallaxElement.style.setProperty('--scroll-offset', offset + 'px');
});

// 或者使用IntersectionObserver配合ScrollTrigger库等高级方法
```

#### 方法3 - 使用CSS Grid或Flexbox布局配合动画属性

结合现代CSS布局和动画特性，也可以实现更为细腻的视差效果。例如，借助 `@keyframes` 定义动画并在滚动到特定位置时触发：

```css
.parallax-container {
    display: grid;
    /* 或 flex */
    overflow: auto;
}

.parallax-item {
    animation: parallaxEffect ease-in-out infinite;
    animation-play-state: paused;
}

.parallax-item.is-visible {
    animation-play-state: running;
}

@keyframes parallaxEffect {

    0%,
    100% {
        transform: translateY(0);
    }

    50% {
        transform: translateY(calc(var(--parallax-translate) * 10%));
        /* --parallax-translate是通过JavaScript动态设置的变量 */
    }
}
```

结合JavaScript判断元素是否进入视窗范围，并添加类名 `.is-visible` 来启动动画。

总之，视差滚动效果的具体实现取决于所需的复杂度和浏览器兼容性要求。简单的背景固定可以用纯CSS实现，而更复杂的效果往往需要配合JavaScript或其他动画库来增强用户体验。

### css3新增了哪些新特性?

CSS3作为对CSS规范的重要升级，引入了许多新特性和改进，以下列举了其中的一部分关键特性：

01. **选择器**：
   - `:nth-child(n)` 和 `:nth-of-type(n)` ：用于选取父元素下的第n个子元素或同类型的第n个子元素。
   - `:not(selector)` ：排除符合指定选择器的元素。
   - `:target` ：匹配URL片段标识符的目标元素。
   - 属性选择器 `[attribute=value]` ，以及更复杂的形式如 `[attr^=value]` （开头包含）、 `[attr$=value]` （结尾包含）、 `[attr*=value]` （包含）等。

02. **盒模型及边框**：
   - `border-radius` ：用于创建圆角边框。
   - `box-shadow` ：为元素添加阴影效果。
   - `border-image` ：使用图像作为边框样式。

03. **背景**：
   - 多重背景 ( `multiple backgrounds` )：允许在一个元素上设置多个背景图像。
   - 渐变背景 ( `linear-gradient` 和 `radial-gradient` )：创建线性渐变和径向渐变背景。

04. **变形与动画**：
   - `transform` ：包括旋转( `rotate` )、缩放( `scale` )、移动( `translate` )、倾斜( `skew` )等。
   - `transition` ：平滑过渡效果，可以为任何CSS属性添加过渡动画。
   - `animation` ：通过@keyframes创建复杂的动画序列。

05. **响应式设计**：
   - 媒体查询 ( `@media` )：根据设备特性（如屏幕尺寸、分辨率、方向等）应用不同的样式规则。

06. **文字效果**：
   - 文本阴影 ( `text-shadow` )：为文本添加阴影效果。
   - 文本修饰 ( `text-decoration-line` , `text-decoration-color` , `text-decoration-style` )：定制文本下划线、删除线等样式。
   - 字间距 ( `letter-spacing` ) 和单词间距 ( `word-spacing` )：控制字符或单词之间的间距。
   - 自定义字体加载 ( `@font-face` )：允许网页直接使用自定义字体。

07. **布局**：
   - 弹性盒模型 (Flexbox)：更灵活的容器布局模式。
   - 网格布局 (Grid Layout)：二维布局系统，用于创建复杂的网页布局。
   - 多列布局 ( `column-count` , `column-width` )：将内容分隔成多列显示。

08. **滤镜与特效**：
   - `filter` ：对元素应用各种图形效果，如模糊、灰度、色彩调整等。

09. **其他**：
   - 透明度 ( `opacity` )：设置元素的不透明度。
   - RGBa颜色模式：允许同时设置颜色和alpha通道（透明度）。

这些只是CSS3众多新特性中的一部分，随着时间的推移，CSS的标准还在持续演进和完善，不断有更多特性被加入进来。

### css3动画有哪些?

CSS3 提供了几种关键的技术来创建丰富的动画效果，主要分为两大类：过渡（Transitions）和动画（Animations）。以下是关于这两类动画技术及其相关特性的概述：

01. **过渡 (Transitions)**:
   - 过渡允许元素在不同样式之间平滑地改变。当元素的CSS属性值发生变化时，过渡效果会在一定时间段内自动填补两个状态之间的变化过程。
   - 关键属性：

     - `transition-property` ：指定要应用过渡效果的CSS属性。
     - `transition-duration` ：定义过渡效果持续的时间。
     - `transition-timing-function` ：控制过渡速度曲线，如 `ease` , `linear` , `ease-in` , `ease-out` , `ease-in-out` , 或 `cubic-bezier()` 函数自定义缓动效果。
     - `transition-delay` ：设置过渡开始前的延迟时间。

02. **动画 (@keyframes)**:
   - 使用 @keyframes 规则可以创建复杂的动画序列，定义一个动画从开始到结束的各个关键帧。
   - 创建动画的基本步骤：

     - 定义 @keyframes 规则，指定动画在不同阶段的样式变化。
     - 使用 `animation-name` 属性引用创建好的关键帧名称。
     - `animation-duration` ：动画总时长。
     - `animation-timing-function` ：同过渡一样，控制动画的速度曲线。
     - `animation-delay` ：动画开始之前的延迟时间。
     - `animation-iteration-count` ：动画循环次数，可以是具体数字、无限循环的 `infinite` 或其它值。
     - `animation-direction` ：控制动画是否反向播放，例如 `normal` （正向播放后停止）、 `reverse` （反向播放后停止）、 `alternate` （来回交替播放）等。
     - `animation-fill-mode` ：决定动画结束后元素的状态，如 `none` （回到初始状态）、 `forwards` （保持最后一帧样式）、 `backwards` （保持第一帧样式）、 `both` （向前和向后都保持相应状态）。

结合上述属性，开发者可以通过CSS3轻松实现元素的平移、旋转、缩放、淡入淡出、形状变换等各种动画效果。此外，还有诸如CSS Filters、Transforms等属性也常与动画配合使用，创造出更加丰富多样的视觉体验。

### 介绍一下grid网格布局

CSS Grid Layout（简称Grid布局）是一种先进的二维布局系统，由W3C制定并在现代浏览器中广泛支持。Grid布局彻底改变了前端开发人员设计复杂网页布局的方式，特别是那些需要精确控制多个元素在水平和垂直方向排列的应用场景。

**核心概念：**

01. **网格容器(Grid Container)**：通过将一个元素的 `display` 属性设置为 `grid` 或 `inline-grid`，使其成为一个网格容器。这意味着它的直接子元素将按照网格布局规则排列。

02. **网格轨道(Grid Tracks)**：网格由行（Rows）和列（Columns）组成，称为网格轨道。开发者可以定义每行和每列的大小，以及它们如何动态调整。

03. **网格线(Grid Lines)**：网格是由行线和列线划分出来的，这些线是虚拟的，但可以帮助我们定位网格项。

04. **网格单元格(Grid Cells)**：两根相邻的行线和两根相邻的列线交叉形成的区域即为一个网格单元格。

05. **网格区域(Grid Areas)**：可以将多个单元格合并起来定义成一个区域，这样就可以方便地放置和命名特定的布局区块。

06. **网格项(Grid Items)**：网格容器内的直接子元素被视为网格项，它们可以根据需要被放置在网格的特定位置或者扩展到多个单元格。

**主要CSS属性：**

* `grid-template-columns` 和 `grid-template-rows`：定义网格的列和行的具体尺寸。
* `grid-template-areas`：通过名称来指定每个网格区域的位置。
* `grid-column` 和 `grid-row`：用于指定网格项在网格中的位置，可以使用线编号或者跨度（span）。
* `grid-auto-flow`：控制网格项在没有明确定位时的自动布局方式。
* `justify-items` 和 `align-items`：定义网格项在其单元格内沿行轴和列轴的对齐方式。
* `justify-content` 和 `align-content`：用于调整整个网格行或列的对齐方式。

借助CSS Grid Layout，开发者可以创建响应式、灵活的布局，轻松应对各种屏幕尺寸和方向的变化，从而实现过去仅能通过复杂定位和浮动才能完成的布局设计。

### 说说flexbox(弹性盒布局模型), 以及适用场景?

Flexbox（Flexible Box Layout Module，弹性盒布局模型）是CSS3中引入的一种强大的布局模式，它旨在提供一个更加灵活和适应性强的布局系统，尤其适用于处理复杂的网页布局和组件对齐问题。相较于传统的布局方式，如浮动（float）和定位（positioning），Flexbox能够更好地处理响应式设计和未知内容尺寸的场景。

**核心概念与特性：**

01. **容器（Container）**：通过将一个元素的 `display` 属性设置为 `flex` 或 `inline-flex`，使其成为弹性容器（flex container）。

02. **主轴与交叉轴（Main Axis & Cross Axis）**：在弹性容器内，有一个主要的布局方向（主轴），与其垂直的方向称为交叉轴。容器的 `flex-direction` 属性决定了主轴的方向（row或column）。

03. **弹性项（Items）**：弹性容器内的直接子元素就是弹性项（flex items），它们在容器内可以自由调整自身的尺寸和位置。

04. **弹性布局属性**：
   - `flex-wrap` ：决定当容器空间不足时，弹性项是否换行（nowrap、wrap、wrap-reverse）。
   - `justify-content` ：沿着主轴对齐弹性项（flex-start、flex-end、center、space-between、space-around、space-evenly）。
   - `align-items` ：沿着交叉轴对齐弹性项（类似的对齐选项）。
   - `align-content` ：在有多行的情况下，控制行间的间距和对齐（仅在 `flex-wrap: wrap` 时生效）。

05. **弹性项属性**：
   - `flex-grow` ：决定弹性项在有剩余空间时的增长比例。
   - `flex-shrink` ：决定弹性项在空间不足时的收缩比例。
   - `flex-basis` ：弹性项在分配空间之前的基本尺寸。
   - `align-self` ：允许单个弹性项覆盖对其在交叉轴上的对齐方式。

**适用场景：**

* **响应式布局**：Flexbox非常适合构建自适应布局，尤其是在不同屏幕尺寸下需要快速调整布局方向或间距的情况。
* **等高布局**：通过合理的`align-items`设置，可以让同一行内的弹性项拥有相同的高度，从而实现简洁的等高布局。
* **居中对齐**：无论是水平还是垂直居中对齐，Flexbox都能轻松实现，解决了传统CSS布局中居中对齐的难题。
* **未知内容尺寸**：当容器内子元素的尺寸不确定时，Flexbox能够很好地适应内容变化，自动调整布局。
* **组件和UI布局**：在构建复杂数字产品或应用程序时，Flexbox对于布局按钮组、卡片、列表等组件非常有用。

总的来说，Flexbox极大地提高了CSS布局的灵活性和可控性，使得开发者能够更高效地创建适应性强、表现力丰富的网页布局。

### 说说设备像素.css像素、设备独立像素、dpr.ppi之间的区别?

**设备像素（Physical Pixel）**：
* 设备像素是显示器硬件上的最小物理显示单元，每个设备像素由红绿蓝子像素组成，共同构成了屏幕图像。设备像素的数量和分布决定了屏幕的分辨率，例如，一台分辨率为1920x1080的显示器上有1920个横向和1080个纵向的设备像素。

**CSS像素（CSS Pixel）/设备独立像素（Device Independent Pixel/DIP）**：
* CSS像素是浏览器使用的抽象单位，用于在CSS和JavaScript中定义布局尺寸和坐标。CSS像素不直接对应设备像素，而是浏览器根据设备特性、用户的缩放级别等因素自行处理的一个虚拟单位。在标准的设备上，一个CSS像素可能对应一个设备像素；但在高分辨率显示屏上，为了保持视觉尺寸一致，一个CSS像素可能对应多个设备像素。

**设备像素比（Device Pixel Ratio, DPR）**：
* DPR表示设备像素与CSS像素的比例关系，即一个CSS像素所代表的设备像素数量。例如，DPR为2的设备上，浏览器将一个CSS像素渲染为4个设备像素（2x2），以提高显示质量。可以通过JavaScript的`window.devicePixelRatio`获取当前设备的DPR值。

**每英寸像素数（Pixels Per Inch, PPI）**：
* PPI描述的是设备屏幕上每英寸所能容纳的像素数量，也就是屏幕的像素密度。PPI值越高，屏幕显示的图像就越精细，人眼观感也就越细腻。例如，iPhone X的Retina显示屏PPI非常高，使得在正常观看距离下，人眼难以察觉单个像素的存在。

总结来说，设备像素是屏幕物理构造的基础，CSS像素是网页开发中使用的抽象单位，设备像素比用来调节CSS像素与设备像素的关系，而每英寸像素数反映的是屏幕的细腻程度。在响应式设计和高分辨率设备的支持中，理解这些概念有助于正确处理不同设备上的布局和显示效果。

### 说说em/px/rem/vh/vw区别?

**em、px、rem、vh、vw** 是 CSS 中常用的长度单位，它们在布局和尺寸定义方面有着不同的用途和行为：

01. **px (像素, Pixels)**：
   - 绝对单位，直接对应屏幕上的物理像素点（但在高DPI设备上，一个CSS像素可能映射到多个设备像素）。
   - 不会随父元素字体大小的改变而变化。

02. **em**：
   - 相对单位，基于当前元素的字体大小。
   - 如果一个元素的 `font-size` 设置为 `16px` ，那么 `1em` 就等于 `16px` 。如果在该元素内嵌套的子元素设置了 `font-size: 0.8em` ，那么子元素的字体大小将是 `12.8px` （16 * 0.8）。
   - 除了应用于字体大小外，em单位也可用于设置元素的宽度、高度和内外边距等尺寸，这时它的值会根据父元素的字体大小进行相对计算。

03. **rem (根em, Root em)**：
   - 也是相对单位，但其参照点是根元素（通常是 `<html>` 元素）的字体大小。
   - 如果根元素的 `font-size` 设置为 `16px` ，那么不论在哪个元素中， `1rem` 都始终等于 `16px` 。
   - 使用rem单位便于在整个页面范围内实现统一的相对单位计算和响应式设计。

04. **vh/vw (视口高度/宽度, Viewport Height/Width)**：
   - 相对于视口（Viewport）的百分比单位。
   - `1vh` 等于视口高度的1%， `1vw` 等于视口宽度的1%。
   - 这些单位非常适用于创建响应式布局，因为它们会随着浏览器窗口大小的变化而自动调整元素的尺寸。

总结：
* `px` 用于设定固定的尺寸，不受字号或视口大小影响。
* `em` 用于根据父元素字体大小动态调整尺寸，适用于局部的相对布局和字体大小调整。
* `rem` 用于全局范围的相对布局和字体大小调整，不受父元素影响，只基于根元素字体大小。
* `vh` 和 `vw` 用于根据浏览器视口大小调整元素尺寸，特别适合制作全屏布局和响应式设计。

### 让Chrome支持小于12px的文字方式有哪些? 区别?

在早期的中文版Chrome浏览器中，默认情况下，出于易读性和用户界面设计考虑，对于中文字体设置了最小字号限制为12px。不过，现代浏览器已经不再强制执行这一限制，您可以使用任意大小的字号。但针对旧版本的Chrome或特殊情况，有几种方式可以尝试让Chrome支持小于12px的文字：

01. **使用transform: scale()**：
   - 通过CSS3的 `transform` 属性缩小字体，例如：

     

```css
     .small-font {
         font-size: 10px;
         transform: scale(0.833333);
         /* 将10px转换为相当于12px的80% */
     }
```

   - 这种方式可以减小文字的实际显示尺寸，但要注意它会同时缩放文字的所有维度，可能会影响到布局的精确性。

02. **修改系统字体设置**：
   - 用户可在Chrome的设置中修改字体大小，但这不会直接影响到网页中固定字号的CSS样式。

03. **使用`-webkit-text-size-adjust`**：
   - 这个属性用于控制网页内文本的缩放，但对中文和小于12px字号的支持有限。

04. **使用`zoom`属性**：
   - 通过给包含小字号文本的容器设置zoom值来整体缩放内容，但同样会影响整个容器内的所有内容。

05. **CSS3的`font-variant`属性**：
   - 通过启用 `font-variant: small-caps;` 可以得到看起来较小的字体效果，但这并不是真正意义上的减小字号，而是将小写字母转化为大写字母的小型形式。

06. **针对老版本Chrome的解决方案**：
   - 对于曾经存在的最小字号限制问题，如今大部分情况下已经不再是问题，因为Chrome后来取消了这个限制。然而，如果是早先版本，可能需要通过JavaScript动态计算并应用transform样式，或者通过SVG等替代方案展示小字号文本。

实际上，现在的最佳实践是直接设置所需的小于12px的字号，大多数现代浏览器应该能够良好支持。如果遇到兼容性问题，可以优先考虑采用transform或其他布局技术来实现类似效果。

### 怎么理解回流跟重绘? 什么场景下会触发?

回流（Reflow）和重绘（Repaint）是Web浏览器渲染过程中两个关键的概念，它们涉及到浏览器如何更新页面布局和视觉表现。

**回流 (Reflow)：**
回流也称为布局或重排，是指当页面中的元素几何属性（如宽度、高度、位置）发生变化，或者DOM结构发生变动（比如添加、删除元素）时，浏览器需要重新计算元素的几何信息以及其子元素乃至整个文档中相关联元素的几何信息。这个过程包括计算元素的新布局、确认元素及其子孙元素的位置和尺寸。回流通常成本较高，因为它可能导致整个或部分渲染树的重新计算布局。

**重绘 (Repaint)：**
重绘则是指在元素的样式发生改变，但不影响元素尺寸和位置的情况下，浏览器仅需要更新元素的视觉表现，比如背景色、边框颜色、文字颜色等非几何属性的变更。相比于回流，重绘的性能开销较小，因为它不需要重新计算布局，仅仅涉及到了元素的样式更新和重新绘制。

**触发场景：**
* **回流会触发的情况：**
  + 添加或删除可见的DOM元素；
  + 元素尺寸（width、height）或位置（top, bottom, left, right）的改变；
  + 内容变化导致元素尺寸变化（例如，文本内容增加，图片加载完成）；
  + 浏览器窗口大小的变化（窗口resize事件）；
  + 获取某些影响布局的样式属性值，如offsetTop、offsetWidth等。

* **重绘会触发的情况：**
  + 改变元素的颜色、背景色、字体样式等不影响布局的样式属性；
  + 设置透明度、visibility等不改变布局但影响视觉效果的属性；
  + CSS伪类的切换（例如:hover效果）。

为了提高页面性能，应当尽量减少不必要的回流和重绘，常见的优化方法包括：
* 避免频繁修改DOM结构；
* 批量修改样式，而不是连续多次修改；
* 使用CSS3硬件加速特性，如transform和opacity；
* 对不在视窗内的元素做更改时，可以考虑使用 `requestAnimationFrame` 或 `Intersection Observer API` 确保只在元素可视时进行渲染操作；
* 将复杂的动画或大量 DOM 变动放在 `position: fixed` 或 `position: absolute` 定位的层中，这样局部的回流不会影响到文档流中的其他元素。

### 说说对css预编语言的理解? 有哪些区别?

CSS 预编译语言是一种扩展了原生CSS能力的编程语言，允许开发者使用变量、嵌套规则、循环、函数等编程概念来编写更强大、更模块化和更易于维护的样式表。这些语言经过编译后会转换成常规的CSS文件，从而被浏览器识别并应用到网页上。CSS预编译语言的主要优点在于增强了CSS的表达能力和组织结构，降低了样式代码的冗余，并且提高了代码复用性和可维护性。

以下是几种主流的CSS预编译语言及其区别：

01. **Sass (Syntactically Awesome Style Sheets)**:
   - 创建于2007年，是最古老的预编译语言之一。
   - 分为两种语法：原始的 `.sass` （缩进语法，类似Haml的简洁风格）和后来推出的 `.scss` （SCSS语法，完全符合CSS语法，采用花括号和分号）。
   - 提供变量、嵌套、混入（mixins）、继承、运算符、函数等功能。
   - 原始版本依赖Ruby环境，但SCSS现在也可以通过Node.js环境编译。

02. **Less (Leaner Style Sheets)**:
   - 也是一种CSS扩展语言，它同样是CSS的超集，即所有有效的CSS都是有效的Less代码。
   - 使用类似于CSS的语法，更容易上手。
   - 引入了变量、嵌套规则、混合、运算符和函数等特性。
   - 通过JavaScript编译引擎运行，可以轻松集成到前端构建流程中。

03. **Stylus**:
   - 相较于前两者，Stylus具有更灵活的语法，比如可以省略分号和花括号。
   - 同样支持变量、嵌套、混入、函数等，还提供了条件语句和循环等更为丰富的编程功能。
   - 编译器支持多种语言实现，如Node.js、Java等。

区别方面：
* **语法差异**：每种预编译语言都有其特定的语法，尽管在功能上大致相似，但在具体书写风格上有所不同，比如Sass有简洁和CSS-like两种语法选择，而Less和Stylus更接近CSS。
* **社区和生态系统**：虽然三种语言都有一定的用户群体，但Sass得益于早期起步和Ruby社区支持，长期积累了很多实用的框架和工具，比如Compass。
* **编译器和依赖**：不同的预编译语言可能有不同的编译环境需求，比如Sass早期依赖Ruby环境，而Less和Stylus则倾向于JavaScript环境，这会影响到项目构建工具的选择和集成方案。

总的来说，选择哪一种预编译语言取决于个人偏好、团队规范和项目需求。随着CSS发展，一些原本只能在预编译语言中实现的功能（如变量、嵌套等）逐渐被CSS自身吸收（例如CSS Custom Properties），但预编译语言依然因其强大的抽象和组织能力，在大型项目和复杂样式管理中发挥重要作用。

### 如果要做优化, css提高性能的方法有哪些?

提高CSS性能的方法主要包括减少不必要的渲染重绘与回流、优化选择器效率、合理组织和加载CSS资源、减少CSS计算负担等方面。以下是一些具体的优化策略：

01. **减少重绘和回流**：
   - 避免不必要的DOM修改，尤其是涉及布局信息的属性更改（如 `width` 、 `height` 、 `padding` 、 `margin` 、 `display` 等）。
   - 使用CSS3 `transform` 和 `opacity` 属性进行动画，因为它们通常可以在合成器层中处理，减少对布局和绘制的影响。
   - 使用批处理DOM操作，如使用 `requestAnimationFrame` 或微任务来推迟修改。

02. **优化选择器**：
   - 减少过于复杂的选择器，尤其是后代选择器和属性选择器，它们的匹配性能较低。
   - 优先使用类选择器，避免过度使用ID选择器和标签选择器。
   - 尽可能减少选择器的嵌套层数。

03. **合并和压缩CSS**：
   - 将多个CSS文件合并成一个或几个，减少HTTP请求次数。
   - 使用CSS压缩工具（如CSSNano、CleanCSS等）压缩CSS代码，移除注释、空白字符和不必要的代码。

04. **利用媒体查询按需加载**：
   - 使用媒体查询根据设备特征加载不同CSS，减少不必要的加载和解析。

05. **提取关键CSS**：
   - 将页面初始渲染所需的关键CSS提取出来，放到HTML头部通过 `<style>` 标签内联或使用 `<link rel="preload">` 提前加载，以便页面更快渲染。

06. **CSS Sprites与图标字体**：
   - 使用CSS Sprites合并多个小图标，减少HTTP请求。
   - 使用图标字体（如Font Awesome）代替多个图片，同样可以减少HTTP请求和提高渲染效率。

07. **CSS3新技术**：
   - 使用Flexbox或Grid布局取代传统的表格布局和浮动布局，简化布局逻辑并提高渲染性能。
   - 使用CSS Variables（CSS自定义属性）简化样式管理和代码复用。

08. **避免CSS表达式**：
   - 不使用CSS表达式，它们会频繁触发重绘和回流。

09. **开启GZIP压缩**：
   - 服务器端配置开启GZIP压缩，减小CSS文件在网络传输过程中的大小。

10. **合理设置`box-sizing`属性**：
    - 使用`box-sizing: border-box;`可以简化布局计算，防止因内边距和边框引发的布局计算错误和频繁的回流。

11. **懒加载未视区内容的CSS**：
    - 对于未视区的内容，可以使用Intersection Observer API延迟加载对应的CSS资源。

通过以上方法的综合应用，可以显著提升CSS的性能和网站的整体加载速度。
