# XPath

## 簡介
XML Path Language (XPath)，用於在XML文件中透過元素核屬性進行查詢。XPath基於XML的樹狀結構，提供在結構樹中查找節點的功能，常用於小型的查詢語言。

## XPath node

### 節點 (Node), 基本值 (Atomic value), 項目 (Item)
在XPath中主要有七種類型的節點(Node):元素(element)、屬性(attribute)、文本(text)、命名空間(namespace)、處理指令(processing-instruction)、註釋(comment)及文檔節點(根節點, document nodes)，範例如下:

	<?xml version="1.0" encoding="ISO-8859-1"?>

	<bookstore> // document nodes
	
	<book> // element
	  <title lang="en">Harry Potter</title> // lang="en" = attrbute, "en" = Atomic value
	  <author>J K. Rowling</author> // J K. Rowling = Atomic value
	  <year>2005</year>
	  <price>29.99</price>
	</book>
	
	</bookstore>

項目 (Item): Item can be a node or a atomic value

### 節點關係
1.父子關係 (Parent, Children)
2.同胞 (Sibling)
3.祖先與後代 (Ancestor, Descendant)

	<bookstore>
	
	<book>
	  <title>Harry Potter</title>
	  <author>J K. Rowling</author>
	  <year>2005</year>
	  <price>29.99</price>
	</book>
	
	</bookstore>

ex:

 - &lt;title&gt; 之父元素為 &lt;book&gt; ; &lt;book&gt; 之子元素為 &lt;title&gt;, &lt;author&gt;, &lt;year&gt; 以及 &lt;price&gt;
 - &lt;title&gt;, &lt;author&gt;, &lt;year&gt;, &lt;price&gt; 互為sibling關係
 - &lt;title&gt; 之祖先元素有 &lt;book&gt;, &lt;bookstore&gt; ; 而 &lt;bookstore&gt; 元素之後代元素除了 &lt;book&gt; 之外還有 &lt;title&gt;, &lt;author&gt;, &lt;year&gt; 以及 &lt;price&gt; 等等


## XPath語法
XPath 使用路徑表達式來選取XML文檔中的節點或節點集，透過路徑(path)或是步(steps)選取。

### 表達式
| 表達式 |描述|  
| ------ |----|
|node|選取此節點下所有子節點|  
|/|根節點選取|  
|//|搜尋自該節點下文件中所有符合的節點|
|.|選取目前的node|
|..|選曲目前的node之父節點|  
|@|選取attrbute|

 Example	
	
	<?xml version="1.0" encoding="ISO-8859-1"?>
	
	<bookstore>
	<book>
	  <title lang="eng">Harry Potter</title>
	  <price>29.99</price>
	</book>
	<book>
	  <title lang="eng">Learning XML</title>
	  <price>39.95</price>
	</book>
	</bookstore>

|ex|描述|
|-|-|
|bookstore|選取所有bookstore下所有子元素|
|/bookstore|選取根元素bookstore|
|bookstore/book|選取bookstore下一層的所有book元素|
|//book|搜尋整份文件下的book元素|
|bookstore//book|在bookstore下，不論幾層，所有book元素|
|//@lang|搜尋所有lang屬性|

### 謂語

|ex|描述|
|-|-|
|/bookstore/book[1]|選取bookstore下的第一個book元素|
|/bookstore/book[last()]|選取bookstore下的最後一個book元素|
|/bookstore/book[last()-1]|選取bookstore下倒數第二個book元素|
|/bookstore/book[price>35.00]|選取bookstore下所有price值大於35之book元素|

### Wildcard

|Wildcard|描述|
|-|-|
|*|所有node|
|@*|所有attrbute|
|node()|任何類型的node|
|&Iota;|pipe, 選取多重路徑|