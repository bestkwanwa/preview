# DOM

## javascript 的组成部分
- DOM (document object model) 文档对象模型
- BOM (browers object model) 浏览器对象模型
- ECMAScript js 的核心

![DOM树](./DOMltree.gif)

## DOM 节点
- 节点分类
  - 元素节点：每个 HTML元素	
    - 属性节点：HTML元素的属性
  - 文本节点：HTML元素内的文本	
    - 注释节点：注释 <!---->
  - 文档节点：整个文档document		
- 节点类型 --- nodeType
  - 元素节点：1	
    - 属性节点：2
  - 文本节点：3	
    - 注释节点：8
  - 文档节点：9
- 节点名称 --- nodeName
  - 元素节点：与标签名相同	
  - 文本节点：为#text	
  - 注释节点：为#comment
  - 文档节点：为#document    

> 1- 元素节点 （大写标签名称）
> 3 - 文本节点 -  (#text) 
> 8 - 注释节点 -  (#comment)
>  9 - document -  (#document)
>  10 - 文档声明 - (html)

## DOM关系
- childNodes 子节点(包含所有节点: 文本节点、注释节点、元素节点……)
- children 子元素 (只包含元素节点)
- firstChild 第0个子节点
- firstElementChild 第0个子元素
- lastChild 最后一个子节点
- lastElementChild 最后一个子元素
- nextSibling 下一个兄弟节点
- nextElementSibling 下一个兄弟元素
- previousSibling 上一个兄弟节点
- previousElementSibling 上一个兄弟元素
- parentNode 父节点
- parentElement 父元素 **父节点父元素都一样**
- offsetParent 定位父级  (元素根据定位的这个父级) 没有定位则跟上面两个一样

## nodeList和HTMLCollection 

- nodeList
  - childNodes
  - querySelectorAll
- HTMLCollection 
     - children
     - tElementsByTagName
     - getElementsByClassName

**nodeList 有 forEach 方法，但是 HTMLCollection 没有forEach**

**HTMLCollection 每次调用时都会动态的去获取, nodeList 中 childNodes 有动态更新，但是querySelectorAll 就不会动态更新**



## DOM 属性操作
注意 . 和 [] 都是 ECMAScript 中对象的属性操作（合法属性：w3c 规定的元素的属性,都存到这个对象中），对象属性的值会被存在内存中, 想要直接获取存在 文档中属性，或者 想把一个属性设置在文档中我们需要使用DOM 的属性操作
- el.attributes 元素所有属性的集合
- el.getAttribute("attr") 获取属性
- el.setAttribute("attr","val") 设置属性
- el.removeAttribute("attr") 移出属性
- el.hasAttribute("attr") 判断是否有这个属性
- 只要操作了innerHTML 元素的所有子元素上，存在内存中的事件和相关的属性都会丢失。如果希望元素的某些属性在操作了父级的innerHTML 之后，还存在就把这个属性加在 DOM 中

- 两种操作不互通。ECMA 的属性操作，操作的是对象，具体的数据存在内存中，可以存储各种类型数据。DOM 的属性操作，值是存在文档中,类型只能是字符串，不是字符串的话，也会被转成字符串

## data 自定义属性
- 在标签中定义data自定义属性：data-key="value";
- 在js操作该元素的 data 自定义属性：el.dataset
    - 获取：el.dataset.key
    - 设置: el.dataset.key = "value"

## 节点操作

### 创建节点
语法：element document.createElement("tagName"); 创建一个节点
参数：tagName 标签名称
返回值：创建好的节点

### 向页面中添加节点
- el.appendChild(node)  在元素的末尾添加一个子级
- el.insertBefore(newNode,oldNode) 在 oldNode 前边添加入 newNode 
- 在使用 appendChild 和 insertBefore时，如果添加是一个页面上已经存在的节点，会先从原位置删除，然后在添加到新的位置去。

### 替换节点

- parent.replaceChild(newChild,oldChild) - 返回值是替换掉的旧节点
      如果替换的节点是一个已有节点的话，会先把这个节点，从原先的位置删除，然后放入我们的新位置

### 删除节点
- parent.removeChild(el) 删除掉某个子元素
- Node.remove() - 把 node 从 DOM 中删除 返回undefined ，新方法

### 克隆节点
- node.cloneNode(deep) 不克隆事件
    - deep: 默认为false
    - deep 为 true, 克隆元素及属性，以及元素的内容和后代
    - deep 为 false, 只克隆元素本身，及它的属性

## 文档碎片

- createDocumentFragment() - 返回创建好的一个新的空白的文档片段

> `DocumentFragments` 是DOM节点。它们不是主DOM树的一部分。通常的用例是创建文档片段，将元素附加到文档片段，然后将文档片段附加到DOM树。在DOM树中，文档片段被其所有的子元素所代替。
>
> 因为文档片段存在于**内存中**，并不在DOM树中，所以将子元素插入到文档片段时不会引起页面[回流](https://developer.mozilla.org/zh-CN/docs/Glossary/Reflow)（对元素位置和几何上的计算）。因此，使用文档片段通常会带来更好的性能。

## 元素的尺寸获取
- offset
    - offsetWidth  可视宽度  
    
      可视宽高 =  width(height) + padding + border
    
- offsetHeight 可视高度 
    
    - offsetLeft   距离定位父级的left坐标  元素距离定位父级左上角的距离
    
    - offsetTop    距离定位父级的top坐标
    
- client
    - clientWidth  可视宽度 - border  
    
      clientWidth/clientHeight =  width(height) + padding;
    
- clientHeight 可视高度 - border
    
    - clientTop    上边框宽度
    
    - clientLeft   左边框宽度 
    
- scroll
    - scrollWidth   内容宽度  
    
      内容高度，如果内容高度比元素高度要高，scrollHeight 就是内容，否则就是元素高度
    
- scrollHeight  内容高度
    
    - scrollLeft    左右滚动距离
    
    - scrollTop     上下滚动距离
    
- getBoundingClientRect() - 新方法
    - left   元素左侧距离可视区左侧距离
    - top    元素顶部距离可视区顶部距离
    - right  元素右侧距离可视区左侧距离
    - bottom 元素底部距离可视区顶部距离
    - width  可视宽度 
    - height 可视高度

```javascript
// 获取元素相对整个页面的位置
function getPageOffset(el){
    let left = el.offsetLeft;
    let top =  el.offsetTop;
    while(el.offsetParent){
        el = el.offsetParent;
        left += el.offsetLeft + el.clientLeft;
        top += el.offsetTop + el.clientTop;
    }
    return {left,top};
}
```



## 表格相关操作
- tBodies、tHead、tFoot、rows、cells

> table.tHead 获取 tHead
> table.tBodies 获取的就是 tbody
>         rows 获取 行(tr)
>         cells 获取单元格 (th,td)
> table.tFoot

## 其他
- createDocumentFragment
- NodeList 和 HTMLCollection 