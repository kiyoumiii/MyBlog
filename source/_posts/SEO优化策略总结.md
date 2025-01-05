---
title: SEO优化策略总结
date: 2024-09-17 20:45:20
categories:
- [前端开发]
tags:
- [前端开发]
---
# SEO优化全方位解决方案
SEO代表搜寻引擎最佳化/搜寻引擎优化（英文全名 Search Engine Optimization，简称 SEO），是指通过了解搜寻引擎的自然排名的算法逻辑，以提高目标网站在有关搜寻引擎内排名的方式。
网站的 SEO 至关重要，它可以让你的网站获得更好的排名和流量，从而提高网站知名度。对于一些盈利的网站，做好 SEO，还可以以低成本提高投资回报率。
网站 SEO 是长线工作，在做好一些基础的配置之后，更重要的是后期的维护，比如定期更新网站动态文章，不断寻找优质外链资源等。

## 一、TDK 优化

TDK 是
- Title（页面标题）
- Meta Description（页面描述）
- Meta Keywords（页面关键词）
P.S.但是由于一些原因，各大主流搜索引擎基本都已经大大降低甚至移除了 <keywords> 对排名的影响
但有些搜索引擎还会参考，如必应，目前 keywords 标签仍然对排名有一定影响。

title 标签-网站名片
当前设置：
``` html
<title>OK简历 - AI简历优化，免费在线使用，一键导出打印</title>
```
参考竞品：
``` html
<title>简历模板_个人简历模板_求职简历模板 - Canva可画</title>
<title>超级简历WonderCV - HR推荐简历模板,智能简历制作工具,专业中英文简历模板免费下载</title>
```

META 标签-网站信息
当前设置：
``` html
<meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta
      name="keywords"
      content="OK简历,写简历,求职,找工作,简历模板"
    />
    <meta
      name="description"
      content="从一份OK的简历开始，笑傲职场！我们不仅懂你的才华，更懂招聘者的心理。AI智能一键优化简历，让你从“简历海”中脱颖而出，笑傲职场江湖。"
    />
    <meta name="viewport" content="width=device-width,initial-scale=1.0">
    <meta name="author" content="霖承科技" />
    <meta name="robots" content="index, follow" />
    <meta name="googlebot" content="index, follow" />
    <meta name="application-name" content="OK简历" />
```
robots：用来告诉搜索机器人哪些页面需要索引，哪些页面不需要索引

Open Graph 协议标签
Open Graph 协议标签通过 OG Tags （OG 标签）实现的，它属于 Meta 标签的一种，可以用来标识网页类型和元素，让分享到社交网络的内容可以被有效的抓取，还可以控制分享的网站卡片呈现我们想要显示的内容。
``` html
<!-- 社交媒体分享展示优化 -->
    <meta property="og:title" content="OK简历">
    <meta property="og:description" content="从一份OK的简历开始，笑傲职场！我们不仅懂你的才华，更懂招聘者的心理。AI智能一键优化简历，让你从“简历海”中脱颖而出，笑傲职场江湖。">
    <meta property="og:type" content="website">
    <meta property="og:url" content="https://okjob.linchance.com">
    <meta property="og:author" content="霖承科技">
```

关于网站关键词
- keywords 关键词数量控制在 4 个左右，避免关键词堆砌；
- 合理选择长尾关键词（长尾关键词一般是 2-3 个词组成。例如，目标关键词是服装，其长尾关键词可以是男士服装、冬装等），长尾关键词虽然相对核心关键词的搜索量小很多，但是它带来的流量精准度非常高，后期的转化效果更好；
- 避免使用过于专业的词汇。过于专业的词汇的搜索量较低；
- 减少使用热门关键词，要选择合适的关键词（搜索量大、转化率高、定位精准）
当前设置：
``` html
<meta
      name="keywords"
      content="OK简历,写简历,求职,找工作,简历模板"
    />
```
参考竞品：
``` html
<meta data-n-head="true" name="keywords" content="简历制作,个人简历模板,写简历,简历网">
<meta data-n-head="ssr" property="og:keywords" content="简历模板,简历,简历模板免费下载,简历制作,英文简历,超级简历">
```
关于网站描述
- Description（页面描述）的长度最好控制在 120～200 个字符；
- Description 要让用户知道将从页面中获得什么；
- 在 Description 中合理使用行动号召（CTA）用语（例如“了解更多”、“立即获取”、“免费试用”等等……）；
- Description 应该包含页面的核心关键字；
- 为每个页面创建独一无二的 Description；

当前设置：
``` html
<meta
      name="description"
      content="从一份OK的简历开始，笑傲职场！我们不仅懂你的才华，更懂招聘者的心理。AI智能一键优化简历，让你从“简历海”中脱颖而出，笑傲职场江湖。"
    />
```
参考竞品：
``` html
<meta data-n-head="true" name="description"
        content="全民简历网是专业的在线简历制作、简历模板下载网站。提供大量原创设计的个人简历模板，包括各种职业和大学生简历模板，让求职者快速制作出高质量简历，服务超800万用户！">
```

## 二、网站质量
### 网站加载速度
网站性能是会影响到网站的 SEO 排名的，原因可想而知：
- 网站卡顿势必会大大降低网站的用户留存率；
- 如果网站加载缓慢，搜索引擎就会认为该网站对用户不友好，从而将其排名下降；
- 影响搜索引擎蜘蛛的爬取频率；
### HTML 语义化
语义化是指内容的结构化（内容语义化），选择合适的标签（代码语义化）。
 杜绝通篇 div，HTML 语义化不仅便于开发者阅读，还有利于浏览器爬虫的解析，对 seo 优化很有帮助。
 所以我们在开发时要遵循语义化的开发规范，根据页面内容，选择合适的标签，优化代码，使得网页结构更加清晰。

相比其他标签而言，h 标签在页面中的权重非常高，所以不要滥用 h 标签。要利用 h 标签告诉浏览器网页的核心内容！例如：
h1 写主标题，通常与网页 title 标签一致，可以在页面展示，一个页面最好只有一个 h1 标签。
h2 写次级标题，h3-h6 以此类推，细分网页结构。

### strong、em 标签
`<b>`和`<strong>`标签都是加粗文字的标签，其二者的区别就在于：`<b>`是为了加粗而加粗的，`<strong>`是为了强调而加粗的。
 同样斜体标签` <i> `和 `<em> `也有着相同的区别，`<em>`有强调效果。
 推荐使用`<strong> ` `<em>`，而不是 `<b>` `<i>` 等，单纯修改加粗等样式可以用 css 实现。

 当前设置：
 ``` html
<style>
      .seo-header {
        position: absolute;
        display: none;
      }
    </style>
  </head>
  <body>
    <h1 class="seo-header">
      <a href="https://https://okjob.linchance.com">OK简历网是专业的在线简历制作、AI辅写优化、简历模板下载网站，提供免费的简历创建、编辑、一键导出服务，让求职者快速制作出高质量简历！</a>
    </h1>
    <noscript>
      <strong>OK简历 - 从一份OK的简历开始，笑傲职场</strong>
    </noscript>
    <div id="app"></div>
  </body>
</html>
```

### ul ol li 标签
 这三个都是列表标签，ul 表示无序列表（unordered list），ol 表示有序列表（oredr list）， li 表示列表项（list item）。从网站优化的角度来说，在罗列多个词条的时候，最好使用列表标签，例如 使用 ul li 布局网站导航条对搜索引擎蜘蛛更加友好，也是影响搜索引擎排名的因素之一。
### img 标签
 img 图片标签的 alt 属性是图片的替换文字。
 alt 属性可以帮助蜘蛛快速理解图片的具体内容，并且在网络故障时，仍然能够爬取到图片的内容信息。

index.html 里暂时无列表标签和图片标签，如有或后续有添加需求，记得按照上面规范进行。

### 其他注意点
- SEO 的禁忌之一就是用 JS 输出重要的内容。爬虫不会读取 JS 格式的内容，所以重要的内容必须是 HTML 格式，这也就是为什么现在流行的 spa 框架都不利于 SEO 的原因之一；
- 尽量不使用 iFrame。因为搜索引擎不会抓取 iframe 内的内容，所以重要内容绝对不能放在 iframe 中；
- 如果需要截取文字，尽量用 css 实现，保证文字可以完整呈现给搜索引擎。

## 三、SEO 手段
### 各搜索引擎提交站点收录
在各个搜索引擎的站点平台提交网站收录可以缩短爬虫发现网站链接时间，加快爬虫抓取速度。
- 百度站长资源平台
ziyuan.baidu.com/?castk=LTE%…
- 谷歌网站管理员工具
www.google.cn/webmasters/
- 搜狗站长平台
zhanzhang.sogou.com/
- 360 站长平台
zhanzhang.so.com/
- 头条搜索站长平台
zhanzhang.toutiao.com/
- 必应网站管理员工具
www.bing.com/webmaster/i…
点击以上链接，站长可以查看网站的各项参数表现。
2024.09.04：尝试百度站长管理平台认证失败，后续如还有需要可以再回来尝试

### sitemap 站点地图
Sitemap，即站点地图，它是一个网站的全部 URL 列表，同时可以列出每个网址的其他元数据（上次更新的时间、更改的频率以及相对于网站上其他网址的重要程度为何等）。它可以为搜索引擎的蜘蛛进行导航，更快的找到全站中的所有链接，更全面的获取网站信息。为了保证链接的全面性和准确性，应该自动不定期更新 sitemap 站点地图。
一般网站的 sitemap 文件都会有以下两种格式：
sitemap.xml，这是大部分搜索引擎所使用的用于提交网站网址的 XML 文件；
sitemap.html，这是可直接放在网站上用于用户访问或搜索引擎快速找到全站链接的页面（每页最多 500 条，自动分页）；

网上有很多生成 sitemap 文件的站长工具，例如：
sitemap.zhetao.com/
tools.bugscaner.com/sitemapspid…

生成的 sitemap 文件一般放在项目根目录下，然后可以在各个搜索引擎的站点平台提交 sitemap.xml 文件。

当前设置：
在 xml.sitemap 网站制作 sitemap，sitemap.xml 文件暂时保存在我本地，如需提交或放在项目根目录下，上服务器前要说

### robots 文件

蜘蛛在访问一个网站时，会首先会检查该网站的根域下是否有一个叫做 robots.txt 的纯文本文件，这个文件用于指定 spider 在您网站上的抓取范围。
如果你有哪些页面不想被蜘蛛访问，则可以通过 robots 文件告诉蜘蛛不想被搜索引擎收录的部分或者指定搜索引擎只收录特定的部分。
robots 文件内容语法：
此文件主要由两种键值对组成：

User-agent:  该项的值用于描述搜索引擎蜘蛛的名字。如果该项的值设为*，则该协议对任何机器人均有效。
Disallow:  该项的值用于描述不希望被访问到的一个 URL，一个目录或者整个网站。以 Disallow 开头的 URL 均不会被搜索引擎蜘蛛访问到。任何一条 Disallow 记录为空，说明该网站的所有部分都允许被访问。

参考： 掘金的 robots 文件：https://juejin.cn/robots.txt

robots 文件使用方法：
使用方法非常简单，只需要将 robots.txt 文件上传到网站根目录就行了，注意文件名一定要全小写。当成功上传后，通常在浏览器中访问域名/robots.txt 就可以查看到文件。

当前设置：
书写 robots.txt 文件，该文件暂时保存在我本地。如需提交或放在项目根目录下，上服务器前要说明

### 内链｜外链
在搜索引擎优化领域，有着内链为王、外链为皇的说法，它们都能对提升网站排名有所帮助，尤其是外链的建设。 先来区分下网站内链和外链：
内链：从自己网站的一个页面指向另外一个页面。通过内链让网站内部形成网状结构，让蜘蛛的广度和深度达到最大化。
外链：在别的网站导入自己网站的链接。通过外链提升网站权重，提高网站流量。外链有以下几个好处：
- 提升网站权重
- 能够吸引蜘蛛来抓取网站
- 提升关键词排名
- 提升网址或品牌的曝光度
- 给网站带来流量
外链能够为我们的网站带来流量，所以外链数量越多越好是必然的。但是，一定要注意外链的质量，例如对方网站没有被搜索引擎收录，对方网站性能过差，死链等，这些低质量的外链反而会影响到本站的排名。
另外，在添加内链外链的过程中，要注意在 a 标签中对 nofollow 和·external 属性的使用。

当前设置：
<!-- 引入外部链接，起引流效果，spider无需跟踪 -->
    <a rel="nofollow" href="http://www.baidu.com/">百度</a>
    <a rel="nofollow" href="https://www.google.com/">谷歌</a>
    <a rel="nofollow" href="https://cn.bing.com/">必应</a>
  
带有 rel=nofollow 属性的链接会告诉搜索引擎忽略这个链接。阻止搜索引擎对该页面进行追踪。从而避免权重分散。这个属性只对搜索引擎有效，这是一个纯粹的 SEO 优化标签。


## Canonical URL（网址规范化）
<!-- 指定规范链接 -->
    <link rel="canonical" href="https://okjob.linchance.com">

网页规范化的两个好处：
- 解决网站由于网站 url 链接不一样，但网页内容是一样而造成搜索引擎重复收录的问题；
- 有利于 URL 权重集中。
解决方法：
在页面的 head 标签中，加入以下 canonical 标签，指定规范化网址。
使用 HTTPS
谷歌曾发公告表示，使用安全加密协议（HTTPS），是搜索引擎排名的一项参考因素。
所以，在域名相同情况下，HTTPS 站点比 HTTP 站点，能获得更好的排名。

## SSR 服务端渲染（ Server-Side Rendering）
当下 SPA 应用盛行，虽然它有用户体验好，服务器压力小等优点，但是同时也暴露出很多问题。例如首屏加载较慢，不利于 SEO 等（因为这些 spa 应用内容是由 js 动态更新的，蜘蛛无法爬取网页内容）。
而 ssr 的出现，很好的解决了 SEO 的问题。因为服务端渲染是指指客户端向服务器发出请求，然后运行时动态生成 html 内容并返回给客户端。所以客户端可以获取到完整的页面内容。
目前流行的 Vue/React 前端框架，都有 SSR 的解决方案：
Vue 的 nuxt.js
React 的 next.js
对于 Vue/React 来说，对于它们的 SSR/SSG 框架出现的原因就是主要就是 SEO 和首屏加载速度。

当前设置：
项目一开始并没有用 Nuxt.js 框架，所以改造 SSR 是一项十分重大艰巨的工程，暂时不考虑

### 预渲染 prerender-spa-plugin
如果只想改善部分页面的 SEO，可以不采用 SSR 的解决方案，毕竟无论是 next.js，还是 nuxt.js，都是有一定学习成本的。那么可以使用 prerender-spa-plugin 等插件来实现预渲染页面，在构建时就针对特定的路有生成静态的 html 文件。

当前设置：
准备尝试，因看到较近日期的言论提到一些插件包含上面提到的插件已不再维护，需要再考察看看哪些更新的方法可以使用。