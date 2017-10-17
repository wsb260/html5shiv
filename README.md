# html5shiv
html5shiv使得传统浏览器支持部分HTML5元素并提供相应的基本样式

# html5shiv有什么用？

html5shiv使得传统浏览器支持部分HTML5元素并提供相应的基本样式。传统浏览器，即主流浏览器的低版本，包括IE6-9、Safari4.x和Firefox 3.x等。

# html5shiv怎么用？

```html
下载html5shiv，在html文档的head标签里引入链接。
注意：引入的文件路径要正确
```
```javascript
<!DOCTYPE html>
<html>
<head>
  <meta charset="utf-8">
    <title></title>
    <!-- 在这里引入html5shiv -->
    <!--[if lt IE 9]>
    <script src="html5shiv.min.js"></script>
  <![endif]-->
</head>
<body>
    <header>
        <h1>如何使用html5shiv</h1>
        <p>引入html5shiv后就可以愉快地让IE6-9支持html5新元素了！</p>
    </header>
</body>
</html>
```

#html5shiv支持哪些html5元素？
```html
目前最版本为3.7.3，默认支持

abbr article aside audio bdi canvas data datalist details dialog figcaption figure footer header hgroup main mark meter nav output picture progress section summary template time video

html5shiv并不能让传统低版本浏览器正常实现html5元素所有功能，而是对不支持html5元素，如video和audio等，当成相应的成块状或行内元素进行显示，并可以为html5元素添加样式。

可以通过JavaScript定制需要支持的html5元素，如通过在head中并且在引入html5shiv之前插入以下代码
```
```javascript
<!--[if lt IE 9]>
<script>
  window.html5 = {
  'elements': 'abbr article custom elements',
  'shivCSS': true,
  'shivMethods': true
  };
</script>
<script src="html5shiv.min.js"></script>
<![endif]-->
```

```html
其中elements的属性值是html5元素标签，可以是由空格分隔的字符串或数组；shivCSS的属性类型为Boolean，默认为true，给html5元素添加CSS样式；shivMethods的属性类型为Boolean，默认为true，覆盖createElement和createDocumentFragment方法。

注意：

    定制的html5元素会覆盖默认元素，所以elements的属性值要包含文档中出现的所有html5元素。
    shivCSS主要为块状元素添加dispaly:block。若shivCSS: false，默认所有元素按照行内元素显示。
    当使用第三方库或框架，如Jquery 1.7+，已经解决为IE6等浏览器动态创建元素，无需重写createElemnt方法，所以 shivMethods可以设置为false

```

```javascript
article,aside,dialog,figcaption,figure,footer,header,hgroup,main,nav,section {
    display:block
}
mark {background:#FF0;color:#000}
template{display:none}
```

# 不用html5shiv解决问题

```html
有时，页面中只需用到section header footer article等少数几个html5语义化元素。能不能不通过html5shiv，自己写JavaScript实现低版本浏览器支持这些元素呢？

其实很简单，把下面的代码嵌入到head中。
```
```javascript
<!--[if lt IE 9]>
  <script>
   ;(function(){
     var elements = ['section','header','footer','article'];
     var i;
     for(i in elements){
       document.createElement(elements[i]);
     }
   })();
  </script>
<![endif]-->
```
再对html5元素添加相应样式

```css
<style>
  section, header, footer, article {display: block}
</style>
```

深入html5shiv

html5shiv可以说是解决html5兼容问题的一个小框架。阅读并[html5shiv源代码](https://github.com/aFarkas/html5shiv)有助于理解html5shiv的工作原理，并学会自己开发一套符合工作需要的html5框架来支持html5。

