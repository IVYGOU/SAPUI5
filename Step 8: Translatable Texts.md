* webapp/i18n/i18n.properties (New)  

属性文件：包含每个元素的name-value(键值对)。

```
showHelloButtonText=Say Hello
helloMsg=Hello {0}  //对应参数被访问顺序（此处从0开始访问）具体可参考https://wiki.wdf.sap.corp/wiki/display/cecnterui/The+Conduct+of+resourceBundle.getText%28%29+to+get+key%3Avalue+in+i18n.properties
```

* controller/App.controller.js
```javascript
sap.ui.define([
   "sap/ui/core/mvc/Controller",
   "sap/m/MessageToast",
   "sap/ui/model/json/JSONModel",
   "sap/ui/model/resource/ResourceModel"
], function (Controller, MessageToast, JSONModel, ResourceModel) {
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
     // set i18n model on view
         var i18nModel = new ResourceModel({//Q:ResourceModel是什么？
            bundleName: "sap.ui.demo.wt.i18n.i18n"
         });
         this.getView().setModel(i18nModel, "i18n");
      },
      onShowHello : function () {
         // read msg from i18n model
         var oBundle = this.getView().getModel("i18n").getResourceBundle();//Q:getResourceBundle()的含义？jQuery.sap.util.ResourceBundle
         var sRecipient = this.getView().getModel().getProperty("/recipient/name");//Q:为什么此处省略getModel参数？省略的含义是？
         var sMsg = oBundle.getText("helloMsg", [sRecipient]);
         // show message
         MessageToast.show(sMsg);
      }
   });
});
```

```javascript
getView():   
Returns the view associated with this controller or undefined.

setModel(oModel, sName?): Sets or unsets a model for the given model name for this ManagedObject.

getModel(sName?):Get the model to be used for data bindings with the given model name.


<mvc:View
	controllerName="sap.ui.demo.wt.controller.App"
	xmlns="sap.m"
	xmlns:mvc="sap.ui.core.mvc">
	<Button
		text="{i18n>showHelloButtonText}"//Q:>符号的含义是什么？
		press="onShowHello"/>
	<Input
		value="{/recipient/name}"
		description="Hello {/recipient/name}"
		valueLiveUpdate="true"
		width="60%"/>
</mvc:View>
```
