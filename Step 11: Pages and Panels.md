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
						headerText="{i18n>helloPanelTitle}">
						<content>
							<Button
								text="{i18n>showHelloButtonText}"
								press="onShowHello" />
							<Input
								value="{/recipient/name}"
								description="Hello {/recipient/name}"
								valueLiveUpdate="true"
								width="60%" />
						</content>
					</Panel>
				</content>
			</Page>
		</pages>
	</App>
</mvc:View>
```

* webapp/i18n/i18n.properties

```properties
# App Descriptor
appTitle=Hello World
appDescription=A simple walkthrough app that explains the most important concepts of SAPUI5

# Hello Panel
showHelloButtonText=Say Hello
helloMsg=Hello {0}
homePageTitle=Walkthrough
helloPanelTitle=Hello World
```
