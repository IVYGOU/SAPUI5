* webapp/Component.js

```javascript
sap.ui.define([
	"sap/ui/core/UIComponent",
	"sap/ui/model/json/JSONModel",
	"sap/ui/demo/wt/controller/HelloDialog"
], function (UIComponent, JSONModel, HelloDialog) {
	"use strict";

	return UIComponent.extend("sap.ui.demo.wt.Component", {

		metadata : {
			manifest: "json"
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
			this.setModel(oModel);

			// set dialog
			this.helloDialog = new HelloDialog();//dialog实例化
		}
	});

});
```

* webapp/controller/HelloDialog.js (New)

```javascript
sap.ui.define([
	"sap/ui/base/Object"
], function (Object) {
	"use strict";
	return Object.extend("sap.ui.demo.wt.controller.HelloDialog", {
		_getDialog : function () {
			// create dialog lazily
			if (!this._oDialog) {
				// create dialog via fragment factory
				this._oDialog = sap.ui.xmlfragment("sap.ui.demo.wt.view.HelloDialog", this);
			}
			return this._oDialog;
		},
		open : function (oView) {//第一次调用open时实例化dialog
			var oDialog = this._getDialog();
			// connect dialog to view (models, lifecycle)
			oView.addDependent(oDialog);
			// open dialog
			oDialog.open();
		},
		onCloseDialog : function () {
			this._getDialog().close();
		}
	});
});
```
* webapp/controller/HelloPanel.controller.js

```javascript
sap.ui.define([
	"sap/ui/core/mvc/Controller",
	"sap/m/MessageToast"
], function (Controller, MessageToast) {
	"use strict";
	return Controller.extend("sap.ui.demo.wt.controller.HelloPanel", {
		onShowHello : function () {
			// read msg from i18n model
			var oBundle = this.getView().getModel("i18n").getResourceBundle();
			var sRecipient = this.getView().getModel().getProperty("/recipient/name");
			var sMsg = oBundle.getText("helloMsg", [sRecipient]);
			// show message
			MessageToast.show(sMsg);
		},
		onOpenDialog : function () {
			this.getOwnerComponent().helloDialog.open(this.getView());
		}
	});
});
```

getOwnerComponent(): sap.ui.core.Component   

Gets the component of the controller's view
