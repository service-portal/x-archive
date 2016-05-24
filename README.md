# Service Portal Documentation
This reference guide contains documentation for Service Portal Developers.

>This site is nonofficial and not endorsed by ServiceNow.

### Index
[Widget Dependencies](/Widget_Dependencies.md)

[Widget Server Script](/widget_server_script.md)

[Widget CSS](/widget_css.md)

[Widget HTML](/widget_html.md)

[Widget Client Script](/widget_client_script.md)

[Widget Server Script APIs](/widget_server_script_apis.md)

### Service Portal
Service Portal contains of two parts: 
- *Framework*: a set of APIs and [Angular.js](https://angularjs.org/) services and directives that help to render portals.
- *Portals*: a group of pages linked by their pageId. For example: `sp_config` is a Portal contains a set tools to help you configure and create and mantain widgets.

### Page
A page is a collection of containers rows and columns that contain widgets built using the Service Portal Designer. Pages are referenced by their Page ID. Pages can be used on multiple portals.

### Widget
A widget is a superset of an Angular 1.x directive that is tightly coupled to a server-side JavaScript code block powered by the Rhino engine under the ServiceNow platform.
Since widgets are `read-only` to benefit from future updates, you can't update their code. If you need to make major changes,
clone the widget and give it another `name` and `id`.

### Widget Instance
A widget instace is a reference to a widget that contains: location, properties and CSS especific for that instance. A widget used multiple times in the same page, will use multiple instances.


### Embeded Widgets
The spWidget directive takes a widget model and renders the compiled widget exactly where you put it in your HTML Template. 

```html
<sp-widget widget="c.myCatItemWidget"></sp-widget>
```
