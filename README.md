# Service Portal Documentation
This reference guide contains documentation for developers.

### Service Portal
Service Portal contains of two parts: 
- The framework: a set of APIs and JavaScript Angular Services and Directives that help to render a Portal.
- The `sp_config` Portal. A set of tools to help you configure and create and mantain widgets.

### Portal
A portal contains all the configuration settings for the site. The `url_suffix` helps to namespace the portal from other portals.

### Page




### Widget
A widget is a superset of an Angular 1.x directive that is tightly coupled to a server-side JavaScript code block powered by the Rhino engine under the ServiceNow platform.
Since widgets are `read-only` to benefit from future updates, you can't update their code. If you need to make major changes,
clone the widget and give it another `name` and `id`.

### Widget Instance
A widget instace is a reference to a widget that contains: location, properties and CSS especific for that instance. A widget used multiple times in the same page, will use multiple instances. 
