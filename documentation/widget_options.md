# Widget Options
In Service Portal, users can configure widgets embedded on pages through the power of **Widget Instances** (for more on this topic, read [Widget Instances](widget_instances.md) and return here for more).

Now, let's go over how a Widget Developer could define an option schema within their own widgets to enable this level of configurability.

### Defining Option Schemas
An **option schema** is a way of defining what properties users of your widgets can define. Any properties declared here will be surfaced when a user is editing the instance of a widget. Here, you can enable users to declare many types of fields, from primitive String and Numbers to reference fields.

To do this, you will need to navigate to the Widget Editor and select the widget you wish to edit. In the top-right corner of the screen, select the hamburger icon and click the item called **Edit Option Schema**.

You should be presented with something that looks like this:

![Edit Option Schema](/assets/widget_options/widget_options_schema_modal.png)

This is where you can add and subtract widget options, along with types and hints. From here, press the + icon and give it a label, a name (snakecase, like_this), a type, and a hint. Depending on the type you select, you may be prompted to provide additional fields.

Once you have provided your option(s), you can click the **Save** button and begin using them.

To see your options in action, navigate to an instance of the widget on a page, hold CTRL and right-click the widget. Select the option titled **Instance Options**. In the modal popover, you will see your new option.

### Using Options in a Widget
Now, let's go over how to access options in a widget, as well as some best practices.

When developing a widget, you can access options from both the Server Script and the Client Script in the following way:

##### Client Script
```javascript
function() {
  /* widget controller */
  var c = this;
	console.log(c.options.text_color) //Outputs the text_color option for this instance
}
```

##### Server Script
```javascript
(function() {
	 $sp.log(options.text_color) //Logs the value of the text_color option to the browser console.
})();
```

#### Default Options

Before an option value is set on an instance, it will appear as an undefined value when you access that option variable. Therefore, it's a good idea to specify default values for your options in the server script of a widget (to handle the situation where those option values haven't been provided yet).

Luckily, in Javascript, that's easy:

##### Server Script
```javascript
(function() {
  options.text_color = options.text_color || "blue";
  options.maximum_entry_count = options.maximum_entry_count || 5;
})
```
