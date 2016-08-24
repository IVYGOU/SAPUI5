* webapp/view/App.view.xml

```xml
<mvc:View
	controllerName="sap.ui.demo.wt.controller.App"
	xmlns="sap.m"
	xmlns:mvc="sap.ui.core.mvc"
	displayBlock="true">
	<App class="myAppDemoWT">
		<pages>
			<Page title="{i18n>homePageTitle}">
				<content>
					<mvc:XMLView viewName="sap.ui.demo.wt.view.HelloPanel"/>//将content里的内容单独放在HelloPanel.view.xml中
				</content>
			</Page>
		</pages>
	</App>
</mvc:View>
```

* webapp/view/HelloPanel.view.xml

```xml
<mvc:View
   controllerName="sap.ui.demo.wt.controller.HelloPanel"//指定与该view绑定的controller
   xmlns="sap.m"
   xmlns:mvc="sap.ui.core.mvc">
   <Panel
      headerText="{i18n>helloPanelTitle}"
      class="sapUiResponsiveMargin"
      width="auto" >
      <content>
         <Button
            text="{i18n>showHelloButtonText}"
            press="onShowHello"
            class="myAppDemoWT myCustomButton"/>
         <Input
            value="{/recipient/name}"
            valueLiveUpdate="true"
            width="60%"/>
         <Text
            text="Hello {/recipient/name}"
            class="sapUiSmallMargin sapThemeHighlight-asColor myCustomText"/>
      </content>
   </Panel>
</mvc:View>
```

* webapp/controller/HelloPanel.controller.js (New) 

为了可重用，将onShowHello 方法放入HelloPanel.controller中  

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
		}
	});

});

```
