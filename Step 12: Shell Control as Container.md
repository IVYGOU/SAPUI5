* webapp/index.html

```html
<!DOCTYPE html>
<html>
   <head>
      …
      <script>
         sap.ui.getCore().attachInit(function () {
            new sap.m.Shell({
               app : new sap.ui.core.ComponentContainer({
                  name : "sap.ui.demo.wt",
                  height : "100%"
               })
            }).placeAt("content");
         });
      </script>
   </head>
   <body class="sapUiBody" id="content">
   </body>
</html>
```
