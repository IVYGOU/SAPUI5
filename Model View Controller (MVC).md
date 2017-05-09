Reference: https://sapui5.netweaver.ondemand.com/#docs/guide/91f233476f4d1014b6dd926db0e91070.html

* 每一个view只可以对应一个没有名字的model，这个model为它的默认model，例如：
```javascript
this.getView().byId("AccountRecentItemsList").setModel(new sap.ui.model.json.JSONModel());	
```
* 其他有名字model的创建如下例：
```javascript
this.getView().byId("AccountRecentItemsList").setModel(new sap.ui.model.json.JSONModel(), "testModel");	
```
* model创建时的可赋初始值如下：
```javascript
this.getView().byId("AccountRecentItemsList").setModel(new sap.ui.model.json.JSONModel({"key1":"vaule1"}));
```
* 向model中放入新值有两种方法：
1.`setData()` 会完全覆盖这个model里所有的oData(即所有的properties)
```javascript
this.getView().byId("AccountRecentItemsList").getModel().setData({"visible": false});
```
2.`setProperty()`只会更改当前这个Property的属性，没有则增加一个Property。
```javascript
this.getView().byId("AccountRecentItemsList").getModel().setProperty("/visible", false);
```
