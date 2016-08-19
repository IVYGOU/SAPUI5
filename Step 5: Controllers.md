* webapp/view/App.view.xml

```xml
<mvc:View
   controllerName="sap.ui.demo.wt.controller.App"//1，设置controllerName的作用？
   xmlns="sap.m"
   xmlns:mvc="sap.ui.core.mvc">
   <Button
      text="Say Hello"
      press="onShowHello"/>//按键触发onShowHello事件
</mvc:View>
```

* webapp/controller/App.controller.js (New)
* 
```javascript
sap.ui.define([
   "sap/ui/core/mvc/Controller"
], function (Controller) {
   "use strict";
   return Controller.extend("sap.ui.demo.wt.controller.App", {
      onShowHello : function () {
         // show a native JavaScript alert
         alert("Hello World");
      }
   });
});
```

sap.ui.define(sModuleName?, aDependencies?, vFactory, bExport?)
