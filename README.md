# Service Portal Documentation
This reference guide contains documentation for developers.

### Service Portal
Service Portal contains of two parts: 
- The framework: a set of APIs and JavaScript Angular Services and Directives that help to render a Portal.
- The `sp_config` Portal. A set of tools to help you configure and create and mantain widgets.

### Portal
A portal contains all the configuration settings for the site. The `url_suffix` helps to namespace the portal from other portals.

### Page
A page is a collection of containers rows and columns that contain widgets built using the Service Portal Designer. Pages are referenced by their Page ID. Pages can be used on multiple portals.




### Widget
A widget is a superset of an Angular 1.x directive that is tightly coupled to a server-side JavaScript code block powered by the Rhino engine under the ServiceNow platform.
Since widgets are `read-only` to benefit from future updates, you can't update their code. If you need to make major changes,
clone the widget and give it another `name` and `id`.

### Widget Instance
A widget instace is a reference to a widget that contains: location, properties and CSS especific for that instance. A widget used multiple times in the same page, will use multiple instances.

#### Widget HTML
Contains the Angular template. It uses the `controllerAs c` syntax for basic binding.

#### Client Script
Angular controller.

##### this.server.update()


#### Server Script
Rhino Javascript

<table width="100%">
	<tr>
		<th valign="top" colspan="3" align="left"><a href="#props" name="props">Special Variables</a></th>
	</tr>
	<tr>
		<th valign="top" width="120px" align="left">Property</th>
		<th valign="top" align="left">Description</th>
	</tr>
	<tr>
		<td valign="top"><code>input</code></td>
		<td valign="top">An object containing client-side properties set under `c.data`</td>
	</tr>
	<tr>
		<td valign="top"><code>data</code></td>
		<td valign="top">An object containing properties set during server-side execution</td>
	</tr>
</table>
