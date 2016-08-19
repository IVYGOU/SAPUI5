## JSON
Javascript Object Notation，Javascript对象表示法，它是一种结构化数据格式。

1，与javascript对象字面量相比的不同之处   

没有声明变量（JSON中没有变量的概念）；  

没有末尾的分号。

注意：对象的属性必须加双引号。

* App.view.xml

```xml
<mvc:View
	controllerName="sap.ui.demo.wt.controller.App"
	xmlns="sap.m"
	xmlns:mvc="sap.ui.core.mvc">
	<Button
		text="Say Hello"
		press="onShowHello" />
	<Input
		value="{/recipient/name}"
		description="Hello {/recipient/name}"
		valueLiveUpdate="true"
		width="60%" />
</mvc:View>
```

* App.controller.js

```javascript
sap.ui.define([
   "sap/ui/core/mvc/Controller",
   "sap/m/MessageToast",
   "sap/ui/model/json/JSONModel"
], function (Controller, MessageToast, JSONModel) {
   "use strict";
   return Controller.extend("sap.ui.demo.wt.controller.App", {
      onInit : function () {
         // set data model on view
         var oData = {
            recipient : {
               name : "World"
            }
         };
         var oModel = new JSONModel(oData);
         this.getView().setModel(oModel);
      },
      onShowHello : function () {
         MessageToast.show("Hello World");
      }
   });
});
```
