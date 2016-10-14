# SAPUI5 Controls lifecycle

* init      
Your little Control is born! Function is called by the framework during constructor execution. Do your initialization stuff here.

* onBeforeRendering   
Called by the framework before the rendering of the control is started. Triggers before every (re)rendering.

* onAfterRendering   
Called by the framework after the rendering of the control has completed. Triggers after every (re)rendering.

* exit    
RIP little Control! Cleans up the element instance before destruction. Called by the framework. Do your clean up here.   
Btw: If you need to explicitly destruct a Control/Element you should call destroy and not directly exit. 

Called when the View is destroyed. Use this one to free resources and finalize activities


```javasccript
sap.ui.core.Control.extend("a.sample.Control", {
  init : function() {
    // instantiate a sub-control
    this._btn = new sap.m.Button(); 
  },

  onBeforeRendering : function() {
    // deregister a listener via jQuery
    this.$("subelement").off("click", this.subElementClick);
  },

  onAfterRendering : function() {
    // register a listener via jQuery on a sub-element
    this.$("subelement").on("click", this.subElementClick);
  },

  subElementClick : function() {
    // do stuff
  },

  exit : function() {
    // clean up sub-controls and local references
    this._btn.destroy();
    delete this._btn;
  }

});
```
Tips: 
Init and exit are called once but onBeforeRendering and onAfterRendering are called every time.


Reference from: http://stackoverflow.com/questions/28703736/how-the-lifecycle-of-ui5-control-works
