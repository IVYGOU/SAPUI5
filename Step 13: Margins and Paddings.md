* webapp/view/App.view.xml

```xml
<mvc:View
	controllerName="sap.ui.demo.wt.controller.App"
	xmlns="sap.m"
	xmlns:mvc="sap.ui.core.mvc"
	displayBlock="true">
	<App>
		<pages>
			<Page title="{i18n>homePageTitle}">
				<content>
					<Panel
						headerText="{i18n>helloPanelTitle}"
						class="sapUiResponsiveMargin"//css类：在panel周围增加一些空间
						width="auto">//auto:跟随屏幕大小变化大小
						<content>
							<Button
								text="{i18n>showHelloButtonText}"
								press="onShowHello"
								class="sapUiSmallMarginEnd"/>//添加此类可增减input field和button之间的空间
							<Input
								value="{/recipient/name}"
								valueLiveUpdate="true"
								width="60%"/>
							<Text
								text="Hello {/recipient/name}"
								class="sapUiSmallMargin"/>
						</content>
					</Panel>
				</content>
			</Page>
		</pages>
	</App>
</mvc:View>
```
