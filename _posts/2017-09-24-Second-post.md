---
layout: post           
title: Second post!   
subtitle: It's a post！ye
image: /img/hello_world.jpeg    
bigimg: /img/path.jpg     
tags: [random, exciting-stuff]
---  

## 把github装修了一下  
> 纪念这历史性的一刻，换了新家，哈哈！
> 发一篇测试推文，以后我会常来的。
> 下面测试一下markdown语法

1、表格：

| Number | Next number | Previous number |
| :------ |:--- | :--- |
| Five | Six | Four |
| Ten | Eleven | Nine |
| Seven | Eight | Six |
| Two | Three | One |

2、加载图片

![Crepe](http://s3-media3.fl.yelpcdn.com/bphoto/cQ1Yoa75m2yUFFbY2xwuqw/348s.jpg)


3、代码块
  无高亮
~~~
var foo = function(x) {
	return(x + 5);
}
foo(3)
~~~

  有高亮代码块
	And here is the same code with syntax highlighting:

```javascript
var foo = function(x) {
	return(x + 5);
}
foo(3)
```

  带有行数和高亮的代码块
	And here is the same code yet again but with line numbers:

{% highlight javascript linenos %}
var foo = function(x) {
	return(x + 5);
}
foo(3)
{% endhighlight %}

  ## Boxes
  You can add notification, warning and error boxes like this:

  ### Notification公告栏模块

{: .box-note}
**Note:** This is a notification box.

### Warning警告提示模块

{: .box-warning}
**Warning:** This is a warning box.

### Error 错误提示模块

{: .box-error}
**Error:** This is an error box.