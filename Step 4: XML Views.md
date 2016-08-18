* App.view.xml
```xml
<mvc:View
   xmlns="sap.m"//xml命名空间属性
   xmlns:mvc="sap.ui.core.mvc">//定义一个额外的sap.ui.core命名空间，别名为mvc
   <Text text="Hello World"/>
</mvc:View>
```


* index.html
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
		data-sap-ui-preload="async"
		data-sap-ui-resourceroots='{ //告诉SAPUI5 core在sap.ui.demo.wt命名空间中的资源与index.html在相同文件夹下
			"sap.ui.demo.wt": "./"
		}'>
	</script>
	<script>
		sap.ui.getCore().attachInit(function () {
			sap.ui.xmlview({
				viewName: "sap.ui.demo.wt.view.App"
			}).placeAt("content");
		});
	</script>
</head>
<body class="sapUiBody" id="content">
</body>
</html>
```
