## Widget Server Script
This is where you put the server-side logic for your widget. This is helpful primarily with interacting with the Glide platform through ServiceNow [server-side APIs](https://developer.servicenow.com/app.do#!/api_doc?id=server). 

```javascript
if (input) {
	var r = new RESTMessage('Yahoo Finance', 'get');
	r.setStringParameter('symbol', input.symbol);
	var response = r.execute();
	data.price = response.getBody();
}
```

This code will be executed within the context of the widget instance related to it.

### Server-side properties and helpers

| Property | Description |
| :------ | :----------- |
| `input`   | An object containing client-side properties set under `c.data`. It will have an `undefined` value until the client-side controller calls `c.server.update()` |
| `data` | An object containing properties set during server-side execution |
| `options`    | An object containing the schema option properties |
| [`$sp`](widget_server_script_apis.md#sp-api) | Helper class used to access server script API |
