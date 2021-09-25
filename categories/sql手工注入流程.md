---
title: SQL手工注入流程
---

## Quick Start

```
sql注入点根据不同维度可分为：
	1.根据请求方式分类：
		GET方式请求注入
			常见产生位置：url
		POST方式请求注入
			常见产生位置：POST包的请求实体
	2.根据注入点参数分类：
		整数型注入
			例：
				select uname,password form users where uid=$id
		字符型注入
			例：
				select uname,password form users where uid='$id'
		搜索型注入
			例：
				select uname,password form users where uname='%$uname%'
	3.根据sql注入点反馈类型分配（重点）
		union类型
		基于错误显示
		布尔类型
		基于时间
		其他类型
	4.根据web应用的数据库类型分类（数据库样式扩充）
		mysql	sqlserver	oracle	access
```

```
sql万能密码
	常见万能密码：
		ASP/ASPX：			
		1.'.).or.('.a.'='.a
		2.or 1=1-- 
		3.'or 1=1-- 
		4.......

		PHP: 
		1.admin’/* 
		2.'or 1=1/* 
		3."or "a"="a 
		4.......-
```

```
手工注入流程：
	1.判断是否有注入漏洞，识别注入点类型
	2.获取数据库中的信息
		(1)获取数据库基本信息(数据库版本、数据库类型、查寻列数等) 
		(2)获取数据库名
		(3)获取表名
		(4)获取列名
		(5)获取用户数据
	3.破解加密数据（数据解密）
	4、提升权限(利用数据库提权上升到系统权限提升) 
	5、内网渗透
```

