#### Widget Server Script
This is where you put the server-side logic for your widget. This is helpful primarily with interacting with the Glide platform through our server-side APIs. If you have experience writing Javascript within our platform, you will have no problem writing server scripts.
```javascript
if (input) {
	var r = new RESTMessage('Yahoo Finance', 'get');
	r.setStringParameter('symbol', input.symbol);
	var response = r.execute();
	data.price = response.getBody();
}
```

Server Side JavaScript executed within the context of the widget intance related to it.

[Server-side variables](#server_side_variables)

| Property | Description |
| :------ | :----------- |
| `input`   | An object containing client-side properties set under `c.data`. It will have an `undefined` value until the client-side controller calls `c.server.update()` |
| `data` | An object containing properties set during server-side execution |
| `option`    | An object containing the schema option properties |


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
