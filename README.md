# Service Portal Documentation
This reference guide contains documentation for Service Portal Developers.

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
Contains the an Angular template. It uses the `controllerAs c` syntax for basic binding.
```html
<div>
${Symbol Lookup}: 
<input ng-model="c.data.symbol" 
ng-model-options="{debounce: 750}" ng-change="c.update()" placeholder="Type stock symbol" />
<div ng-show="c.data.symbol" style="font-size: 2em;">        
  <p>${Stock Price}: 
  	<span ng-if="!c.data.price">${Requesting stock price}</span><span>{{c.data.price | currency:"$"}}</span>
  </p>
 <img ng-src="http://chart.finance.yahoo.com/z?s={{c.data.symbol}}&t=1d&z=l"/>
</div>
</div>
```
#### Client Script
```javascript
function() {	
	var c = this;
	c.update = function() {
		c.data.price = false;
		c.server.get({symbol: c.data.symbol}).then(function(r) {			
			c.data.price = r.data.price;			
		});
	}
}
```

<table width="100%">
	<tr>
		<th valign="top" colspan="3" align="left"><a href="#special" name="special">Special Methods</a></th>
	</tr>
	<tr>
		<th valign="top" width="120px" align="left">Property</th>
		<th valign="top" align="left">Description</th>
	</tr>
	<tr>
		<td valign="top"><code>this.server.get(input)</code></td>
		<td valign="top">Calls the server and sends custom <code>input</code></td>
	</tr>
	<tr>
		<td valign="top"><code>this.server.update()</code></td>
		<td valign="top">Calls the server and <code>this.data</code> is automatically send to server side</td>
	</tr>
	<tr>
		<td valign="top"><code>this.server.refresh()</code></td>
		<td valign="top">Calls the server and automatically replaces the current options and data from the server response.</td>
	</tr>	
</table>

#### Server Script
```javascript
if (input) {
	var r = new RESTMessage('Yahoo Finance', 'get');
	r.setStringParameter('symbol', input.symbol);
	var response = r.execute();
	data.price = response.getBody();
}
```

Server Side JavaScript executed within the context of the widget intance related to it.

<table width="100%">
	<tr>
		<th valign="top" colspan="3" align="left"><a href="#special" name="special">Special Variables</a></th>
	</tr>
	<tr>
		<th valign="top" width="120px" align="left">Property</th>
		<th valign="top" align="left">Description</th>
	</tr>
	<tr>
		<td valign="top"><code>input</code></td>
		<td valign="top">An object containing client-side properties set under <code>c.data</code>. It will have an <code>undefined</code> value until the client-side controller calls <code>c.server.update()</code></td>
	</tr>
	<tr>
		<td valign="top"><code>data</code></td>
		<td valign="top">An object containing properties set during server-side execution</td>
	</tr>
	<tr>
		<td valign="top"><code>option</code></td>
		<td valign="top">An object containing the schema option properties</td>
	</tr>	
</table>

<table width="100%">
	<tr>
		<th valign="top" colspan="3" align="left"><a href="#props" name="props">Debugging</a></th>
	</tr>
	<tr>
		<th valign="top" width="120px" align="left">Method</th>
		<th valign="top" align="left">Description</th>
	</tr>
	<tr>
		<td valign="top"><code>console.log(String|Object)</code></td>
		<td valign="top">Ouputs into the Browser console, server-side JavaScript objects and strings that can be displayed</td>
	</tr>
	<tr>
		<td valign="top"><code>$sp.log(String|Object)</code></td>
		<td valign="top">Outputs into the Java console, server-side JavaScript objects and strings that can be displayed</td>
	</tr>
</table>
