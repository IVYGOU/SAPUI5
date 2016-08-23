* webapp/css/style.css (New)

```css
.myAppDemoWT .myCustomButton.sapMBtn {//定义3个类，属于这3个类都需要满足该条件
  margin-right: 0.125rem
}

html[dir="rtl"] .myAppDemoWT .myCustomButton.sapMBtn {//html[dir="rtl"]含义：Right to Left
  margin-left: 0.125rem;
  margin-right: 0 
}
.myAppDemoWT .myCustomText {
  font-weight: bold;
}
```

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
               <Panel
                  headerText="{i18n>helloPanelTitle}"
                  class="sapUiResponsiveMargin"
                  width="auto">
                  <content>
                     <Button
                        text="{i18n>showHelloButtonText}"
                        press="onShowHello"
                        class="myCustomButton"/>
                     <Input
                        value="{/recipient/name}"
                        valueLiveUpdate="true"
                        width="60%"/>
				 <Text
                        text="Hello {/recipient/name}"
                        class ="sapUiSmallMargin sapThemeHighlight-asColor myCustomText"/>//highlight为blue，根据主题而定（不要在css中自定义颜色）
                  </content>
               </Panel>
            </content>
         </Page>
      </pages>
   </App>
</mvc:View>
```
