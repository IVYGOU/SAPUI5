Reference: https://sapui5.netweaver.ondemand.com/#docs/guide/91f233476f4d1014b6dd926db0e91070.html

每一个view只可以对应一个没有名字的model，这个model为它的默认model，例如：
```javascript
this.getView().byId("AccountRecentItemsList").setModel(new sap.ui.model.json.JSONModel());	
```


