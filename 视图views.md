# 视图views
## 视图本质就是一个函数
	视图参数：1. 一个HtpRequest的实例
						  2. 通过正则表达式获取来的参数
	位置：通常在应用下的views.py中定义
	错误视图：1. 404视图（页面没找到）
						   2. 400视图（客户操作错误）
						   3. 500视图（服务器内部错误）
	自定义错误视图
			在工程的templates文件夹中创建参应的错误文件
			获取请求路径{{request_path}}
			在文件中定义自己的错误样式
			需要在关闭Debug的情况下才可
			不关闭debug会在界面中直接显示log
			
			例如：在templates/新建 404.html
			
```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>404</title>
</head>
<body>
    <h3>Client Request is Not Found!</h3>
</body>
</html>
```

页面上的变化并不能启动服务器，要手动启动。
系统本身有404这样的错误提示代码，但系统会遵循就近的原则，优先找到刚才的代码。

## 双R：Request, Response
### HttpRequest
	服务器在接收到Http请求后，会根据报文创建HttpRequest对象，视图中的第一个参数就是HttpRequest对象。
	Django框架会进行自己的包装，之后传递给视图。
	属性：path			请求的完整路径
				method 		请求的方法，常用GET, POST
				encoding	编码方式，常用urt-8
				GET		类似字典的参数，包含了get的所有参数
				POST	类似字典的参数，包含了post的所有参数
				FILES	类似字典的参数，包含了上传的文件
				COOKIES  字典，包含了所有COOKIE
				session		类似字典，表示会话。
	方法：is_ajax() 判断是否是ajax()，多用在移动端和JS中。
	
	Two/urls.py中添加：		
` url(r'^haverequest/ ' , views.have_request), `
	
	Two/views.py中添加：
	
```
	def have_request(request):
			print(request.path)
			print(request.methon)
			print(request.GET)
			print(request.POST)
			return HttpResponse('Request success')
```



	
			
