# 美丽的汤中文文档

作者：

Leonard Richardson

 （leonardr@segfault.org） 

翻译：

Richie Yan

 （richieyan@gmail.com） 

\###如果有些翻译的不准确或者难以理解，直接看例子吧。### 

英文原文点

这里

[美丽的汤](http://www.crummy.com/software/BeautifulSoup/)是用Python写的一个HTML / XML的解析器，它可以很好的处理不规范标记并生成剖析树（parse tree）。它提供简单又常用的导航（导航），搜索以及修改剖析树的操作。它可以大大节省你的编程时间。对于Ruby，使用[Rubyful Soup](http://www.crummy.com/software/RubyfulSoup/)。

这个文档说明了Beautiful Soup 3.0主要的功能特性，并附有例子。从中你可以知道这个库有哪些好处，它是怎样工作的，怎样让它帮做你想做的事以及你该怎样做当它做的和你期待不一样。

## 目录

- [快速开始](https://www.crummy.com/software/BeautifulSoup/bs3/documentation.zh.html#Quick%20Start)

- [剖析文档](https://www.crummy.com/software/BeautifulSoup/bs3/documentation.zh.html#Parsing%20a%20Document)

- - [剖析HTML](https://www.crummy.com/software/BeautifulSoup/bs3/documentation.zh.html#Parsing%20HTML)
  - [剖析XML](https://www.crummy.com/software/BeautifulSoup/bs3/documentation.zh.html#Parsing%20XML)
  - [如果它不工作](https://www.crummy.com/software/BeautifulSoup/bs3/documentation.zh.html#If%20That%20Doesn%27t%20Work)

- [使用Unicode的美丽汤，该死](https://www.crummy.com/software/BeautifulSoup/bs3/documentation.zh.html#Beautiful%20Soup%20Gives%20You%20Unicode,%20Dammit)

- [输出文档](https://www.crummy.com/software/BeautifulSoup/bs3/documentation.zh.html#Printing%20a%20Document)

- [剖析树](https://www.crummy.com/software/BeautifulSoup/bs3/documentation.zh.html#The%20Parse%20Tree)

- - [`Tag`小号的属性](https://www.crummy.com/software/BeautifulSoup/bs3/documentation.zh.html#The%20attributes%20of%20Tags)

- [导航剖析树](https://www.crummy.com/software/BeautifulSoup/bs3/documentation.zh.html#Navigating%20the%20Parse%20Tree)

- - [`parent`](https://www.crummy.com/software/BeautifulSoup/bs3/documentation.zh.html#parent)
  - [`contents`](https://www.crummy.com/software/BeautifulSoup/bs3/documentation.zh.html#contents)
  - [`string`](https://www.crummy.com/software/BeautifulSoup/bs3/documentation.zh.html#string)
  - [`nextSibling` 和 `previousSibling`](https://www.crummy.com/software/BeautifulSoup/bs3/documentation.zh.html#nextSibling%20and%20previousSibling)
  - [`next` 和 `previous`](https://www.crummy.com/software/BeautifulSoup/bs3/documentation.zh.html#next%20and%20previous)
  - [遍历`Tag`](https://www.crummy.com/software/BeautifulSoup/bs3/documentation.zh.html#Iterating%20over%20a%20Tag)
  - [使用标签名作为成员](https://www.crummy.com/software/BeautifulSoup/bs3/documentation.zh.html#Using%20tag%20names%20as%20members)

- [搜索剖析树](https://www.crummy.com/software/BeautifulSoup/bs3/documentation.zh.html#Searching%20the%20Parse%20Tree)

- - [基本查找方法： `findAll(name, attrs, recursive, text, limit, **kwargs)`](https://www.crummy.com/software/BeautifulSoup/bs3/documentation.zh.html#The%20basic%20find%20method:%20findAll%28name,%20attrs,%20recursive,%20text,%20limit,%20**kwargs%29)

  - - [使用CSS类查找](https://www.crummy.com/software/BeautifulSoup/bs3/documentation.zh.html#Searching%20by%20CSS%20class)
    - [像`findall`一样调用标签](https://www.crummy.com/software/BeautifulSoup/bs3/documentation.zh.html#Calling%20a%20tag%20is%20like%20calling%20findall)

  - [`find(name, attrs, recursive, text, **kwargs)`](https://www.crummy.com/software/BeautifulSoup/bs3/documentation.zh.html#find%28name,%20attrs,%20recursive,%20text,%20**kwargs%29)

  - [`first`哪里去了？](https://www.crummy.com/software/BeautifulSoup/bs3/documentation.zh.html#What%20happened%20to%20first?)

- [正在搜索剖析树内部](https://www.crummy.com/software/BeautifulSoup/bs3/documentation.zh.html#Searching%20Within%20the%20Parse%20Tree)

- - [`findNextSiblings(name, attrs, text, limit, **kwargs)` 和 `findNextSibling(name, attrs, text, **kwargs)`](https://www.crummy.com/software/BeautifulSoup/bs3/documentation.zh.html#findNextSiblings%28name,%20attrs,%20text,%20limit,%20**kwargs%29%20and%20findNextSibling%28name,%20attrs,%20text,%20**kwargs%29)
  - [`findPreviousSiblings(name, attrs, text, limit, **kwargs)` 和 `findPreviousSibling(name, attrs, text, **kwargs)`](https://www.crummy.com/software/BeautifulSoup/bs3/documentation.zh.html#findPreviousSiblings%28name,%20attrs,%20text,%20limit,%20**kwargs%29%20and%20findPreviousSibling%28name,%20attrs,%20text,%20**kwargs%29)
  - [`findAllNext(name, attrs, text, limit, **kwargs)` 和 `findNext(name, attrs, text, **kwargs)`](https://www.crummy.com/software/BeautifulSoup/bs3/documentation.zh.html#findAllNext%28name,%20attrs,%20text,%20limit,%20**kwargs%29%20and%20findNext%28name,%20attrs,%20text,%20**kwargs%29)
  - [`findAllPrevious(name, attrs, text, limit, **kwargs)` 和 `findPrevious(name, attrs, text, **kwargs)`](https://www.crummy.com/software/BeautifulSoup/bs3/documentation.zh.html#findAllPrevious%28name,%20attrs,%20text,%20limit,%20**kwargs%29%20and%20findPrevious%28name,%20attrs,%20text,%20**kwargs%29)

- [修改剖析树](https://www.crummy.com/software/BeautifulSoup/bs3/documentation.zh.html#Modifying%20the%20Parse%20Tree)

- - [改变属性值](https://www.crummy.com/software/BeautifulSoup/bs3/documentation.zh.html#Changing%20attribute%20values)
  - [删除元素](https://www.crummy.com/software/BeautifulSoup/bs3/documentation.zh.html#Removing%20elements)
  - [替换元素](https://www.crummy.com/software/BeautifulSoup/bs3/documentation.zh.html#Replacing%20one%20Element%20with%20Another)
  - [添加新元素](https://www.crummy.com/software/BeautifulSoup/bs3/documentation.zh.html#Adding%20a%20Brand%20New%20Element)

- [常见问题（故障检测）](https://www.crummy.com/software/BeautifulSoup/bs3/documentation.zh.html#Troubleshooting)

- - [为什么美丽的汤不能打印我的no-ASCII字符？](https://www.crummy.com/software/BeautifulSoup/bs3/documentation.zh.html#Why%20can%27t%20Beautiful%20Soup%20print%20out%20the%20non-ASCII%20characters%20I%20gave%20it?)
  - [美丽的汤弄丢了我给的数据！为什么？为什么?????](https://www.crummy.com/software/BeautifulSoup/bs3/documentation.zh.html#Beautiful%20Soup%20loses%20the%20data%20I%20fed%20it%21%20Why?%20WHY?????)
  - [美丽的汤太慢了！](https://www.crummy.com/software/BeautifulSoup/bs3/documentation.zh.html#Beautiful%20Soup%20is%20too%20slow%21)

- [高级主题](https://www.crummy.com/software/BeautifulSoup/bs3/documentation.zh.html#Advanced%20Topics)

- - [产生器（发电机）](https://www.crummy.com/software/BeautifulSoup/bs3/documentation.zh.html#Generators)
  - [其他的内部剖析器](https://www.crummy.com/software/BeautifulSoup/bs3/documentation.zh.html#Other%20Built-In%20Parsers)
  - [定制剖析器（分析器）](https://www.crummy.com/software/BeautifulSoup/bs3/documentation.zh.html#Customizing%20the%20Parser)
  - [实体转换](https://www.crummy.com/software/BeautifulSoup/bs3/documentation.zh.html#Entity%20Conversion)
  - [使用正则式处理糟糕的数据](https://www.crummy.com/software/BeautifulSoup/bs3/documentation.zh.html#Sanitizing%20Bad%20Data%20with%20Regexps)
  - [玩玩`SoupStrainer`小号](https://www.crummy.com/software/BeautifulSoup/bs3/documentation.zh.html#Fun%20With%20SoupStrainers)
  - [通过剖析部分文档来提升效率](https://www.crummy.com/software/BeautifulSoup/bs3/documentation.zh.html#Improving%20Performance%20by%20Parsing%20Only%20Part%20of%20the%20Document)
  - [使用`extract`改进内存使用](https://www.crummy.com/software/BeautifulSoup/bs3/documentation.zh.html#Improving%20Memory%20Usage%20with%20extract)

- [其它](https://www.crummy.com/software/BeautifulSoup/bs3/documentation.zh.html#See%20Also)

- - [使用Beautiful Soup的其他应用](https://www.crummy.com/software/BeautifulSoup/bs3/documentation.zh.html#Applications%20that%20use%20Beautiful%20Soup)
  - [类似的库](https://www.crummy.com/software/BeautifulSoup/bs3/documentation.zh.html#Similar%20libraries)

- [小结](https://www.crummy.com/software/BeautifulSoup/bs3/documentation.zh.html#Conclusion)

快速开始



从[这里](http://www.crummy.com/software/BeautifulSoup/#Download/)获得Beautiful Soup。 [变更日志](http://www.crummy.com/software/BeautifulSoup/CHANGELOG.html) 描述了3.0版本与之前版本的不同。

在程序中中导入Beautiful Soup库：

```
from BeautifulSoup import BeautifulSoup          # For processing HTML
from BeautifulSoup import BeautifulStoneSoup     # For processing XML
import BeautifulSoup                             # To get everything
```

下面的代码是Beautiful Soup基本功能的示范。你可以复制粘贴到你的python文件中，自己运行看看。

```
from BeautifulSoup import BeautifulSoup
import re

doc = ['<html><head><title>Page title</title></head>',
       '<body><p id="firstpara" align="center">This is paragraph <b>one</b>.',
       '<p id="secondpara" align="blah">This is paragraph <b>two</b>.',
       '</html>']
soup = BeautifulSoup(''.join(doc))

print soup.prettify()
＃ <HTML>
＃  <HEAD>
＃   <TITLE>
＃    页面标题
＃   </ TITLE>
＃  </ HEAD>
＃  <BODY>
＃   <p id =“firstpara”align =“center”>
＃    这是段落
＃    <B>
＃     一
＃    </ B>
＃    。
＃   </ p>
＃   <p id =“secondpara”align =“blah”>
＃    这是段落
＃    <B>
＃     二
＃    </ B>
＃    。
＃   </ p>
＃  </ BODY>
＃ </ HTML>
```

导航汤的一些方法：

```
soup.contents[0].name
＃ u'html”

soup.contents[0].contents[0].name
＃ u'head”

head = soup.contents[0].contents[0]
head.parent.name
＃ u'html”

head.next
＃ <title>页面标题</ title>

head.nextSibling.name
＃ u'body”

head.nextSibling.contents[0]
＃ <p id =“firstpara”align =“center”>这是段<b>一</ b>。</ p>

head.nextSibling.contents[0].nextSibling
＃ <p id =“secondpara”align =“blah”>这是段<b>两个</ b>。</ p>
```

下面是一些方法搜索汤，获得特定标签或有着特定属性的标签：

```
titleTag = soup.html.head.title
titleTag
＃ <title>页面标题</ title>

titleTag.string
＃ 你的页面标题'

len(soup('p'))
＃ 2

soup.findAll('p', align="center")
＃ [<p id =“firstpara”align =“center”>这是段落<b>一个</ b>。</ p>]

soup.find('p', align="center")
＃ <p id =“firstpara”align =“center”>这是段<b>一</ b>。</ p>

soup('p', align="center")[0]['id']
＃ u'firstpara”

soup.find('p', align=re.compile('^b.*'))['id']
＃ u'secondpara”

soup.find('p').b.string
＃ u'one”

soup('p')[1].b.string
＃ u'two”
```

修改汤也很简单：

```
titleTag['id'] = 'theTitle'
titleTag.contents[0].replaceWith("New title")
soup.html.head
＃ <head> <title id =“theTitle”>新标题</ title> </ head>

soup.p.extract()
soup.prettify()
＃ <HTML>
＃  <HEAD>
＃   <title id =“theTitle”>
＃    新标题
＃   </ TITLE>
＃  </ HEAD>
＃  <BODY>
＃   <p id =“secondpara”align =“blah”>
＃    这是段落
＃    <B>
＃     二
＃    </ B>
＃    。
＃   </ p>
＃  </ BODY>
＃ </ HTML>

soup.p.replaceWith(soup.b)
＃ <HTML>
＃  <HEAD>
＃   <title id =“theTitle”>
＃    新标题
＃   </ TITLE>
＃  </ HEAD>
＃  <BODY>
＃   <B>
＃    二
＃   </ B>
＃  </ BODY>
＃ </ HTML>

soup.body.insert(0, "This page used to have ")
soup.body.insert(2, " &lt;p&gt; tags!")
soup.body
＃ <body>此页面曾用于<b>两个</ b>＆lt; p＆gt; 标签！</ body>
```

一个实际例子，用于抓取[ICC商业犯罪服务每周盗版报告](http://www.icc-ccs.org/prc/piracyreport.php)页面，使用Beautiful Soup剖析并获得发生的盗版事件：

```
import urllib2
from BeautifulSoup import BeautifulSoup

page = urllib2.urlopen("http://www.icc-ccs.org/prc/piracyreport.php")
soup = BeautifulSoup(page)
for incident in soup('td', width="90%"):
    where, linebreak, what = incident.contents[:3]
    print where.strip()
    print what.strip()
    print
```

剖析文档



美丽的汤使用XML或HTML文档以字符串的方式（或类文件对象）构造。它剖析文档并在内存中创建通讯的数据结构

如果你的文档格式是非常标准的，解析出来的数据结构正如你的原始文档。但是如果你的文档有问题，美丽的汤会使用启发式修复可能的结构问题。

### 剖析HTML



使用`BeautifulSoup`类剖析HTML文档。 `BeautifulSoup`会得出以下一些信息：

- 有些标签可以内嵌（<BLOCKQUOTE>），有些不行（<P>）。
- table和list标签有一个自然的内包顺序。例如，<TD>标签内为<TR>标签，而不会相反。
- <SCRIPT>标签的内容不会被剖析为HTML。
- <META>标签可以知道文档的编码类型。

这是运行例子：

```
from BeautifulSoup import BeautifulSoup
html = "<html><p>Para 1<p>Para 2<blockquote>Quote 1<blockquote>Quote 2"
soup = BeautifulSoup(html)
print soup.prettify()
＃ <HTML>
＃  <P>
＃   第1段
＃  </ p>
＃  <P>
＃   第2段
＃   <BLOCKQUOTE>
＃    引用1
＃    <BLOCKQUOTE>
＃     引用2
＃    </ BLOCKQUOTE>
＃   </ BLOCKQUOTE>
＃  </ p>
＃ </ HTML>
```

注意：`BeautifulSoup`会智能判断那些需要添加关闭标签的位置，即使原始的文档没有。

也就是说那个文档不是一个有效的HTML，但是它也不是太糟糕。下面是一个比较糟糕的文档。在一些问题中，它的<FORM>的开始在<TABLE>外面，结束在<TABLE>里面。（这种HTML在一些大公司的页面上也屡见不鲜）

```
from BeautifulSoup import BeautifulSoup
html = """
<html>
<form>
 <table>
 <td><input name="input1">Row 1 cell 1
 <tr><td>Row 2 cell 1
 </form> 
 <td>Row 2 cell 2<br>This</br> sure is a long cell
</body> 
</html>"""
```

Beautiful Soup也可以处理这个文档：

```
print BeautifulSoup(html).prettify()
＃ <HTML>
＃  <FORM>
＃   <表>
＃    <TD>
＃     <input name =“input1”/>
＃     第1行单元格1
＃    </ TD>
＃    <TR>
＃     <TD>
＃      第2行单元格1
＃     </ TD>
＃    </ TR>
＃   </ TABLE>
＃  </ FORM>
＃  <TD>
＃   第2行单元格2
＃   <br />
＃   这个 
＃   肯定是一个长细胞
＃  </ TD>
＃ </ HTML>
```

table的最后一个单元格已经在标签<TABLE>外了; Beautiful Soup决定关闭<TABLE>标签当它在<FORM>标签哪里关闭了。写这个文档家伙原本打算使用<FORM>标签扩展到table的结尾，但是美丽的汤肯定不知道这些。即使遇到这样糟糕的情况，美丽的汤仍然可以剖析这个不合格文档，使你开业存取所有数据。

### 剖析XML



`BeautifulSoup`类似浏览器，是个具有启发性的类，可以尽可能的推测HTML文档作者的意图。但是XML没有固定的标签集合，因此这些启发式的功能没有作用。因此 `BeautifulSoup`处理XML不是很好。

使用`BeautifulStoneSoup`类剖析XML文档。它是一个概括的类，没有任何特定的XML方言已经简单的标签内嵌规则。下面是范例：

```
from BeautifulSoup import BeautifulStoneSoup
xml = "<doc><tag1>Contents 1<tag2>Contents 2<tag1>Contents 3"
soup = BeautifulStoneSoup(xml)
print soup.prettify()
＃ <文档>
＃  <TAG1>
＃   内容1
＃   <TAG2>
＃    内容2
＃   </ TAG2>
＃  </ TAG1>
＃  <TAG1>
＃   内容3
＃  </ TAG1>
＃ </ DOC>
```

`BeautifulStoneSoup`的一个主要缺点就是它不知道如何处理自结束标签.HTML有固定的自结束标签集合，但是XML取决对应的DTD文件。你可以通过传递`selfClosingTags`的参数的名字到 `BeautifulStoneSoup`的构造器中，指定自结束标签：

```
from BeautifulSoup import BeautifulStoneSoup
xml = "<tag>Text 1<selfclosing>Text 2"
print BeautifulStoneSoup(xml).prettify()
＃ <标签>
＃  文字1
＃  <自闭合>
＃   文字2
＃  </自闭合>
＃ </标签>

print BeautifulStoneSoup(xml, selfClosingTags=['selfclosing']).prettify()
＃ <标签>
＃  文字1
＃  <selfclosing />
＃  文字2
＃ </标签>
```

如果它不工作



这里有[一些其他的剖析类](https://www.crummy.com/software/BeautifulSoup/bs3/documentation.zh.html#Other%20Built-In%20Parsers) 使用与上述两个类不同的智能感应。你也可以[子类化以及定制一个剖析器](https://www.crummy.com/software/BeautifulSoup/bs3/documentation.zh.html#Customizing%20the%20Parser) 使用你自己的智能感应方法。

## 使用Unicode的美丽汤，该死



当你的文档被剖析之后，它就自动被转换为unicode。美丽的汤只存储Unicode字符串。

```
from BeautifulSoup import BeautifulSoup
soup = BeautifulSoup("Hello")
soup.contents[0]
＃ u'Hello”
soup.originalEncoding
＃ 'ASCII'
```

使用UTF-8编码的日文文档例子：

```
from BeautifulSoup import BeautifulSoup
soup = BeautifulSoup("\xe3\x81\x93\xe3\x82\x8c\xe3\x81\xaf")
soup.contents[0]
＃ U '\ u3053 \ u308c \ u306f'
soup.originalEncoding
＃ 'UTF-8'

str(soup)
＃ '\ XE3 \ X81 \ X93 \ XE3 \ X82 \ x8c \ XE3 \ X81 \ XAF'

＃ 注意：这个位使用EUC-JP，所以只有你有cjkcodecs才有效
＃ 安装，或正在运行Python 2.4。
soup.__str__('euc-jp')
＃ '\ XA4 \ XB3 \ XA4 \ XEC \ XA4 \ XCF'
```

Beautiful Soup使用一个称为`UnicodeDammit` 的类去来检测文档的编码，并将其转换为Unicode。如果你需要为其他文档（没有石油Beautiful Soup剖析过得文档）使用这转换，你也可以直接使用`UnicodeDammit`。它是基于[Universal Feed Parser](http://www.feedparser.org/)开发的。

如果你使用Python2.4之前的版本，请下载和安装[`cjkcodecs` 以及`iconvcodec`](http://cjkpython.i18n.org/) 是python支持更多的编码，特别是CJK编码。要想更好地自动检测，你也要安装[`chardet`](http://chardet.feedparser.org/)

美丽的汤会按顺序尝试不同的编码将你的文档转换为Unicode：

- 通过可以`fromEncoding`参数传递编码类型给汤的构造器
- 通过文档本身找到编码类型：例如XML的声明或者HTML文档`http-equiv`的META标签。如果Beautiful Soup在文档中发现编码类型，它试着使用找到的类型转换文档。但是，如果你明显的指定一个编码类型，并且成功使用了编码：这时它会忽略任何它在文档中发现的编码类型。
- 通过嗅探文件开头的一下数据，判断编码。如果编码类型可以被检测到，它将是这些中的一个：UTF- *编码，EBCDIC或者ASCII。
- 通过[`chardet`](http://chardet.feedparser.org/) 库，嗅探编码，如果你安装了这个库。
- UTF-8
- Windows的1252

美丽的汤总是会猜对它可以猜测的。但是对于那些没有声明以及有着奇怪编码的文档，它会常常会失败。这时，它会选择Windows-1252编码，这个可能是错误的编码。下面是EUC-JP的例子，Beautiful Soup猜错了编码。（重申一下：因为它使用了EUC-JP，这个例子只会在python 2.4或者你安装了`cjkcodecs`的情况下才工作。）：

```
from BeautifulSoup import BeautifulSoup
euc_jp = '\xa4\xb3\xa4\xec\xa4\xcf'

soup = BeautifulSoup(euc_jp)
soup.originalEncoding
＃ “窗口1252”

str(soup)
＃ '\ xc2 \ xa4 \ xc2 \ xb3 \ xc2 \ xa4 \ xc3 \ xac \ xc2 \ xa4 \ xc3 \ x8f'＃错了！
```

但如果你使用`fromEncoding`参数指定编码，它可以正确的剖析文档，并可以将文档转换为UTF-8或者转回EUC-JP。

```
soup = BeautifulSoup(euc_jp, fromEncoding="euc-jp")
soup.originalEncoding
＃ “窗口1252”

str(soup)
＃ '\ xe3 \ x81 \ x93 \ xe3 \ x82 \ x8c \ xe3 \ x81 \ xaf'＃对！

soup.__str__(self, 'euc-jp') == euc_jp
＃ 真正
```

如果你指定美丽的汤使用Windows-1252编码（或者类似的编码如ISO-8859-1，ISO-8859-2），美丽的汤找到并破坏文档的智能引用以及其他的Windows特定的字符。这些字符不会转换为相应的Unicode，而是将它们变为HTML实体（`BeautifulSoup`）或者XML entitis（`BeautifulStoneSoup`）。

但是，你可以指定参数`smartQuotesTo=None`到汤构造器：这时智能引用会被正确的转换为Unicode。你也可以指定`smartQuotesTo`为“xml”或“html”去改变`BeautifulSoup`和`BeautifulStoneSoup`的默认操作。

```
from BeautifulSoup import BeautifulSoup, BeautifulStoneSoup
text = "Deploy the \x91SMART QUOTES\x92!"

str(BeautifulSoup(text))
＃ '部署＆lsquo; SMART QUOTES＆rsquo;！'

str(BeautifulStoneSoup(text))
＃ '部署＆＃x2018; SMART QUOTES＆＃x2019;！'

str(BeautifulSoup(text, smartQuotesTo="xml"))
＃ '部署＆＃x2018; SMART QUOTES＆＃x2019;！'

BeautifulSoup(text, smartQuotesTo=None).contents[0]
＃ 你在那里发布了“麦克风报价！”
```

输出文档



你可以使用`str`函数将Beautiful Soup文档（或者它的子集）转换为字符串，或者使用它的代码> prettify或`renderContents`。你也可以使用`unicode`函数以Unicode字符串的形式获得。

`prettify`方法添加了一些换行和空格以便让文档结构看起来更清晰。它也将那些只包含空白符的，可能影响一个XML文档意义的文档节点（节点）剔除（strip out）。 `str`和`unicode`函数不会剔除这些节点，他们也不会添加任何空白符。

看看这个例子：

```
from BeautifulSoup import BeautifulSoup
doc = "<html><h1>Heading</h1><p>Text"
soup = BeautifulSoup(doc)

str(soup)
＃ '<HTML> <H1>标题</ H1> <P>文本</ p> </ HTML>'
soup.renderContents()
＃ '<HTML> <H1>标题</ H1> <P>文本</ p> </ HTML>'
soup.__str__()
＃ '<HTML> <H1>标题</ H1> <P>文本</ p> </ HTML>'
unicode(soup)
＃ 的u '<HTML> <H1>标题</ H1> <P>文本</ p> </ HTML>'

soup.prettify()
＃ '<html> \ n <h1> \ n标题\ n </ h1> \ n <p> \ n文字\ n </ p> \ n </ html>'

print soup.prettify()
＃ <HTML>
＃  <H1>
＃   标题
＃  </ H1>
＃  <P>
＃   文本
＃  </ p>
＃ </ HTML>
```

可以看到使用文档中的标签时成员 `str`状语从句：`renderContents`报道查看的查询查询结果的英文不同的。

```
heading = soup.h1
str(heading)
＃ '<H1>标题</ H1>'
heading.renderContents()
＃ '标题'
```

当你调用`__str__`，`prettify`或者`renderContents`时，你可以指定输出的编码。默认的编码（`str`使用的）是UTF-8。下面是处理ISO-8851-1的串并以不同的编码输出同样的串的例子。

```
from BeautifulSoup import BeautifulSoup
doc = "Sacr\xe9 bleu!"
soup = BeautifulSoup(doc)
str(soup)
＃ 'Sacr \ xc3 \ xa9 bleu！' ＃UTF-8
soup.__str__("ISO-8859-1")
＃ 'Sacr \ xe9 bleu！'
soup.__str__("UTF-16")
＃ '\ xff \ xfeS \ x00a \ x00c \ x00r \ x00 \ xe9 \ x00 \ x00b \ x00l \ x00e \ x00u \ x00！\ x00'
soup.__str__("EUC-JP")
＃ 'Sacr \ x8f \ xab \ xb1 bleu！'
```

美果汤会将原始的编码声明改为新的编码。也就是说，你载入一个HTML文档到`BeautifulSoup`后，在输出它，不仅HTML被清理过了，而且可以明显的看到它已经被转换为UTF-8。

这是HTML的例子：

```
from BeautifulSoup import BeautifulSoup
doc = """<html>
<meta http-equiv="Content-type" content="text/html; charset=ISO-Latin-1" >
Sacr\xe9 bleu!
</html>"""

print BeautifulSoup(doc).prettify()
＃ <HTML>
＃  <meta http-equiv =“Content-type”content =“text / html; charset = utf-8”/>
＃  Sacrébleu！
＃ </ HTML>
```

这是XML的例子：

```
from BeautifulSoup import BeautifulStoneSoup
doc = """<?xml version="1.0" encoding="ISO-Latin-1">Sacr\xe9 bleu!"""

print BeautifulStoneSoup(doc).prettify()
＃ <？xml version ='1.0'coding ='utf-8'>
＃ Sacrébleu！
```

剖析树



到目前为止，我们只是载入文档，然后再输出它。现在看看更让我们感兴趣的剖析树：Beautiful Soup剖析一个文档后生成的数据结构。

剖析对象（`BeautifulSoup`或 `BeautifulStoneSoup`的实例）是深层嵌套（deep-nested），精心构思的（良好连接）的数据结构，可以与XML和HTML结构相互协调。剖析对象包括2个其他类型的对象，`Tag`对象，用于操纵像<TITLE>，<B>这样的标签; `NavigableString`对象，用于操纵字符串，如“页面标题”和“这是段落”。

`NavigableString`的一些子类（`CData`， `Comment`，`Declaration`和`ProcessingInstruction`），也处理特殊XML结构它们就像。`NavigableString`一样，除了但他们被输出时，他们会被添加一些额外的数据下面是一个包含有注释（评论）的文档：

```
from BeautifulSoup import BeautifulSoup
import re
hello = "Hello! <!--I've got to be nice to get what I want.-->"
commentSoup = BeautifulSoup(hello)
comment = commentSoup.find(text=re.compile("nice"))

comment.__class__
＃ <class'BeautifulSoup.Comment'>
comment
＃ “我必须很高兴得到我想要的东西。”
comment.previousSibling
＃ u'Hello！“

str(comment)
＃ “<！ - 我必须很高兴得到我想要的东西.-->”
print commentSoup
＃ 你好！<！ - 我必须很高兴得到我想要的东西.-->
```

现在，深入我们研究一下我们开头和结尾使用的那个文档：

```
from BeautifulSoup import BeautifulSoup 
doc = ['<html><head><title>Page title</title></head>',
       '<body><p id="firstpara" align="center">This is paragraph <b>one</b>.',
       '<p id="secondpara" align="blah">This is paragraph <b>two</b>.',
       '</html>']
soup = BeautifulSoup(''.join(doc))

print soup.prettify()
＃ <HTML>
＃  <HEAD>
＃   <TITLE>
＃    页面标题
＃   </ TITLE>
＃  </ HEAD>
＃  <BODY>
＃   <p id =“firstpara”align =“center”>
＃    这是段落
＃    <B>
＃     一
＃    </ B>
＃    。
＃   </ p>
＃   <p id =“secondpara”align =“blah”>
＃    这是段落
＃    <B>
＃     二
＃    </ B>
＃    。
＃   </ p>
＃  </ BODY>
＃ </ HTML>
```

`Tag`的属性



`Tag`和`NavigableString`对象有很多有用的成员，在 [导航剖析树](https://www.crummy.com/software/BeautifulSoup/bs3/documentation.zh.html#Navigating%20the%20Parse%20Tree)和 [搜索剖析树](https://www.crummy.com/software/BeautifulSoup/bs3/documentation.zh.html#Searching%20the%20Parse%20Tree)中我们会更详细的介绍。现在，我们先看看这里使用的成员`Tag`：属性

SGML标签有属性：。例如，在[上面那个HTML](https://www.crummy.com/software/BeautifulSoup/bs3/documentation.zh.html#The%20document%20above) 中每个<P>标签都有“id”属性和“align”属性。你可以将`Tag`看成字典来访问标签的属性：

```
firstPTag, secondPTag = soup.findAll('p')

firstPTag['id']
＃ u'firstPara”

secondPTag['id']
＃ u'secondPara”
```

`NavigableString`对象没有属性;只有`Tag`对象有属性。

## 导航剖析树



`Tag`对象都有如下含有所有的成员的列表（尽管，某些实际的成员值可能为`None`）。 `NavigableString`对象也有下面这些成员，除了`contents`状语从句：`string`成员。

### `parent`



上面那个[例子](https://www.crummy.com/software/BeautifulSoup/bs3/documentation.zh.html#The%20document%20above)中，<HEAD> `Tag`的父是<HTML> `Tag`。<HTML> `Tag`的父是`BeautifulSoup`剖析对象自己。剖析对象的父是`None`。利用`parent`，你可以向前遍历剖析树。

```
soup.head.parent.name
＃ u'html”
soup.head.parent.parent.__class__.__name__
＃ 'BeautifulSoup'
soup.parent == None
＃ 真正
contents
```



使用`parent`向前遍历树。使用`contents`向后遍历树。 `contents`的英文`Tag`的有序列表， `NavigableString`对象包含在一个页面元素内。最只有高层座数的剖析对象状语从句： `Tag`对象有`contents`。 `NavigableString`只有字符串，不能包含子元素，因此他们也没有`contents`。

在上面的[例子](https://www.crummy.com/software/BeautifulSoup/bs3/documentation.zh.html#The%20document%20above)中， `contents`的第一个<P> `Tag`是个列表，包含一个 `NavigableString`（“这是段落”），一个<B> `Tag`，和其他的 `NavigableString`（“。”）。而`contents`的<B> `Tag`：包含一个`NavigableString`（“一“）的列表。

```
pTag = soup.p
pTag.contents
＃ [这是段落'，<b>一个</ b>，你'。']
pTag.contents[1].contents
＃ [u'one']
pTag.contents[0].contents
＃ AttributeError：'NavigableString'对象没有属性'contents'
string
```



为了方便，如果一个标签只有一个子节点且是字符串类型，这个自己可以这样访问 `tag.string`，等同于`tag.contents[0]`的形式。在上面的[例子](https://www.crummy.com/software/BeautifulSoup/bs3/documentation.zh.html#The%20document%20above)中， `soup.b.string`是个`NavigableString`对象，它的值是Unicode字符串“一”。这是剖析树中<B> `Tag`的第一个字符串。

```
soup.b.string
＃ u'one”
soup.b.contents[0]
＃ u'one”
```

但是`soup.p.string`是`None`，剖析中的第一个<P> `Tag` 拥有多个子元素。`soup.head.string`也为`None`，虽然<HEAD> Tag只有一个子节点，但是这个子节点是`Tag`类型（<TITLE> `Tag`），不是`NavigableString`。

```
soup.p.string == None
＃ 真正
soup.head.string == None
＃ 真正
nextSibling`和`previousSibling
```



使用它们你可以跳往在剖析树中同等层次的下一个元素。在上面的[文档中](https://www.crummy.com/software/BeautifulSoup/bs3/documentation.zh.html#The%20document%20above)，<HEAD> `Tag`的`nextSibling`是<BODY> `Tag`，因为<BODY> `Tag`是在<html> `Tag`的下一层。<BODY>标签的`nextSibling`为`None`，因为<HTML>下一层没有标签是直接的在它之后。

```
soup.head.nextSibling.name
＃ u'body”
soup.html.nextSibling == None
＃ 真正
```

相应的<BODY> `Tag`的`previousSibling`是<HEAD>标签，<HEAD> `Tag`的`previousSibling`为`None`：

```
soup.body.previousSibling.name
＃ u'head”
soup.head.previousSibling == None
＃ 真正
```

更多例子：<P> `Tag`的第一个`nextSibling`是第二个<P> `Tag`。第二个<P>`Tag里的<B>Tag的previousSibling是NavigableString"This is paragraph"。 这个NavigableString的previousSibling是None, 不会是第一个<P> Tag里面的任何元素。`

```
soup.p.nextSibling
# <p id="secondpara" align="blah">This is paragraph <b>two</b>.</p>

secondBTag = soup.findAlll('b')[1]
secondBTag.previousSibling
# u'This is paragraph'
secondBTag.previousSibling.previousSibling == None
# True
This document (source) is part of Crummy, the webspace of Leonard Richardson (contact information). It was last modified on Thursday, February 02 2012, 13:11:38 Nowhere Standard Time and last built on Wednesday, November 14 2018, 08:00:01 Nowhere Standard Time.Crummy is © 1996-2018 Leonard Richardson. Unless otherwise noted, all text licensed under a Creative Commons License.Document tree:http://www.crummy.com/software/BeautifulSoup/bs3/documentation.zh.htmlSite Search:
Crummy is © 1996-2018 Leonard Richardson. Unless otherwise noted, all text licensed under a Creative Commons License.
```