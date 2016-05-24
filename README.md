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

### Portal Configuration

| Property | Description |
| :------ | :----------- |
| Title   | Page `title` |
| Url Suffix | helps to namespace the portal from other portals. |
| Homepage    | The first page that the portal will load |
| Knowledge base | Default knowledge base |


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



---
## Widget Dependencies
In Service Portal, it is possible to link Javascript and CSS files to widgets. This allows developers to create dependencies between their widgets and third party libraries, external style sheets, and angular modules. Dependencies are only fetched from the server at the time that they are needed, which keeps initial page loads very fast. 

Following is a step-by-step guide on creating new dependency packages and associating them with widgets.

### Creating a Dependency Package
A dependency package is a collection of Javascript and CSS files that can be then connected to a widget. Dependencies can be found in the table `sp_dependency`, or by navigating to the Service Portal module in the navigator and selecting the Dependencies submodule.

In a dependency record, you will define the following: 

1. Name - The name that your dependency will be referred to by (Useful for selecting a dependency from a dropdown list)

2. Include on page load - Select if you want your dependency to be loaded onto the page on initial page load of Service Portal, or leave unchecked to load the dependency only when the linked widget is loaded onto a page.

3. Angular module name - Only necessary if the linked Javascript is an Angular module. Provide the name of the Angular module name that you are loading in, so that it can be injected into the Service Portal angular application. Leave blank if not applicable.

Once these fields are defined, you can start creating records in the `sp_js_include` and `sp_css_include` table and adding them to the JS Includes and CSS Includes related lists in a dependency record.
