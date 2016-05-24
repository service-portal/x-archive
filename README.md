# Service Portal Documentation
This reference guide contains documentation for Service Portal Developers.

>This site is nonofficial and not endorsed by ServiceNow.

### Index
[Portal Configuration](/portal_configuration.md)

[Widget](/widget.md)

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
