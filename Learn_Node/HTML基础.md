# HTML基础 

## 一、认识WEB 

**「网页」**主要是由文字、图像和超链接等元素构成，当然除了这些元素，网页中还可以包括音频、视频以及Flash等。

**「浏览器」**是网页显示、运行的平台。

**「浏览器内核」**(排版引擎、解释引擎、渲染引擎)

> 负责读取网页内容，整理讯息，计算网页的显示方式并显示页面。

| 浏览器  | 内核           | 备注                                                         |
| ------- | -------------- | ------------------------------------------------------------ |
| IE      | Trident        | IE、猎豹安全、360极速浏览器、百度浏览器                      |
| firefox | Gecko          | 可惜这几年已经没落了，打开速度慢、升级频繁、猪一样的队友flash、神一样的对手chrome。 |
| Safari  | webkit         | 现在很多人错误地把 webkit 叫做 chrome内核（即使 chrome内核已经是 blink 了）。苹果感觉像被别人抢了媳妇，都哭晕在厕所里面了。 |
| chrome  | Chromium/Blink | 在 Chromium 项目中研发 Blink 渲染引擎（即浏览器核心），内置于 Chrome 浏览器之中。Blink 其实是 WebKit 的分支。大部分国产浏览器最新版都采用Blink内核进行二次开发 |
| Opera   | blink          | 现在跟随chrome用blink内核。                                  |

### Web标准

**「构成」** **结构标准，表现标准和行为标准**

-   结构标准：用于对网页元素进行整理和分类(HTML)
-   表现标准：用于设置网页元素的版式、颜色、大小等外观属性(CSS)
-   行为标准：用于对网页模型的定义及交互的编写(JavaScript)

**「Web标准的优点」**

-   易于维护：只需更改CSS文件，就可以改变整站的样式
-   页面响应快：HTML文档体积变小，响应时间短
-   可访问性：语义化的HTML（结构和表现相分离的HTML）编写的网页文件，更容易被屏幕阅读器识别
-   设备兼容性：不同的样式表可以让网页在不同的设备上呈现不同的样式
-   搜索引擎：语义化的HTML能更容易被搜索引擎解析，提升排名

* * * * *

## 二、HTML初识 

### HTML初识

**「HTML」**(Hyper Text Markup Language)：超文本标记语言

**「所谓超文本，有2层含义：」**

-   因为它可以加入图片、声音、动画、多媒体等内容（超越文本限制 ）
-   不仅如此，它还可以从一个文件跳转到另一个文件，与世界各地主机的文件连接（超级链接文本）。

**「HTML骨架格式」**

``` html
<!-- 页面中最大的标签 根标签 -->
<html>
<!-- 头部标签 -->
<head>
    <!-- 标题标签 -->
    <title></title>
</head>
<!-- 文档的主体 -->
<body>
</body>
</html>
```

**「团队约定大小写」**

-   HTML标签名、类名、标签属性和大部分属性值统一用小写

**「HTML元素标签分类」**

-   常规元素(双标签)
-   空元素(单标签)

``` html
常规元素(双标签)  
<标签名> 内容 </标签名>   比如<body>我是文字</body>  
空元素(单标签)  
<标签名 />  比如 <br />或<br>
```

**「HTML标签关系」**

嵌套关系父子级包含关系

并列关系兄弟级并列关系

-   如果两个标签之间的关系是嵌套关系，子元素最好缩进一个tab键的身位（一个tab是4个空格）。如果是并列关系，最好上下对齐。

### 文档类型\<!DOCTYPE  >

文档类型声明标签：用来说明你用的XHTML或者HTML是什么版本。\<!DOCTYPE
html\>告诉浏览器按照HTML5标准解析页面。不属于HTML标签。

### 页面语言lang

lang指定该html标签内容所用的语言，language的缩写。

``` html
<html lang="en">    
en 定义语言为英语 zh-CN定义语言为中文
```

**「lang的作用」**

-   根据根据lang属性来设定不同语言的css样式，或者字体
-   告诉搜索引擎做精确的识别
-   让语法检查程序做语言识别
-   帮助翻译工具做识别
-   帮助网页阅读程序做识别

### 字符集

**「字符集」**(Character set)是多个字符的集合，计算机要准确的处理各种字符集文字，需要进行字符编码，以便计算机能够识别和存储各种文字。

-   UTF-8是目前最常用的字符集编码方式
-   让 html 文件是以 UTF-8 编码保存的，浏览器根据编码去解码对应的html内容。

``` html
<meta charset="UTF-8" />
```

**「meta viewport的用法」**
通常viewport是指视窗、视口。浏览器上（也可能是一个app中的webview）用来显示网页的那部分区域。在移动端和pc端视口是不同的，pc端的视口是浏览器窗口区域，而在移动端有三个不同的视口概念：布局视口、视觉视口、理想视口

meta有两个属性name 和 http-equiv

**name属性的取值**

-   keywords(关键字) 告诉搜索引擎，该网页的关键字
-   description(网站内容描述) 用于告诉搜索引擎，你网站的主要内容。
-   viewport(移动端的窗口)
-   robots(定义搜索引擎爬虫的索引方式)
    robots用来告诉爬虫哪些页面需要索引，哪些页面不需要索引
-   author(作者)
-   generator(网页制作软件）
-   copyright(版权)

**http-equiv有以下参数**

http-equiv相当于http的文件头作用，它可以向浏览器传回一些有用的信息，以帮助正确和精确地显示网页内容

-   content-Type：设定网页字符集(HTML4用法，不推荐)。
-   Expires(期限)：可以用于设定网页的到期时间。一旦网页过期，必须到服务器上重新传输。
-   Pragma(cache模式)：是用于设定禁止浏览器从本地机的缓存中调阅页面内容，设定后一旦离开网页就无法从Cache中再调出。
-   Refresh(刷新)：自动刷新并指向新页面。
-   cache-control：请求和响应遵循的缓存机制。

``` html
<meta name="viewport" content="width=device-width, initial-scale=1.0">
```

### HTML标签的语义化

-   方便代码的阅读和维护，样式丢失的时候能让页面呈现清晰的结构。
-   有利于SEO，搜索引擎根据标签来确定上下文和各个关键字的权重。
-   方便其他设备解析，如盲人阅读器根据语义渲染网页

**「拓展」** 标签：规定页面上所有链接的默认 URL 和设置整体链接的打开状态

``` html
<head>
    <base href="http://www.baidu.com" target="_blank">
    <base target="_self">
</head>
<body>
    <a href="">测试</a> 跳转到 百度
</body>
```

* * * * *

## 三、HTML常用标签

### 1. 排版标签

主要和css搭配使用，显示网页结构的标签，是网页布局最常用的标签。

- 标题标签h(h1\~h6)

  加了标题标签的文字会加粗，字号也会依次变大，一个标题独占一行。

- 段落标签p,可以把 HTML 文档分割为若干段落

- 水平线标签hr：\<hr />，单标签

- 换行标签br：\<br />，单标签

-   div和span标签：是没有语义的，是我们网页布局最主要的2个盒子。

### 2. 排版标签

-   b 和 strong 文字以粗体显示
-   i 和 em 文字以斜体显示
-   s 和 del 文字以加删除线显示
-   u 和 ins 文字以加下划线显示

### 3. 标签属性(行内式)

使用HTML制作网页时，如果想让HTML标签提供更多的信息，可以使用HTML标签的属性加以设置。

``` html
<标签名 属性1="属性值1" 属性2="属性值2" …> 内容 </标签名>
<手机 颜色="红色" 大小="5寸">  </手机>
```

### 4. 图像标签img

| 属性   | 属性值                       | 描述                               |
| ------ | ---------------------------- | ---------------------------------- |
| src    | URL                          | 图像的路径                         |
| alt    | 文本                         | 替换文本，图形不能显示时的替换文本 |
| title  | 文本                         | 提示文本，鼠标悬停时显示的内容     |
| width  | 像素(XHTML不支持%页面百分比) | 设置图像的宽度                     |
| height | 像素(XHTML不支持%页面百分比) | 设置图像的高度                     |
| border | 数字(HTML5已弃用)            | 设置图像表框的宽度                 |

**注意：**

-   标签可以拥有多个属性，必须写在开始标签中，位于标签名后面。
-   属性之间不分先后顺序，标签名与属性、属性与属性之间均以空格分开。
-   采取  键值对 的格式   key="value"  的格式

``` html
<img src="cz.jpg" width="300" height="300" border="3" title="这是个小蒲公英" />
```

### 5. 链接标签(重点)

``` html
<a href="跳转目标" target="目标窗口的弹出方式">文本或图像</a>
target="_self"  默认窗口弹出方式
target="_blank" 新窗口弹出
```

| 属性   | 作用                                                         |
| ------ | ------------------------------------------------------------ |
| href   | 用于指定链接目标的url地址，（必须属性）当为标签应用href属性时，它就具有了超链接的功能 |
| target | 用于指定链接页面的打开方式，其取值有\_self和\_blank两种，其中\_self为默认值，_blank为在新窗口中打开方式。 |

*****

#### src 和 href 的区别

一句话概括：**src 是引入资源的，href 是跳转url的**。

1.  src用于替换当前元素，href用于在当前文档和引用资源之间确立联系。
2.  src是source的缩写，指向外部资源的位置，指向的内容将会嵌入到文档中当前标签所在位置；在请求src资源时会将其指向的资源下载并应用到文档内，例如js脚本，img图片和frame等元素。当浏览器解析到该元素时，会暂停其他资源的下载和处理，直到将该资源加载、编译、执行完毕，图片和框架等元素也如此，类似于将所指向资源嵌入当前标签内。这也是为什么将js脚本放在底部而不是头部。
3.  href是Hypertext Reference的缩写，指向网络资源所在位置，建立和当前元素（锚点）或当前文档（链接）之间的链接。如果我们在文档中添加那么浏览器会识别该文档为css文件，就会并行下载资源并且不会停止对当前文档的处理。这也是为什么建议使用link方式来加载css，而不是使用@import方式。

**注意：**

1.  外部链接，需要添加 http:// www.baidu.com。
2.  内部链接 直接链接内部页面名称即可 比如 \< a href="index.html"\> 首页
3.  如果当时没有确定链接目标时，通常将链接标签的href属性值定义为“\#”(即href="\#")，表示该链接暂时为一个空链接。
4.  不仅可以创建文本超链接，在网页中各种网页元素，如图像、表格、音频、视频等都可以添加超链接。

#### 锚点连接

**锚点定位：通过创建锚点链接，用户能够快速定位到目标内容。**

``` html
1. 使用相应的id名标注跳转目标的位置。 (找目标)
  <h3 id="two">第2集</h3>
2. 使用<a href="#id名">链接文本</a>创建链接文本（被点击的） 
  <a href="#two">
```

### 6. 注释标签

``` html
 <!-- 注释语句 -->     
  快捷键是：    ctrl + /
  或者 ctrl +shift + /
```

**团队约定：**注释内容前后各一个空格字符，注释位于要注释代码的上面，单独占一行

### 7. 路径

| 路径分类   | 符号  | 说明                                                         |
| ---------- | ----- | ------------------------------------------------------------ |
| 同一级路径 |       | 只需输入图像文件的名称即可，如\<img src="baidu.gif"/>        |
| 下一级路径 | "/"   | 图像文件位于HTML文件同级文件夹下，如\<img src="images/baidu.gif"/> |
| 上一级路径 | "../" | 在文件名之前加入"../"，如果是上两级，则需要使用"../../"，以此类推。如\<img src="../baidu.gif"/> |

### 8. 其他知识

**预格式化文本pre标签** 元素中的文本通常会保留空格和换行符。而文本也会呈现为等宽字体。格式化文本就是，按照我们预先写好的文字格式来显示页面， 保留空格和换行等。

**特殊字符**

HTML为这些特殊字符准备了专门的替换代码

| 特殊字符     | 描述          | 字符的代码 |
| ------------ | ------------- | ---------- |
|              | 空格          | \&nbsp;    |
| <            | 小于号        | \&lt;      |
| >            |               | \&gt;      |
| &            | 和号          | \&amp;     |
| ￥           | 人民币        | \&yen;     |
| ©            | 版权          | \&copy;    |
| ®            | 注册商标      | \&reg;     |
| °            | 摄氏度        | \&deg;     |
| ±            | 正负号        | \&plusmn;  |
| ×            | 乘号          | \&times;   |
| ÷            | 除号          | \&divide;  |
| <sup>2</sup> | 平方（上标2） | \&sup2;    |
| <sup>3</sup> | 立方（上标3） | \&sup3;    |

### 9. XHTML

-   XHTML 指**「可扩展超文本标签语言」**（EXtensible HyperText Markup
    Language）。
-   XHTML 的目标是取代 HTML。
-   XHTML 与 HTML 4.01 几乎是相同的。
-   XHTML 是更严格更纯净的 HTML 版本。
-   XHTML 是作为一种 XML 应用被重新定义的HTML,是严格版本的HTML。例如它要求标签必须小写，标签必须被正确关闭，标签顺序必须正确排列，对于属性都必须使用双引号等。
-   XHTML 是一个 W3C 标准。

**写HTML代码时应注意什么？**

-   尽可能少的使用无语义的标签div和span；
-   在语义不明显时，既可以使用div或者p时，尽量用p，因为p在默认情况下有上下间距，对兼容特殊终端有利；
-   不要使用纯样式标签，如：b、font、u等，改用css设置。
-   需要强调的文本，可以包含在strong或者em标签中（浏览器预设样式，能用CSS指定就不用他们），strong默认样式是加粗（不要用b），em是斜体（不用i）；
-   使用表格时，标题要用caption，表头用thead，主体部分用tbody包围，尾部用tfoot包围。表头和一般单元格要区分开，表头用th，单元格用td；
-   表单域要用fieldset标签包起来，并用legend标签说明表单的用途；
-   每个input标签对应的说明文本都需要使用label标签，并且通过为input设置id属性，在lable标签中设置for来让说明文本和相对应的input关联起来。

* * * * *

## 四、表格

现在还是较为常用的一种标签，但不是用来布局，常见显示、展示表格式数据。因为它可以让数据显示的非常的规整，可读性非常好。特别是后台展示数据的时候表格运用是否熟练就显得很重要，一个清爽简约的表格能够把繁杂的数据表现得很有条理。

### 1. 创建表格

``` html
<table>
  <tr>
    <td>单元格内的文字</td>
    ...
  </tr>
  ...
</table>
```

table、tr、td，他们是创建表格的基本标签，缺一不可

-   table用于定义一个表格标签。
-   tr标签 用于定义表格中的行，必须嵌套在 table标签中。
-   td 用于定义表格中的单元格，必须嵌套在\<tr\>\</tr\>标签中。
-   字母 td 指表格数据（table data），即数据单元格的内容，现在我们明白，表格最合适的地方就是用来存储数据的。td像一个容器，可以容纳所有的元素。
-   table：最外层的大盒子；tr，代表一行；td，代表一个单元格。

**表头单元格标签th**：一般表头单元格位于表格的第一行或第一列，并且文本加粗居中,只需用表头标签\<th\>\</th\>替代相应的单元格标签\<td\>\</td\>即可。

**表格标题caption**：通常这个标题会被居中且显示于表格之上。caption标签必须紧随 table 标签之后。这个标签只存在表格里面才有意义。

``` html
<table>
   <caption>我是表格标题</caption>
</table>
```

### 2. 表格属性

| 属性名      | 含义                                     | 常用属性值          |
| ----------- | ---------------------------------------- | ------------------- |
| border      | 设置表格的边框(默认border="0"无边框)     | 像素值              |
| cellspacing | 设置单元格与单元格边框之间的空白间距     | 像素值(默认为2像素) |
| cellpadding | 设置单元格内容与单元格边框之间的空白间距 | 像素值(默认为1像素) |
| width       | 设置表格的宽度                           | 像素值              |
| height      | 设置表格的高度                           | 像素值              |
| align       | 设置表格在网页中的水平对齐方式           | left,center,right   |

三参为0，平时开发的我们这三个参数border  cellpadding  cellspacing  为  0

### 3. 合并单元格

合并的顺序我们按照   先上 后下   先左  后右的顺序 ，合并完之后需要删除多余的单元格。

-   跨行合并：rowspan="合并单元格的个数"
-   跨列合并：colspan="合并单元格的个数"

### 4. 总结表格

| 标签名                | 定义           | 说明                                         |
| :-------------------- | :------------- | :------------------------------------------- |
| \<table>\</table>     | 表格标签       | 就是一个四方的盒子                           |
| \<tr>\</tr>           | 表格行标签     | 行标签要再table标签内部才有意义              |
| \<td>\</td>           | 单元格标签     | 单元格标签是个容器级元素，可以放任何东西     |
| \<th>\</th>           | 表头单元格标签 | 它还是一个单元格，但是里面的文字会居中且加粗 |
| \<caption>\</caption> | 表格标题标签   | 表格的标题，跟着表格一起走，和表格居中对齐   |
| clospan 和 rowspan    | 合并属性       | 用来合并单元格的                             |

### 5. 表格划分结构

    对于比较复杂的表格，表格的结构也就相对的复杂了，所以又将表格分割成三个部分：题头、正文和脚注。而这三部分分别用:thead,tbody,tfoot来标注，这样更好的分清表格结构。

**注意：**

1. \<thead\>\</thead\>：用于定义表格的头部。用来放标题之类的东西。\<thead\>内部必须拥有\<tr\> 标签！

2. \<tbody\>\</tbody\>：用于定义表格的主体。放数据本体 。
3. \<tfoot\>\</tfoot\>放表格的脚注之类。
4. 以上标签都是放到table标签中。

* * * * *

五、列表 
----

**「列表」**容器里面装载着结构，样式一致的文字或图表的一种形式，叫列表。

列表最大的特点就是整齐 、整洁、有序，跟表格类似，但是它可组合自由度会更高。

### 1. 无序列表 ul

-   \<ul\>\</ul\>中只能嵌套\<li\>\</li\>，直接在\<ul\>\</ul\>标签中输入其他标签或者文字的做法是不被允许的。
-   \<li\>与\</li\>之间相当于一个容器，可以容纳所有元素。

``` html
<ul>
  <li>列表项1</li>
  <li>列表项2</li>
  <li>列表项3</li>
  ......
</ul>
```

### 2. 有序列表 ol

-   \<ol\>标签中的type属性值为排序的序列号，不添加type属性时，有序列表默认从数字1开始排序。
-   常用的type属性值分别为是1，a，A，i，I
-   \<ol reversed="reversed"\>中的reversed属性能够让有序列表中的序列倒序排列。
-   \<ol start="3"\>中的start属性值为3，有序列表中的第一个序列号将从3开始排列。

``` html
<ol type="A"> 
  <li>列表项1</li>
  <li>列表二</li>
  <li>列表三</li>
</ol>
```

### 3. 自定义列表 dl

定义列表常用于对术语或名词进行解释和描述，定义列表的列表项前没有任何项目符号。

``` html

<dl>
  <dt>名词1</dt>
  <dd>名词1解释1</dd>
  <dd>名词1解释2</dd>
  ...
  <dt>名词2</dt>
  <dd>名词2解释1</dd>
  <dd>名词2解释2</dd>
  ...
</dl>
```

* * * * *

六、表单
----

在HTML中，一个完整的表单通常由表单控件（也称为表单元素）、提示信息和表单域 3 个部分构成。表单目的是为了收集用户信息。

**表单控件：**
包含了具体的表单功能项，如单行文本输入框、密码输入框、复选框、提交按钮、重置按钮等。
**提示信息：**
一个表单中通常还需要包含一些说明性的文字，提示用户进行填写和操作。
**表单域：**
它相当于一个容器，用来容纳所有的表单控件和提示信息，可以通过他定义处理表单数据所用程序的url地址，以及数据提交到服务器的方法。如果不定义表单域，表单中的数据就无法传送到后台服务器。

### 1. input 控件

``` html
<input type="属性值" value="你好">
```

-   input 输入的意思
-   \<input /\>标签为单标签
-   type属性设置不同的属性值用来指定不同的控件类型
-   除了type属性还有别的属性

**常用属性：**

<table>
 	<tr>
 	    <th>属性</th>
 	    <th>属性值</th>
 	    <th>描述</th>
   	</tr >
 	<tr >
 	    <td rowspan="9">type</td>
 	    <td>text</td>
 	    <td>单行文本输入框</td>
 	</tr>
 	<tr>
 	    <td>password</td> 
	    <td>密码输入框</td>
 	</tr>
 	<tr>
 	    <td>radio</td>
 	    <td>单选按钮</td>
 	</tr>
 	<tr>
 	    <td>CheckBox</td>
 	    <td>复选按钮</td>
 	</tr>
 	<tr>
	<td>button</td>
 	<td>普通按钮</td>
 	</tr> 
	<tr>
 	    <td>submit</td>
 	    <td>提交按钮</td>
 	</tr>
 	<tr>
 	    <td>reset</td> 
	    <td>重置按钮</td>
 	</tr>
 	<tr>
 	    <td>image</td>
 	    <td>图像形式的提交按钮</td>
 	</tr>
 	<tr>
 	    <td >file</td>
 	    <td>文件域</td>
 	</tr>
 	<tr>
 	    <td >name</td>
 	    <td>用户自定义</td>
 	    <td>控件名称</td>
 	</tr> 
	<tr>
 	    <td >value</td>
 	    <td >用户自定义</td>
 	    <td >默认文本值</td> 
	</tr>
 	<tr>
 	    <td >size</td>
 	    <td >正整数</td> 
	    <td >控件在页面中的显示宽度</td>
 	</tr>
 	<tr>
 	    <td >checked</td>
 	    <td >checked</td>
 	    <td >定义选择控件默认被选中项</td>
 	</tr>
 	<tr>
 	    <td >maxlength</td>
 	    <td >正整数</td>
 	    <td >控件允许输入的最多字符</td>
 	</tr>
 </table>

``` html
用户名: <input type="text" /> 
密  码：<input type="password" />
```

**value属性**

value 默认的文本值。有些表单想刚打开页面就默认显示几个文字，就可以通过这个value来设置。

``` html
用户名:<input type="text"  name="username" value="请输入用户名"> 
```

**name属性**

name表单的名字，后台可以通过这个name属性找到这个表单。 页面中的表单很多，name主要作用就是用于区别不同的表单。

-   name属性后面的值，是我们自己定义的。
-   radio  如果是一组，我们必须给他们命名相同的名字 name 这样就可以多个选其中的一个
-   name属性，我们现在用的较少，但是，当我们学ajax 和后台的时候，是必须的。

``` html
<input type="radio" name="sex"  />男<input type="radio" name="sex" />女
```

**checked属性**

表示默认选中状态。 较常见于 单选按钮和复选按钮。

``` html
性    别:<input type="radio" name="sex" value="男" checked="checked" />男<input type="radio" name="sex" value="女" />女 
```

**input 属性小结**

| 属性    | 说明     | 作用                                                 |
| ------- | -------- | ---------------------------------------------------- |
| type    | 表单类型 | 用来指定不同的表单类型                               |
| value   | 表单值   | 表单里面默认显示的文本                               |
| name    | 表单名称 | 页面中的表单很多，name主要作用就是用于区别不同的表单 |
| checked | 默认选中 | 表示那个单选或复选按钮默认就被选中                   |

### 2. label标签

-   label 标签为 input 元素定义标注（标签）。
-   label标签主要目的是为了提高用户体验。为用户提高最优秀的服务。

**作用：**用于绑定一个表单元素，当点击 label 标签的时候,被绑定的表单元素就会获得输入焦点。

**如何绑定元素呢**

-   第一种用法就是用label标签直接包含input表单， 适合单个表单选择
-   第二种用法 for 属性规定 label 与哪个表单元素绑定(通过id)。

``` html
第一种
  <label> 用户名： 
    <input type="radio" name="usename" value="请输入用户名">   
  </label>
第二种
  <label for="sex">男</label>
  <input type="radio" name="sex"  id="sex">
```

### 3. textarea控件(文本域)

-   通过textarea控件可以轻松地创建多行文本输入框。
-   cols="每行中的字符数"  rows="显示的行数"  我们实际开发不用

``` html
  <textarea >
    文本内容
  </textarea>
```

**文本框和文本域区别**

| 表单              | 名称   | 区别             | 默认值显示                  | 用于场景             |
| ----------------- | ------ | ---------------- | --------------------------- | -------------------- |
| input type="text" | 文本框 | 只能显示一行文本 | 单标签，通过value显示默认值 | 用户名、昵称、密码等 |
| textarea          | 文本域 | 可以显示多行     | 双标签，默认值写到标签中间  | 留言板               |

### 4. select下拉列表

-   如果有多个选项让用户选择，为了节约空间，我们可以使用select控件定义下拉列表。
-   在option 中定义selected =" selected "时，当前项即为默认选中项。
-   我们实际开发会用的比较少

``` html
<select>
  <option>选项1</option>
  <option>选项2</option>
  <option>选项3</option>
  ...
</select>
```

### 5. form表单域

收集的用户信息通过form表单域传递给服务器。

目的：在HTML中，form标签被用于定义表单域，以实现用户信息的收集和传递，form中的所有内容都会被提交给服务器。

``` html
<form action="url地址" method="提交方式" name="表单名称">
  各种表单控件
</form>
```

**常用属性：**

-   每个表单都应该有自己表单域。后面学 ajax 后台交互的时候，必须需要form表单域。

| 属性   | 属性值   | 作用                                           |
| ------ | -------- | ---------------------------------------------- |
| action | url地址  | 用于指定接收并处理表单的服务器的url地址        |
| method | get/post | 用于设置表单数据的提交方式，其值为get或post    |
| name   | 名称     | 用于指定表单的名称，以区分一个页面中的多个表单 |

**GET 和 POST 的区别**

-   GET在浏览器回退时是无害的，而POST会再次提交请求。
-   GET请求会被浏览器主动cache，而POST不会，除非手动设置。
-   GET请求只能进行url编码，而POST支持多种编码方式。
-   GET请求参数会被完整保留在浏览器历史记录里，而POST中的参数不会被保留。
-   GET请求大小一般是(1024字节)，http协议并没有限制，而与服务器，操作系统有关，POST理论上来说没有大小限制，http协议规范也没有进行大小限制，但实际上post所能传递的数据量根据取决于服务器的设置和内存大小。
-   对参数的数据类型，GET只接受ASCII字符，而POST没有限制。
-   GET比POST更不安全，因为参数直接暴露在URL上，所以不能用来传递敏感信息。

**团队约定：**

-   元素属性值使用双引号语法
-   元素属性值可以写上的都写上

``` html
推荐
<input type="text" /> 
<input type="radio" name="name" checked="checked" />
```

## 查阅文档

W3C：http://www.w3school.com.cn/

MDN：http://developer.mozilla.org/zh-CN/

