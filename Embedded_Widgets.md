# Service Portal Documentation
## Embedded Widgets

### <sp-widget />
You can embed any widget inside of your widget’s HTML template using the spWidget directive. This directive requires a complete widget model which you can get using spUtil.get() on the client or $sp.getWidget on the server. [See below for details](#get_1).

Use it like this:

```html
<sp-widget widget="c.myCatItemWidget"></sp-widget>
```

#### Widget Model in depth
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

#### There are 2 ways to get a widget model for use with \<sp-widget />

<a name="get_one" />##### Getting a widget model from client script

```javascript
spUtil.get("widget-sc-cat-item", {sys_id: "your_catalog_item_sys_id"}).then(function(response) {
	c.catalogItemWidget = response;
});
```
**Parameters**
- (_string_) widget\_id  
   Can be a widget_id or widget sys_id.
- (_object_) data  
   An object to post to the widget's server script. Refer to this object as **input** in your server script.

**Callback**  
The callback function is called when the widget model is ready. The response object contains the full widget model.

<br id="get_1" />
##### Getting a widget model from server script

```javascript
data.catalogItemWidget = $sp.getWidget("widget-sc-cat-item", {sys_id: "your_catalog_item_sys_id"});
```
**Parameters**
- (_string_) widget\_id  
   Can be a widget_id or widget sys_id.
- (_object_) options  
   An object to pass to the widget's server script. Refer to this object as **options** in your server script.

