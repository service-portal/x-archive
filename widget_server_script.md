#### Widget Server Script
This is where you put the server-side logic for your widget. This is helpful primarily with interacting with the Glide platform through ServiceNow [server-side APIs](http://wiki.servicenow.com/index.php?title=Server_API_Reference#gsc.tab=0). If you have experience writing Javascript within our platform, you will have no problem writing server scripts.
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
| [`$sp`](/widget_server_script_apis.md) | Global object used to access server script API |
