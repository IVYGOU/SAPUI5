* webapp/manifest.json (New)

包含all global application settings and parameters

```json
{
  "_version": "1.1.0",
  "sap.app": {
	"_version": "1.1.0",
	"id": "sap.ui.demo.wt",
	"type": "application",
	"i18n": "i18n/i18n.properties",
	"title": "{{appTitle}}",
	"description": "{{appDescription}}",
	"applicationVersion": {
	  "version": "1.0.0"
	}
  },
  "sap.ui": {
	"_version": "1.1.0",
	"technology": "UI5",
	"deviceTypes": {
	  "desktop": true,
	  "tablet": true,
	  "phone": true
	},
	"supportedThemes": [
	  "sap_bluecrystal"
	]
  },
  "sap.ui5": {
	"_version": "1.1.0",
	"rootView": "sap.ui.demo.wt.view.App",
	"dependencies": {
	  "minUI5Version": "1.30",
	  "libs": {
		"sap.m": {}
	  }
	},
	"models": {
	  "i18n": {
		"type": "sap.ui.model.resource.ResourceModel",
		"settings": {
		  "bundleName": "sap.ui.demo.wt.i18n.i18n"
		}
	  }
	}
  }
}
```