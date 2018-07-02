## 4.通用规则

1. 注意前端性能优化，使页面加载速度尽可能的快。
2. 尽可能提高css和js的复用率，避免重复开发。
3. 格式：
  1. 1)缩进：每次缩进使用2个空格，若使用tab需要改为2空格。
  2. 2)使用linux换行符，即LF(\n或0a)。
  3. 3)大小写：标签、颜色等不区分大小写的场景，一律使用小写字母。适用于元素名，属性，属性值（除了文本和 CDATA ）， 选择器，特性，特性值（除了字符串）。
  4. 4)删除行尾白空格。
  5. 5)行尾风格，不推荐次行风格。
4. 协议
  1. 1)嵌入式资源书写省略协议头。
  2. 2)省略图像、媒体文件、样式表和脚本等URL协议头部声明 ( http: , https: )。如果不是这两个声明的URL则不省略。
  3. 3)省略协议声明，使URL成相对地址，防止内容混淆问题和导致小文件重复下载。
  ```
  <!-- 不推荐 -->
  <script src="http://www.google.com/js/gweb/analytics/autotrack.js"></script>
  <!-- 推荐 -->
  <script src="//www.google.com/js/gweb/analytics/autotrack.js"></script>
  /* 不推荐 */
  .example {
    background: url(http://www.google.com/images/example);
  }
  /* 推荐 */
  .example {
    background: url(//www.google.com/images/example);
  }
  ```

5. 元数据规则

  1. 1)编码

用不带BOM头的 UTF-8编码。
让你的编辑器用没有字节顺序标记的UTF-8编码格式进行编写。
在HTML模板和文件中指定编码 &lt;meta charset=&quot;utf-8&quot;&gt; . 不需要制定样式表的编码，它默认为UTF-8。（更多有关于编码的信息和怎样指定它，请查看  [Character Sets &amp; Encodings in XHTML, HTML and CSS](http://www.w3.org/International/tutorials/tutorial-char-enc/en/all.html)。）

  1. 2)注释
尽可能的去解释你写的代码。用注释来解释代码：它包括什么，它的目的是什么，它能做什么，为什么使用这个解决方案，还是说只是因为偏爱如此呢？
  1. 3)只用 TODO 来强调代办事项或者活动的条目。格式：空格+TODO+英文冒号+空格
  ```
  //  TODO: 活动条目说明 。
  <!-- TODO: 删除可选元素 -->
  ```
## 5.文件规范

1. html，css，js，images文件均归档至&lt;系统开发规范&gt;约定的目录中。
2. 英文命名，以下划线&quot;\_&quot;作为单词分隔符。
3. html文件:

  1. 1)英文命名，后缀.html；同时将对应界面稿放于同目录中。
  2. 2)若界面稿命名为中文，或者和实际访问路径不同，请重命名与html文件同名（或修改访问路径），以方便后端添加功能时查找对应页面。

1. css文件:

  1. 1)英文命名，后缀.css；共用common.css，首页index.css，其他页面依实际模块需求命名。
  2. 2)文件组织结构参考Js文件。

1. Js文件:

  1. 1)文件名须包含库名称及版本号及是否为压缩版，比如jquery-1.3.2.min.js； 引入插件，文件名格式为库名称+插件名称，比 如jquery.cookie.js。
  2. 2)文件组织结构：
    1. 公共代码路径static/js/util。
    2. 组件代码路径static/js/component。
    3. 模块代码路径 static/js/module,根据业务命名（最好和html、css命名相同）。
  3. 3)第三方代码放在 static/libs 中，不要和 js 代码混在一起。
  4. 4)修改第三方代码时，位置和文件名不变，必须要在文件头部写明修改内容、作者、时间。

1. 所有页面元素类图片均放入images或img文件夹。
2. 一个文件应该是一个最小逻辑功能组件，不要担心文件太多，部署的时候打包就行。

## 6.HTML代码风格规则

1. 1.通用规则

1. 1)文档类型：统一为html5声明类型&lt;!DOCTYPE html&gt;。
2. 2)能以背景形式呈现的图片，尽量写入css样式中。
3. 3)书写链接地址时，必须避免重定向，例如：href=&quot;http://www.cncn.com/&quot;，即须在URL地址后面加上&quot;/&quot;。

1. 2.格式

1. 1)属性值必须用双引号包括；
2. 2)每个块元素、列表元素或表格元素都独占一行，每个子元素都相对于父元素进行缩进；
3. 3)避免实体引用，如&amp;mdash;及&amp;rdquo;（空格等不可见元素除外）；

1. 3.文件引用

1. 1)非特殊情况下样式文件必须外链至&lt;head&gt;...&lt;/head&gt;之间；
2. 2)非特殊情况下JavaScript文件必须外链至页面底部；
3. 3)在样式表（除非不用 CSS）和脚本（除非不用 JavaScript）的标签中 不写 type 属性。写法如下:
  ```
  <link rel="stylesheet" href="..." />
  <style>...</style>
  <script src="..."></script>
  ```
1. 4.标签

1. 1)自闭合（self-closing）标签，无需闭合 ( 例如： img input br hr 等 )；
2. 2)可选的闭合标签（closing tag），需闭合 ( 例如：&lt;/li&gt; 或 &lt;/body&gt; )；
3. 3)尽量减少标签数量，尽量减少标签嵌套；

1. 5.标签嵌套

1. 1)内联元素中不可嵌套块级元素；
2. 2)严格嵌套约束：
  - inline-Level 元素，仅可以包含文本或其它 inline-Level 元素;
  - &lt;a&gt;里不可以嵌套交互式元素&lt;a&gt;、&lt;button&gt;、&lt;select&gt;等;
  - &lt;p&gt;里不可以嵌套块级元素&lt;div&gt;、&lt;h1&gt;~&lt;h6&gt;、&lt;p&gt;、&lt;ul&gt;/&lt;ol&gt;/&lt;li&gt;、&lt;dl&gt;/&lt;dt&gt;/&lt;dd&gt;、&lt;form&gt;等。

1. 3)语义嵌套约束：
  - &lt;li&gt; 用于 &lt;ul&gt; 或 &lt;ol&gt; 下；
  - &lt;dd&gt;, &lt;dt&gt; 用于 &lt;dl&gt; 下；
  - &lt;thead&gt;, &lt;tbody&gt;, &lt;tfoot&gt;, &lt;tr&gt;, &lt;td&gt; 用于 &lt;table&gt; 下；

1. 4)严格嵌套约束在所有的浏览器下都不被允许；而语义嵌套约束，浏览器大多会容错处理，生成的文档树可能相互不太一样；
2. 5)更多详情，参考 [WEB标准系列-HTML元素嵌套](http://www.smallni.com/element-nesting/)

1. 6.Table标签

1. 1)避免使用table做布局；
2. 2)表格标题要使用&lt;caption&gt;，表头使用&lt;thead&gt;包围，主体部分使用包围，尾部使用&lt;tfoot&gt;包围，表头和一般单元格要区分开，表头用&lt;th&gt;,一般单元格用&lt;td&gt;；
3. 3)使用table标签时，不要用width/height/cellspacing/cellpadding等table属性直接定义表现，应用css控制表现；

1. 7.属性

1. 1)为含有描述性表单元素添加label属性；
2. 2)给重要的图片加上alt属性；
3. 3)给重要的元素和截断的元素加上title属性；
4. 4)布尔值属性不用设置值（disabled、checked、selected等）；
5. 5)合理使用style属性，避免滥用造成的耦合；
6. 6)HTML 属性应该按照特定的顺序出现以保证易读性：Id &gt; class &gt; name &gt; data-xxx &gt; src, for, type, href &gt; title, alt &gt; aria-xxx, role

1. 8.语义化

根据HTML各个元素的用途而去使用它们。语义化的 HTML 结构，有助于机器（搜索引擎）理解，另一方面多人协作时，能迅速了解开发者意图。

例如，用heading元素构造标题， p 元素构造段落, a 元素构造锚点等。根据HTML各个元素的用途而去使用是很重要的，它涉及到文档的可访问性、重用和代码效率等问题。
```
<!-- 不推荐 -->
<div onclick="goToRecommendations();">All recommendations</div>
<!-- 推荐 -->
<a href="recommendations/">All recommendations</a>
```
标题内容型：
标题使用&lt;h2&gt;而不是&lt;div class=&quot;h2&quot;&gt;,段落使用&lt;p&gt;标签，锚点使用&lt;a&gt;。

表单：
分组表单要用&lt;fieldset&gt;标签包起来，并用&lt;legend&gt;标签进行说明表单的用途。

1. 9.关注点分离

严格保持结构 （HTML 结构），表现 （CSS），和行为 （JS）三者分离, 并尽量让这三者之间的交互保持最低限度。
就是说，尽量在文档和模板中只包含结构性的 HTML；而将所有表现代码，移入样式表中；将所有动作行为，移入脚本之中。
在此之外，为使得它们之间的联系尽可能的小，在文档和模板中也尽量少地引入样式和脚本文件。

清晰的分层意味着：
  1. 1)避免使用行内样式，避免在元素上使用 style 属性；
  2. 2)避免使用行内脚本；
  3. 3)避免使用表象元素（i.e. &lt;b&gt;, &lt;u&gt;, &lt;center&gt;, &lt;font&gt;, &lt;b&gt;）；
  4. 4)避免使用表象 class 名（i.e. red, left, center）；
  5. 5)用带&quot;js-&quot;前缀的class作为js选择器钩子，这个class不应包含有样式。为方便查看，统一写在class属性最前面。例：class=&quot;js-event nav nav-header&quot;

**示例一：**

不推荐
推荐

**示例二：**

不推荐
推荐

## 7. **CSS** 代码风格规则

1. 1.声明块格式

1. 1)缩进所有代码块（&quot;{}&quot;之间）内容；
2. 2)选择器分组时，保持独立的选择器占用一行，且与上一个选择器之间空一行；【待讨论】
3. 3)声明块的左括号 { 前添加一个空格；
4. 4)声明块的右括号 } 应单独成行；
5. 5)声明语句中的 : 后应添加一个空格；
6. 6)声明语句应以分号 ; 结尾；
7. 7)一般以逗号分隔的属性值，每个逗号后应添加一个空格；
8. 8)模块之间空2行；
9. 9)将媒体查询放在尽可能相关规则的附近。不要将他们打包放在一个单一样式文件中或者放在文档底部；

1. 2.属性格式

1. 1)css属性书写顺序，建议遵循：布局定位&gt;盒模型属性&gt;排版属性&gt;展示属性&gt;其他属性；
2. 2)属性的划分并不绝对。这么排列的原因是定位可以从正常的文档流中移除元素，并且还能覆盖盒模型相关的样式，因此排在首位。盒模型决定了组件的尺寸和位置，因此排在第二位。其他属性只是影响组件的内部或者是不影响前两组属性，因此排在后面。
  - 布局定位属性： display、position（相应的top,right,bottom,left）、z-index等；
  - 盒模型属性： box-sizing、float、clear、overflow、width、height、margin、padding、border、visibility等；
  - 排版属性：font、line-height、text-align、vertical-align、white-space、list-style、opacity等
  - 展示属性：color、text-decoration、background等；
  - 其他属性：cursor
  - 链接样式的顺序：a:link -&gt; a:visited -&gt; a:hover -&gt; a:active

1. 3)写属性值的时候尽量使用缩写（例如border、font）；
2. 4)省略0后面的单位；
3. 5)省略0开头小数点前面的0；
4. 6)省略url内的引号；
5. 7)属性选择符、属性值使用双引号；
  ```
  .selector[type=&quot;text&quot;] {
    font-family: &quot;open sans&quot;, arial, sans-serif;
  }
  ```
1. 8)十六进制尽可能使用3个字符，更简洁；
2. 9)不需要添加浏览器前缀，可以通过插件统一添加；

1. 3.ID和class的命名

1. 1)避免使用拼音
2. 2)为ID和class取通用且有意义的名字，而不是表象或模糊不清的命名。
3. 3)应该优先虑以这元素具体目来进行命名，这样他就最容易理解，减少更新。
4. 4)通用名称可以加在兄弟元素都不特殊或没有个别意义的元素上，可以起名类似&quot;helpers&quot;这样的泛。
5. 5)使用功能性或通用的名字会减少不必要的文档或模板修改。
6. 6)多单词组合的用&quot;-&quot;分开。
  ```
  /* 不推荐 */
  #navigation {}
  .atr {}
  /* 推荐 */
  #nav {}
  .author {}
  ```
1. 7)为模块中的子元素命名，建议在ID或class名字前加上标识性前缀作为命名空间，用&quot;-&quot;分开。
```
<div id="mainnav"><div class="main-firstnav">...</div></div>
```
1. 4.ID 与 class 的使用

1. 1)id是唯一的并是父级的，class是可以重复的并是子级的，所以id仅使用在大的模块上，class可用在重复使用率高及子级中；
2. 2)非必要的情况下不要使用元素标签名和ID或class进行组合；
3. 3)避免选择器嵌套层级过多，尽量少于 3 级；

1. 5.性能优化

1. 1)慎重选择高消耗的样式。高消耗属性在绘制前需要浏览器进行大量计算：box-shadows、border-radius、transparency、transforms、CSS filters（性能杀手）
2. 2)避免过分重排。当发生重排的时候，浏览器需要重新计算布局位置与大小。通常影响到容器定位、盒模型的属性都会引起重排。
3. 3)不要滥用float。
4. 4)提升 CSS 选择器性能：CSS 选择器是从右到左进行规则匹配，因此选择器要尽量准确且精简，尤其避免使用通用选择器\*。

## 8.SASS/LESS代码风格规则

1. 代码组织顺序：@import &gt; 变量声明 &gt; 样式声明。
2. 嵌套：

- 避免嵌套层级过多。这会使代码看起来过于复杂，以不利于选择器性能。
- 避免嵌套没有任何内容的选择器。如果需要指定一些子元素的样式属性，而父元素将没有什么样式属性，可以使用常规的CSS选择器链。
- 嵌套顺序：

1. 1)当前选择器的样式属性；
2. 2)父级选择器的伪类选择器 (:first-letter, :hover, :active etc)；
3. 3)伪类元素 (:before and :after)；
4. 4)父级选择器的声明样式 (.selected, .active, .enlarged etc.)；
5. 5)用Sass的上下文媒体查询；
6. 6)子选择器作为最后的部分；

1. 善用变量、继承、方法。

## 9. **JavaScript** 代码风格规则

1. 1.格式

1. 1)优先使用单引号(&#39;)于双引号(&quot;)，因为字符串可能包含HTML代码；
2. 2)函数声明与函数声明、变量声明与函数声明、函数内部的逻辑块之间都应该有空行隔开；
3. 3)函数声明部分前后各有一个空格，&quot;{&quot;不换行，&quot;}&quot; 换行；
4. 4)if后的圆括号部分前后各有一个空格，&quot;{&quot;不换行，else 不换行，&quot;}&quot; 换行；
5. 5)switch语句：

- 缩进：case比switch缩进1级，break比case缩进1级；
- case贯穿：用空行或注释//falls through表明case贯穿是故意的（避免使用case；贯穿）
- default：保留default或者用注释//no default表明没有default；

1. 6)模块之间空1行，用模块注释进行分割；

1. 2.命名规则

1. 1)变量、方法：驼峰命名法——第一个单词首字母小写，其余单词首字母大写；
2. 2)类：帕斯卡命名法——与驼峰类似，但第一个单词首字母大写；
3. 3)常量：全部字母大写，以下划线分割单词；
4. 4)私有属性、变量和方法：下划线开头，首字母小写，驼峰命名法；
5. 5)存放 jQuery 对象的变量以 $ 开头，使用驼峰命名变量；
6. 6)命名语义化，尽可能利用英文单词或其缩写；

1. 3.命名语法

1. 1)命名语义化，尽可能利用英文单词或其缩写；
2. 2)类名，使用名词；
3. 3)函数名，使用动宾短语；
4. 4)boolean 类型的变量使用 is 或 has 开头，不要笼统的用flag命名；
5. 5)Promise 对象用动宾短语的进行时表达；

1. 4.声明

1. 1)变量和函数先声明再使用；
2. 2)变量集中声明，就近声明；
3. 3)可以不必在声明变量的时候就进行初始化，延迟初始化挺好的；
4. 4)避免全局变量；
5. 5)将 jQuery 选择器返回的对象缓存到本地变量中复用；
6. 6)避免块内函数声明，如果一定要用的话可以在块内用变量来定义函数；

1. 5.运算符

1. 1)二元和三元操作符必须在当前行的末尾，避免被分号阻断。操作符在上一行末尾，且下一行缩进。
2. 2)使用三元操作符(?:)用于替代简单的 if 条件判断语句。
3. 3)使用 &amp;&amp; 和 || 。二元布尔操作符是可短路的, 只有在必要时才会计算到最后一项。也可以避免 if 判断嵌套。
4. 4)使用 === 或 !== 做严格的相等判断，避免使用 == 或 !=，因为隐式类型转换可能带来错误。

1. 6.语法规则

1. 1)建议使用严格模式。
2. 2)不允许修改内置对象的原型。

1. 7.性能优化

1. 1)避免不必要的 DOM 操作：

- 简化 DOM 树结构，减少嵌套；
- 避免频繁的 DOM 查询：如当一个元素出现多次时，将它保存在一个变量中；
- 避免在循环中插入，应当先缓存，在循环结束后插入。

1. 2)避免在循环中重复计算。对于在循环中使用且不会被改变的对象，应当在循环前缓存。


## 11. **注释书写规则**

1. 1.原则

1. 1)As short as possible（如无必要，勿增注释）：尽量提高代码本身的清晰性、可读性。
2. 2)As long as necessary（如有必要，尽量详尽）：合理的注释、空行排版等，可以让代码更易阅读、更具美感。
3. 3)在哪里添注释：
  - 不能自解释的代码；
  - 针对浏览器的hack；
  - 文档注释；
  - 应该给各个函数添注释，包括功能描述、参数、返回值、抛出的错误等等；

1. 2.单行注释

1. 1)行尾：用1级缩进隔开代码
2. 2)独占一行：用来注释下面，要与被注释的代码保持相同的缩进
3. 3)// 后面要有一个空格

1. 3.多行注释

1. 1)多行注释上方留一个空行
2. 2)\*星号后面留一个空格
3. 3)方法的注释推荐参考Eclipse风格：
  ```
  /**
   * 添加指定元素到默认数组
   *
   * @method add
   * @param {Number} 将要添加的元素
   * @return {Boolean} 添加成功/失败
   * @throw {TypeError} 参数类型不匹配
   */
  function add(item){
      if(typeof item === "number"){
          arr.push(item)
      }
      else{
          throw new TypeError();
      }
  }
  ```
1. 4.文件注释：

文件注释用于告诉不熟悉这段代码的读者这个文件中包含哪些东西。 应该提供文件的大体内容, 它的作者, 依赖关系和兼容性信息。如下：
```
/**
 * @fileoverview Description of file, its uses and information
 * about its dependencies.
 * @author user@meizu.com (Firstname Lastname)
 * Copyright 2009 Meizu Inc. All Rights Reserved.
 */
```
## 12. **开发及测试工具约定**

1. 可根据自己喜好选择IDE，编码必须格式化，比如缩进、换行等