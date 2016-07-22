
```html
<!DOCTYPE html>
<html>
<head>
	<meta http-equiv="X-UA-Compatible" content="IE=edge">
	<meta charset="utf-8">
	<title>SAPUI5 Walkthrough</title>
	<script
		id="sap-ui-bootstrap"
		src="https://sapui5.netweaver.ondemand.com/resources/sap-ui-core.js"
		data-sap-ui-theme="sap_bluecrystal"
		data-sap-ui-libs="sap.m"
		data-sap-ui-compatVersion="edge"
		data-sap-ui-preload="async">
	</script>
	<script>
		sap.ui.getCore().attachInit(function () {
			alert("UI5 is ready");
		});
	</script>
</head>
<body>
<div>Hello World</div>
</body>
</html>
```
黄色部分为初始化sapui5的核心模块设置:   

1.src属性，表示sapui5的核心库位置   

2.SAPUI5 controls default theme为 sap_bluecrystal   

3.指定包含ui库sap.m    

4.定义兼容版本"edge"   

5."bootstrapping"进程异步运行    


当加载完所有的resources and librariess时`init()`事件触发。
通过调用`sap.ui.getCore().attachInit(function ())`实现，参数为`function(){alert("UI5 is ready");}`

NOTE:JavaScript中function()也是一种对象，可用作参数和赋值，例如:
` var callback = function(){alert("UI5 is ready");}`

`<script>`标签标签用于定义客户端脚本。
既可以包含脚本语句，也可以通过 src 属性指向外部脚本文件URL。
