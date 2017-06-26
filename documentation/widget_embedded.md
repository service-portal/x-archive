
# Embedded Widgets
In Service Portal, widgets can be embedded inside other widgets. This technique is useful for creating more powerful widgets through the composition of other widgets.

For a direct example of this, see the Social QA Question widget, which embeds a login widget next to the Answer Question section for an easy way to prompt users to login to answer questions.

---

## Widget Directive Syntax
You can embed any widget inside of your widget’s [HTML template](widget_html.md) using the custom `<widget><widget>` element.
The basic usage looks like this:

###### HTML Template
```html
<div>
  <widget id="widget-cool-clock"></widget>
</div>
```
_The `id` parameter is simply the id of the widget you're trying to embed._

## Widget Options

Widgets might have [options](widget_options.md) that you can setup. You can define their values in JSON format:


### Providing options in the HTML template

###### HTML Template
```html
<widget id="widget-cool-clock" options='{"zone": "America/Los_Angeles","title": "San Diego, CA"}'><widget>
```

![Clock Options](/assets/widget_embedded/clock-options.png)

You don't necessarily need to provide options in the HTML template.

### Providing options server-side

###### HTML template
```html
<widget id="widget-cool-clock" options='data.clockOptions'><widget>
```
###### Server Script
```javascript
(function() {
  data.clockOptions = {"zone": "America/Los_Angeles","title": "San Diego, CA"};
})();
```

### Embedded Widgets client-side

###### HTML Template
```html
<sp-widget widget="c.myClockWidget"></sp-widget>
```

###### Client Script
```javascript
function(spUtil) {
	var c = this;
	spUtil.get("widget-cool-clock").then(function(response) {
			c.myClockWidget = response;
	});
}
```

------


## Example: How to embed a widget multiple times with custom options

Each instance of the clock is provided a different timezone and title.

> To see what options are configurable in the cool clock widget, open it in the widget editor. It uses the options object for the title, second hand color, and the timezone. This screenshot shows you where they're hiding.

> ![Cool clock client script](/assets/widget_embedded/example_clock_options_1.png)

Edit the "Embedded clock" widget and replace with the following code blocks:

###### HTML Template
```html
<div class="panel panel-default">
  <div class="panel-heading">Time across the US</div>
  <div class="panel-body">
    <div class="row">
      <div class="col-sm-3" ng-repeat="myClock in c.data.clocks">
        <sp-widget widget="myClock"></sp-widget>
      </div>
    </div>
  </div>
</div>
```

###### CSS
```css
.panel {
	margin-top: 10px;
}
```

###### Client Script
```javascript
function() {
	// nothing to do here...
}
```

###### Server Script
```javascript
(function() {
	var options = [
		{zone: "America/Los_Angeles", title: "San Diego"},
		{zone: "America/Denver", title: "Denver"},
		{zone: "America/Chicago", title: "Chicago"},
		{zone: "America/New_York", title: "New York"}
	];

	data.clocks = [];
	for (var i in options) {
		data.clocks.push($sp.getWidget("widget-cool-clock", options[i]));
	}
})();
```
### Result  
Each instance of the clock widget has a different timezone and title.

![Embedded clock](/assets/widget_embedded/example_clock_options_2.png)

---

## API Reference

### Client Side
##### spUtil.get() - Get a widget model via client script

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


### Server Side
##### $sp.getWidget() - Get a widget model via server script

```javascript
data.catalogItemWidget = $sp.getWidget("widget-sc-cat-item", {sys_id: "your_catalog_item_sys_id"});
```
**Parameters**  

- (*string*) widget\_id  
   Can be a widget_id or widget sys_id.  
- (*object*) options  
   An object to pass to the widget's server script. Refer to this object as **options** in your server script.

**Note:** As of all versions of Helsinki, any options passed into this function will only be available in the embedded widget's server script on the **first execution** of that script. Any subsequent calls into the server script from the embedded widget will not contain the object properties passed in. This is something we are investigating for a future version of Helisinki or Istanbul.

## Widget Model in depth

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
