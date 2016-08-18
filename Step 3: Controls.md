
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
			new sap.m.Text({//实例一个SAPUI5 text control
				text: "Hello World"
			}).placeAt("content");//将Text对象放入ID为"content"的对象中
		});
	</script>
</head>
<body class="sapUiBody" id="content">
</body>
</html>
```

*  `placeAt`  	SAPUI5封装的方法
