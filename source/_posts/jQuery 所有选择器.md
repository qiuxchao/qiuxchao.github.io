---
title: jQuery 所有选择器
date: 2020-01-15 08:08:08
# top: true
categories: jQuery
tags: jQuery
---

# jQuery 所有选择器
--------------------------------------------------------------------------------
## 基本选择器

 - `#id	`		id 选择器

```javascript
// id 选择器
$("#demo").css("border", "2px solid green");
```

- `element `   元素名选择器

```javascript
// 元素名选择器
$("li").css("border", "2px solid orange");
```


`.class`    	class 选择器

```javascript
// class 选择器
$(".box2").css("border", "2px solid red");
```

`*  `   	通配符选择器

```javascript
// 通配符选择器
$("*").css("border", "2px solid pink");
```


`selector1, selector2, selectorN `   	分组选择器

```javascript
// 分组选择器
$("#demo, .box2, ul").css("border", "2px solid blue");
```

--------------------------------------------------------------------------------
## 层级选择器

`ancestor descendant`        后代选择器

```javascript
// 后代选择器
$("ul li").css("border", "2px solid yellow");
```


`parent > child `         直接子元素选择器

```javascript
// 直接子元素选择器
$("ul > li").css("border", "2px solid purple");
```


`prev + next `           	相邻兄弟选择器

```javascript
// 相邻兄弟选择器
$("#demo + li").css("border", "2px solid green");
```


`prev ~ sibings`        后续兄弟选择器

```javascript
// 后续兄弟选择器
$("#demo ~ li").css("border", "2px solid red");
```


--------------------------------------------------------------------------------
## 基本筛选器

`:first `               选择指 定的元素是同级元素中的第一个的元素

```javascript
// 选择指定的元素是同级元素中的第一个的元素
$("li:first").css("border", "2px solid red");
```


`:not(selector)`     在指定 的元素范围中排除元素

```javascript
// 在指定的元素范围中排除元素
$("li:not(.box2)").css("border", "2px solid green");
```


`:even`           选择 指定的元素范围中为奇数行的元素

```javascript
// 选择指定的元素范围中为奇数行的元素
$("li:even").css("border", "2px solid yellow");
```


`:odd`              选择 指定的元素范围中为偶数行的元素

```javascript
 // 选择指定的元素范围中为偶数行的元素
$("li:odd").css("border", "2px solid blue");
```


`:eq(index)`      选择 指定的元素范围中给定索引的元素（索引从0开始）

```javascript
// 选择指定的元素范围中指定索引的元素（索引从0开始）
$("li:eq(0)").css("border", "2px solid purple");
```

`:gt(index)`      选择 指定的元素范围中大于给定索引值的元素

```javascript
// 选择指定的元素范围中大于给定索引值的元素
$("li:gt(0)").css({"border": "2px solid orange", "background-color": "pink"});
```

`:lt(index)`      选择 指定的元素范围中小于给定索引值的元素

```javascript
// 选择指定的元素范围中大于给定索引值的元素
$("li:lt(2)").css("border", "2px solid green");
```

`:last`              选择 指定的元素范围中的最后一个元素

```javascript
// 选择指定的元素范围中的最后一个元素
$("li:last").css("border","2px solid orange");
```

`:lang()`           选择 元素的属性 lang 为给定值的元素

```javascript
// 选择元素的属性 lang 为给定值的元素
$("li:lang(en)").css("border","2px solid pink");
```


`:header `          选择 所有的标题元素（h1 ~ h6）

```javascript
// 选择所有的标题元素（h1 ~ h6）
$(":header").css({
    "border" : "2px solid orange",
    "background-color" : "pink"
});
```


`:focus `             过滤 出当前获取焦点的元素

`:root `               选择 该文档的根元素，即 <html></html> 元素

```javascript
// 选择根元素
$(":root").css("background-color", "pink");
```


`:target ` 		过滤出 锚点正在指向的元素

```javascript
$(":target").css("border", "2px solid red");
```


`:animated`	获取 正在执行动画的元素

--------------------------------------------------------------------------------
## 内容选择器

`:contains(text)` 	获取 包含指定内容的元素

```javascript
$("li:contains('2')").css("border", "2px solid orange");
```


`:has(selector)	`	获取 后代元素拥有满足指定的选择器条件的元素

```javascript
$("li:has('.box')").css('border', "2px solid yellow");
```


`:empty`		获取 既没有内容，又没有子元素的元素

```javascript
$("li:empty").css("border", "2px solid orange");
```


`:parent`		获取 要么有内容，要么有子元素的元素（跟 empty 相反）
 

```javascript
$("li:parent").css("border", "2px solid orange");
```



--------------------------------------------------------------------------------
## 可见性选择器
`:visible	`	选择 所有可见的元素

```javascript
$(":visible").css("border", "2px solid orange");
```


`:hidden`		选择 所有不可见的元素

```javascript
$(":hidden").css("border", "2px solid orange");
```



--------------------------------------------------------------------------------
## 属性选择器
`[attr]`		选择 包含方括号中属性的元素

```javascript
$("li[name]").css("border", "2px solid green");
```


`[attr='value'] `  选择 属性值为指定的值的元素

```javascript
$("li[name='test']").css("border", "2px solid green");
```


`[attr!='value'] ` 	选择 属性值不为指定的值的元素

```javascript
$("li[name!='test']").css("border", "2px solid green");
```


`[attr^='v']`   	选择 属性值为指定的字符开头的元素

```javascript
$("li[name^='t']").css("border", "2px solid green");
```


`[attr$='e']`		选择 属性值为指定的字符结尾的元素

```javascript
$("li[name$='t']").css("border", "2px solid green");
```


`[attr*='l']	`	选择 属性值中包含指定的字符的元素

```javascript
$("li[name*='t']").css("border", "2px solid green");
```



--------------------------------------------------------------------------------
## 子元素选择器

`:first-child `		选择 是所有兄弟元素中的第一个的元素

```javascript
$("li:first-child").css("border", "2px solid red");
```


`:last-child`		选择 是所有兄弟元素中的最后一个的元素（与 first-child 相反）

```javascript
$("li:last-child").css("border", "2px solid orange");
```


`:nth-child(n)`		选择 是所用兄弟元素中第 n  个的元素（从前往后数）

```javascript
$("li:nth-child(3)").css("border", "2px solid pink");
```


`:nth-last-child(n)`	选择 是所有兄弟元素中倒数第 n 个的元素（从后往前数，跟 nth-child 相反）

```javascript
$("li:nth-last-child(3)").css("border", "2px solid yellow");
```


`:only-child `		选择 没有兄弟元素的元素

```javascript
$("li:only-child").css("border", "2px solid green");
```


`:first-of-type`		选择 所有兄弟元素里面相同标签的第一个元素

```javascript
$("li:first-of-type").css("border", "2px solid blue");
```


`:last-of-type`		选择 所有兄弟元素里面相同标签的最后一个元素

```javascript
$("li:last-of-type").css("background-color", "blue");
```


`:nth-of-type(n)`		选择 所有兄弟元素里面相同标签的第 n 个元素（从前往后数）

```javascript
$("li:nth-of-type(3)").css("border", "2px solid red");
```


`:nth-last-child(n)	`	选择 所有兄弟元素里面相同标签的倒数第 n 个元素（从后往前数）

```javascript
$("li:nth-last-of-type(3)").css("background-color", "green");
```


`:only-of-type`			选择 所有兄弟元素标签中没有相同标签的元素

```javascript
 $("li:only-of-type").css("border", "2px solid orange");
```



--------------------------------------------------------------------------------
## 表单选择器

`:input`			选择 所有的表单元素 （input select testarea button ......）

```javascript
$(":input").width(40).height(40).css("border", "1px solid red");
```


`:text`			选择 type 属性为 text 的 input 元素

```javascript
$(":text").css("border", "1px solid green");
```


`:password`		选择 type 属性为 password 的 input 元素

```javascript
$(":text").css("border", "1px solid green");
```


`:radio	`		选择 type 属性为 radio 的 input 元素

```javascript
$(":radio").width(100).height(100);
```


`:checkbox`		选择 type 属性为 checkbox 的 input 元素

```javascript
$(":checkbox").width(100).height(100);
```


`:file`				选择 type 属性为 file的 input 元素

```javascript
$(":file").css("border", "2px solid orange");
```


`:submit`			选择 具有提交功能的按钮

```javascript
$(":submit").css("border", "2px solid orange");
```


`:reset`			选择 具有重置功能的按钮

```javascript
$(":reset").css("border", "2px solid red");
```


`:button`			选择 `botton` 标签、`<input type='button'>`

```javascript
$(":button").css("border", "2px solid red");
```



--------------------------------------------------------------------------------
## 表单对象选择器

`:disabled`		选择 所有禁用的表单元素

```javascript
$(":disabled").css("background-color", "orange" );
```


`:enabled`			选择 所有启用的表单元素

```javascript
$(":enabled").css("background-color", "orange" );
```


`:checked`		选择 默认选中的表单元素

```javascript
$(":checked").width(100).height(100);
```


`:selected`		选中 默认选中的 option 元素

```javascript
$(":selected").css("border", "2px solid orange");
```



--------------------------------------------------------------------------------
## 混淆选择器

`$.escapeSelecotr(selector)	`		用于选择 className 或 idName 是有特殊符号的
<div class="box" id="#item"></div>

```javascript
$("#" + $.escapeSelector("#item")).css("background-color", "green");
```



























































