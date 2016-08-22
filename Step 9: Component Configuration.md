* webapp/Component.js 

```javascript
sap.ui.define([
	"sap/ui/core/UIComponent",
	"sap/ui/model/json/JSONModel",
	"sap/ui/model/resource/ResourceModel"
], function (UIComponent, JSONModel, ResourceModel) {
	"use strict";

	return UIComponent.extend("sap.ui.demo.wt.Component", {

		metadata : {//metadata部分指定rootView，不直接在index.html中显示the root view
			rootView: "sap.ui.demo.wt.view.App"
		},

		init : function () {
			// call the init function of the parent
			UIComponent.prototype.init.apply(this, arguments);

			// set data model
			var oData = {
				recipient : {
					name : "World"
				}
			};
			var oModel = new JSONModel(oData);
			this.setModel(oModel);//  Q:区别于前一节的this.getView().setModel(i18nModel, "i18n");为什么？

			// set i18n model
			var i18nModel = new ResourceModel({
				bundleName : "sap.ui.demo.wt.i18n.i18n"
			});
			this.setModel(i18nModel, "i18n");
		}
	});

});
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
         // read msg from i18n model
         var oBundle = this.getView().getModel("i18n").getResourceBundle();
         var sRecipient = this.getView().getModel().getProperty("/recipient/name");
         var sMsg = oBundle.getText("helloMsg", [sRecipient]);
         // show message
         MessageToast.show(sMsg);
      }
   });
});
```

* webapp/index.html
```javascript
<!DOCTYPE html>
<html>
   <head>
      <meta http-equiv="X-UA-Compatible" content="IE=edge">
      <meta charset="utf-8">
      <title>Walkthrough</title>
      <script
         id="sap-ui-bootstrap"
         src="/resources/sap-ui-core.js"
         data-sap-ui-theme="sap_bluecrystal"
         data-sap-ui-libs="sap.m"
         data-sap-ui-bindingSyntax="complex"
         data-sap-ui-compatVersion="edge"
         data-sap-ui-preload="async"
         data-sap-ui-resourceroots='{
            "sap.ui.demo.wt": "./"
         }' >
      </script>
      <script>
         sap.ui.getCore().attachInit(function () {
            new sap.ui.core.ComponentContainer({
               name : "sap.ui.demo.wt"
            }).placeAt("content");

         });
      </script>
   </head>
   <body class="sapUiBody" id="content">
   </body>
</html>
```
