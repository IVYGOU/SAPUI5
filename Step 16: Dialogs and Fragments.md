Fragments： Fragments are light-weight UI parts (UI subtrees) which can be reused but do not have any controller. 

* webapp/view/HelloPanel.view.xml
<mvc:View
   controllerName="sap.ui.demo.wt.controller.HelloPanel"
   xmlns="sap.m"
   xmlns:mvc="sap.ui.core.mvc">
   <Panel
      headerText="{i18n>helloPanelTitle}"
      class="sapUiResponsiveMargin"
      width="auto" >
      <content>
      <Button
         text="{i18n>openDialogButtonText}"
         press="onOpenDialog"
         class="sapUiSmallMarginEnd"/>

      <Button
         text="{i18n>showHelloButtonText}"
         press="onShowHello"
         class="sapUiDemoWTmyCustomButton"/>
      <Input
         value="{/recipient/name}"
         valueLiveUpdate="true"
         width="60%"/>
      <Text
         text="Hello {/recipient/name}"
         class="sapUiSmallMargin sapThemeHighlight-asColor sapUiDemoWTmyCustomText"/>
      </content>
   </Panel>
</mvc:View>

* webapp/view/HelloDialog.fragment.xml (New)

没有指定特定的controller，它只是一系列重用控件的容器。

```xml
<core:FragmentDefinition
   xmlns="sap.m"
   xmlns:core="sap.ui.core" >
   <Dialog
      title="Hello {/recipient/name}">
   </Dialog>
</core:FragmentDefinition>
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
         …
      },
      _getDialog : function () {
         if (!this._oDialog) {
            this._oDialog = sap.ui.xmlfragment("sap.ui.demo.wt.view.HelloDialog");//实例化一个fragment
            this.getView().addDependent(this._oDialog);//getview()的viewname为“sap.ui.demo.wt.view.HelloPanel”,view作为element的subclass，可以继承它的addDependent方法
         }
         return this._oDialog;
      },
      onOpenDialog : function () {
         this._getDialog().open();
      }
   });
});
```

sap.ui.xmlfragment(sId?, vFragment, oController?)

addDependent(oDependent): sap.ui.core.Element  

Adds some dependent to the aggregation dependents.
