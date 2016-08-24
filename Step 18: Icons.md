webapp/view/HelloPanel.view.xml

```xml
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
            icon="sap-icon://world"             //增加一个icon显示在button上
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
```

webapp/view/HelloDialog.fragment.xml

```xml
<core:FragmentDefinition
   xmlns="sap.m"
   xmlns:core="sap.ui.core" >
   <Dialog
      title ="Hello {/recipient/name}">
      <content>
         <core:Icon        //增加一个icon control，并设置size和margin
            src="sap-icon://hello-world"
            size="8rem"
            class="sapUiMediumMargin"/>
      </content>
      <beginButton>
         <Button
            text="{i18n>dialogCloseButtonText}"
            press="onCloseDialog"/>
      </beginButton>
   </Dialog>
</core:FragmentDefinition>
```
