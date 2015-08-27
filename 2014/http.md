HTTP权威指南
********
###第一部分：HTTP：Web 的基础
####第一章：HTTP概述

1. MIME	
	>因特网上有数千种不同的数据类型，HTTP 仔细地给每种要通过 Web 传输的对象都打上了名为 MIME 类型（MIME type）的数据格式标签。
		
	>MIME （Multipurpose Internet Mail Extension，多用途因特网邮件扩展） 类型

	>当 Web 浏览器从服务器中取回一个对象时，会去查看相关的 MIME 类型，看看它是否知道应该如何处理这个对象。
	
	>常见的 MIME 类型有数百个，实验性或用途有限的 MIME 类型则更多。
	
	- HTML 格式的文本文档由 text/html 类型来标记。
	- 普通的 ASCII 文本文档由 text/plain 类型来标记。
	- JPEG 格式的图片为 image/jpeg 类型。
	- GIF 格式的图片为 image/gif 类型。

2. URI	

    >服务器资源名被称为统一资源标识符（Uniform Resource Identifier，URI）
	
3. URL	
	>统一资源定位符（Uniform Resource Locator，缩写为URL）是资源标识符(URI)最常见的形式。
	>现在，几乎所有的 URI 都是 URL。
	
	大部分 URL 都遵循一种标准格式，这种格式包含三个部分。
	- URL 的第一部分被称为方案（scheme），说明了访问资源所使用的协议类型。这部分通常就是 HTTP 协议（http://）
	- 第二部分给出了服务器的因特网地址（比如，www.joes-hardware.com）。
	- 其余部分指定了 Web 服务器上的某个资源（比如，/specials/saw-blade.gif）。
4. URN
    >URI 的第二种形式就是统一资源名（URN）.URN 仍然处于试验阶段，还未大范围使用。
	
5. 事务
		
	>一个事务由一条(从客户端发完服务器)的请求命令和一个(服务器端发往客户端)的响应结果组成。
	
	>每条 HTTP 请求报文都包含一个方法。这个方法会告诉服务器要执行什么动作（获取一个 Web 页面、运行一个网关程序、删除一个文件等）
#####http支持几种请求方法	
	- GET	从服务器向客户端发送命名资源
	- POST	将来自客户端的数据存储到一个命名的服务器资源中去
	- DELETE 从服务器中删除命名资源
	- PUT	将客户端数据发送到一个服务器网关应用程序
	- HEAD  仅发送命名资源响应中的HTTP 首部
	>每条 HTTP 响应报文返回时都会携带一个状态码。
#####一些常见的HTTP状态码
	- 200	OK。文档正确返回
	- 302	Redirect（重定向）。到其他地方去获取资源
	- 404	Not Found（没找到）。无法找到这个资源
	
	>应用程序完成一项任务时通常会发布多个 HTTP 事务。 显示页面中的图片是一个事物，执行页面布局也是一个事物。

6. 报文
	
  #####HTTP 报文是由一行一行的简单字符串组成的。

  HTTP 报文包括以下三个部分:

	- 起始行(类似以下)	
		Request URL:http://www.baidu.com/
		Request Method:GET
		Status Code:200 OK
		
	- 首部字段
		Request Headers中的内容
	- 主体
		请求报文没有主体！
		只有在响应的报文中会返回主体(请求www.baidu.com 返回百度首页主体)
	
  #####这是一个请求报文的一部分 Request Headers：

	Accept:text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,*/*;q=0.8
	Accept-Encoding:gzip,deflate,sdch
	Accept-Language:zh-CN,zh;q=0.8,ja;q=0.6,zh-TW;q=0.4
	Cache-Control:max-age=0
	Connection:keep-alive

  #####这是一个响应报文的一部分 Response Headers：

	Cache-Control:no-cache
	Connection:Keep-Alive
	Content-Encoding:gzip
	Content-type:text/html;charset=utf-8
	
7. 连接

	>	
	
	

	
   