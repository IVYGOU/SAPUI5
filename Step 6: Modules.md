* webapp/view/App.view.xml

```xml
<mvc:View
   controllerName="sap.ui.demo.wt.controller.App"//1，设置controllerName的作用即可与App.controller.js进行连接。
   xmlns="sap.m"
   xmlns:mvc="sap.ui.core.mvc">
   <Button
      text="Say Hello"
      press="onShowHello"/>//按键触发onShowHello事件
</mvc:View>
```

* webapp/controller/App.controller.js 

```javascript
sap.ui.define([
   "sap/ui/core/mvc/Controller",
   "sap/m/MessageToast"
], function (Controller, MessageToast) {
   "use strict";
   return Controller.extend("sap.ui.demo.wt.controller.App", {
      onShowHello : function () {
         MessageToast.show("Hello World");
      }
   });
});
```

sap.ui.define(sModuleName?, aDependencies?, vFactory, bExport?)

sap.ui.require(vDependencies, fnCallback?)

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
		data-sap-ui-resourceroots='{
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

