#### Fields
In Service Portal, widgets can be attached to fields. Two ways to do this are as a macro field or a single line text field.

##### Macro
Adding a widget to a macro field will render the widget instead of the field.

##### Single Line Text
Adding a widget to a single line text field will be treated as a widget, but a value can also be stored in the text field. It will render the label of the field including the decorators, but where the field would render, it placed the widget instead.

In the client script, the field can then be accessed through

```#JavaScript
$scope.page.field
```
