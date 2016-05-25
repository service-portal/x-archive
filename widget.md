### Widget
A widget is a superset of an Angular 1.x directive that is tightly coupled to a server-side JavaScript code block powered by the Rhino engine under the ServiceNow platform.
Since widgets are `read-only` to benefit from future updates, you can't update their code. If you need to make major changes,
*clone* the widget and give it another `name` and `id`.

### Widget Instance
A widget instace is a reference to a widget that contains: location, properties and CSS especific for that instance. A widget used multiple times in the same page, will use multiple instances.


### Embeded Widgets
The spWidget directive takes a widget model and renders the compiled widget exactly where you put it in your HTML Template. 

***Learn more***

  - [Dependencies](/widget_dependencies.md)
  - [Server Script](/widget_server_script.md)
  - [CSS/SCSS](/widget_css.md)
  - [HTML](/widget_html.md)
  - [Client Script](/widget_client_script.md)
  - [Server Script APIs](/widget_server_script_apis.md)
  - [Embedded Widgets] (/widget_embedded.md)
