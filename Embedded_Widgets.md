# Service Portal Documentation
## Embedded Widgets

### <sp-widget />
The spWidget directive takes a widget model, creates a directive for it, and renders it where you put it in your HTML Template. 

Use it like this:

```html
<sp-widget widget="c.myCatItemWidget"></sp-widget>
```

### Widget Model
The widget model contains all of the client-side parts of a widget needed to create an angular directive. The HTML template, client script, and link function are loaded just as they are in the sp_widget record. The data property is the result of the widget's server script execution. Anything that you put on the data object on the server is available in the data object on the client.

Here is a detailed look at some of the fields in the widget model: 

| Property name | Type | Description |
| ------------- | ---- | ----------- |
| client_script | string | The widget's client script field |
| css | string | The compiled css output from the widget's sass field |
| data | object | The data object containing all of the keys and values added to it in the widget's server script |
| dependencies | array | A collection of javascript libraries to load before the widget executes |
| options | object | The options used to initialize the widget |
| template | string | The widget's HTML Template field |


There are 2 ways to get a widget model for use with <sp-widget />

#### Getting a widget model from client script

```
spUtil.get("widget-sc-cat-item", {sys_id: "your catalog item sys_id"}).then(function(response) {
	c.catalogItemWidget = response;
});
```

spUtil.get( **string**, object )

> Can be a **Widget Id** or **Widget sys_id**

spUtil.get( string, **object** )

> An object to post to the widget's server script. _refer to this object as **input** in your server script_ **

#### Getting a widget model from server script

```
data.catalogItemWidget = $sp.getWidget("widget-sc-cat-item", {sys_id: "your catalog item sys_id"});
```