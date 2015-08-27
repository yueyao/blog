package.json 配置项
-----------------

以下示例列举了常用的地方，一些不常用的可以查看文档：[文档地址](https://npmjs.org/doc/misc/npm-config.html)

###写法示例：

	{
		//该模块名字
		"name":"test" ,
		//版本
		"version":"0.0.1",
		//主入口
		"main":"app.js",
		//脚本
		"script":{"start": "node server.js"},
		//依赖模块
		"dependencies":{

		},
		//描述  可以让人们在npm搜索到相关信息
		"description":"this is a description",
		//关键词  可以让人们在npm搜索到相关信息
		"keywords":"",
		//项目主页
		"homepage":"",
		//bug提交方式 邮件
		"bugs":{
				"url" : "http://github.com/owner/project/issues",
				"email" : "project@hostname.com"
		},
		//遵循的协议
		"license":"BSD",
		//作者
		"author": "zuozhe" ,
		//代码仓库地址
		"repository" :
		{ "type" : "git"
			, "url" : "http://github.com/isaacs/npm.git"
		},
		//指定node版本
		"engines":{"node" : ">=0.10.3 <0.12"}
	}
	
	
	