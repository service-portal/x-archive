# spUtil

Set of methods that perform common, often re-used functions. 

| Method | Description|
| :------ | :----------- |
| addErrorMessage(String message)| Displays a notification error message |

```javascript
spUtil.addErrorMessage("There has been an error processing your request")
```

<br/>

| Method | Description|
| :------ | :----------- |
| addInfoMessage(String message) | Displays a notification info message | 

```javascript
spUtil.addInfoMessage("Your order has been placed")
```

<br/>

| Method | Description|
| :------ | :----------- |
| addTrivialMessage(String message)| Displays a notification trivial message |

```javascript
spUtil.addTrivialMessage("Thanks for your order")
```

<br/>

| Method | Description|
| :------ | :----------- |
| get(String widgetId) | Gets a widget model by id or sys_id. Returns Promise. |

```javascript
spUtil.get("widget-cool-clock").then(function(response) {
    c.coolClock = response;
});
```

<br/>


| Method | Description|
| :------ | :----------- |
| format(String, Object) | Alternative to string concatenation | 

Let's say you want to build a string with variables: `'An error occurred: ' + error + ' when loading ' + widget`
instead of doing string concatenation you can use `format()`. 
```javascript
spUtil.format('An error ocurred: {error} when loading {widget}', {error: '404', widget: 'sp-widget'})
```

<br/>

| Method | Description|
| :------ | :----------- |
| refresh(Object $scope) | Calls the server and automatically replaces the current options and data from the server response. Returns Promise |

Same as `server.refresh()`  The diference is that you can define what $scope to pass over. 

<br/>

| Method | Description|
| :------ | :----------- |
| recordWatch(Object $scope, String table, String filter, Function callback)| watch for a table / filter update - callback when it happens |

```javascript
spUtil.recordWatch($scope, "live_profile", "sys_id=" + liveProfileId);
```
More documentation on recordWatch can be found [here](./widget_record_watch.md).

<br/>

| Method | Description|
| :------ | :----------- |
| update(Object $scope)  | Calls the server and `this.data` is automatically send to server side. Returns Promise. |

Same as `server.update()`. The diference is that you can define what $scope to pass over. 

`Do not try to use any other methods from spUtil() that are not listed here`













