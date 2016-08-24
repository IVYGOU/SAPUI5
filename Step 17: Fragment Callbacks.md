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
         // create dialog lazily
         if (!this._oDialog) {
            // create dialog via fragment factory
            this._oDialog = sap.ui.xmlfragment("sap.ui.demo.wt.view.HelloDialog", this);
            // connect dialog to view (models, lifecycle)
            this.getView().addDependent(this._oDialog);
         }
         return this._oDialog;
      },
      onOpenDialog : function () {
         this._getDialog().open();//open():Open the dialog.(class:sap.m.Dialog)
      },
      onCloseDialog : function () {
         this._getDialog().close();//close()Close the dialog.(class:sap.m.Dialog)
      }
   });
});
```
* webapp/view/HelloDialog.fragment.xml

```xml
<core:FragmentDefinition
   xmlns="sap.m"
   xmlns:core="sap.ui.core" >
   <Dialog
      title ="Hello {/recipient/name}">
      <beginButton>
         <Button
            text="{i18n>dialogCloseButtonText}"
            press="onCloseDialog"/>
      </beginButton>
   </Dialog>
</core:FragmentDefinition>
```
