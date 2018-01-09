---
layout: post
title: 百度网盘pcs下载地址获取
date: 2018-01-09 14:36:40
categories: 搞机
tags: 技巧 pcs 百度网盘 
excerpt: 百度网盘下载大文件限速，几十k的速度下载几个
G，玩呢？微云也是慢的出奇，但是百度目前还可以通过获取pcs下载地址的方式，通过其他下载器来提升下载速度，经常可以获得宽带满速效果。
---
# PCS下载地址获取方法
>之所以这个方法可以使用，是因为到写这篇文章为止，百度云下载还是地址解析，所以只要获取到网盘的pcs下载地址就可以突破百度网盘的下载限速

### 如下方法：

一：如果是别人分享的，就保存到自己的网盘，然后再分享出去；如果本身自己的，也是要分享出去

二：必须是 创建公开链接，私密链接不行

三：进入到自己的分享链接 四：按F12进入开发者模式，找到Console

五：在这里复制粘贴这代码到这里，按回车键 控制台输入以下代码：  
``` $.ajax({
type: "POST",
url: "/api/sharedownload?sign="+yunData.SIGN+"&timestamp="+yunData.TIMESTAMP,
data: "encrypt=0&product=share&uk="+yunData.SHARE_UK+"&primaryid="+yunData.SHARE_ID+"&fid_list=%5B"+yunData.FS_ID+"%5D",
dataType: "json",
success: function(d){ 
window.location.href = d.list[0].dlink;
}
});
```  
六：按了回车键之后，就会弹出下载链接了。此时一般都会弹出浏览器的自带下载，如果浏览器安装了下载插件比如IDM或者是其他国产浏览器里面的自建下载器的话，都可以产生比较好的下载效果。
>此文章截至2018-01-09仍然有效，段时间内百度应该不会改变这个地址解析的下载方式，方法是从网上找到的，在此分享