### $sp API
Service Portal provides a set of convenience methods found on the global `$sp` object, which is available in any widget server script.

| Method | Description |
| :------ | :----------- |
| [canReadRecord](#canReadRecord)(Mixed, *opt String*): boolean | Returns true if the user can read the specified GlideRecord. |
| [getCatalogItem](#getCatalogItem)(String): Object | Returns a model and view model for a sc_cat_item or sc_cat_item_guide. |
| [getDisplayValue](#getDisplayValue)(String): String | Returns a display value from a field on a record in this order: <br/>1. The widget's sp_instance* record<br/>2.
| [getField](#getField)(GlideRecord, String): Object | Returns {display_value, label, type, value} for a given field on a GlideRecord. |
| [getFields](#getFields)(GlideRecord, String): Array | Like getField Checks the specified field names, and returns a comma seperated list of valid names. |
| [getFieldsObject](#getFieldsObject)(GlideRecord, String) | Checks the specified field names, and returns an object containing the valid names. |
| [getForm](#getForm)(String table, String sys_id, /*Optional String*/ encodedQuery, /*Optional String*/ view)|Returns the form|
| [getListColumns](#getListColumns)(String tableName, String view): |Returns a list of the specified table's columns in the specified view|
| [getMenuItems](#getMenuItems)(String sys_id): Array | Returns the menu items for the specified instance |
| [getMenuHREF](#getMenuHREF)(GlideRecord): String | Returns the (?id=) portion of the URL based on the sp_menu type. |
| [getParameter](#getParameter)(String): Object | Returns the value of a given key from the query string or post body. |
| [getPortalRecord](#getPortalRecord)(): GlideRecord  | Returns the portal's GlideRecord. |
| [getRecord](#getRecord)(): Glide | Returns the GlideRecord for the current sp_instance\*. Returns null if the widget is embedded by another widget. |
| [getRecordDisplayValues](#getRecordDisplayValues) (Object, GlideRecord, String): void | Copies display values for the specified field names from a GlideRecord into the data parameter. |
| [getRecordElements](#getRecordElements)(Object, GlideRecord, String): void | Copies the value and display value for the specified field names from a GlideRecord into the data parameter. |
| [getRecordValues](#getRecordValues) (Object, GlideRecord, String): void | Copies values for the specified field names from a GlideRecord into the data parameter. |
| getStream(String, String): Object | Get the activity stream for a record. |
| getUserInitials() | Returns the user's initials as a string. |
| [getValue](#getValue)(String): Object | Like [getDisplayValue](#getDisplayValue) except that it returns the value instead of the display value. |
| [getValues](#getValues)(Object, String): void | Copies values from the request or instance into the data parameter. |
| [getValues](#getValues)(Object): void | Copies values from the widget's sp_instance GlideRecord into the data parameter. |
| [getWidget](#getWidget)(String, Object): Object | Returns a widget model for embedding a widget inside another widget. |
| getSCRecord(): Object | Returns sc_cat_item record for the portal's catalog with sys_class_name != sc_cat_item_wizard and active = true in the query. GlideRecord returned has not yet triggered the query. |
| logStat(String type, String table, String id, *opt String comments*): void | Create a new entry in the `sp_log` table with a table name, a record sys_id from that name, and some type and optional comments. Handy for doing things like logging searches or visits to pages, etc. |


<a name="getPortalRecord"></a> $sp.getPortalRecord()
------
Useful for getting the current portal context. It returns the sp_portal GlideRecord if there is one.

- $sp.getPortalRecord( )  
	- **Parameters**
		- None  
	- **Returns**
		- (*GlideRecord*) The sp_portal record of the current portal context or null.

Server Script

```javascript
(function() {
	var portalGr = $sp.getPortalRecord();
	data.logo = portalGr.getDisplayValue("logo");
	data.homepage = portalGr.getDisplayValue("homepage.id");
})();
```
<br />
HTML Template

```html
<div>
	<img ng-src="{{::c.data.logo}}" />
	<a href="?id={{::c.data.homepage}}">Click here to go home</a>
</div>
```
<br/>
Result
![Screenshot](/assets/widget_server_script_apis/getPortalRecord.png)

<a name="getWidget"></a> $sp.getWidget()
-----
Gets a widget by id or sys_id, executes that widget's server script using the provided options, then returns the widget model.

- $sp.getWidget( widget_id, options ): Object
	- **Parameters**
		- (*String*) widget\_id  
		Can be a widget_id or widget sys_id.  
		- (*Object*) options  
		An object to pass to the widget's server script. Refer to this object as **options** in your server script.
	- **Returns**  
		- (*Object*) A widget model to be used with \<sp-widget />.

Server Script

```javascript
data.myWidget = $sp.getWidget('widget_id', {p1: param1, p2: param2});
```
<br />
HTML Template

```html
<sp-widget widget="c.data.myWidget"></sp-widget>
```
<br />
For more information and examples refer to the [Embedded Widgets guide](widget_embedded.md).

<a name="canReadRecord"></a> $sp.canReadRecord()
-----
Useful for quickly determining if a record is valid and if the logged-in user has access to it.

> If the record type is kb_knowledge, sc_cat_item, or sc_category it also checks if the user can view that item.

- $sp.canReadRecord( gr ): Boolean
	- **Parameters**
		- (*GlideRecord*) gr  
		 A glide record
	- **Returns**
		- (*Boolean*) True if the record is valid and readable
- $sp.canReadRecord( table, sys_id ): Boolean
	- **Parameters**
		- (*String*) table  
		 A table name to query.
		- (*String*) sys_id  
		 The record sys_id to query.
	- **Returns**
		- (*Boolean*) True if the record is valid and readable

Server Script

```javascript
data.items = [];
data.userName = gs.getUserDisplayName();
var gr = new GlideRecord("sc_cat_item");
gr.query();
while(gr.next() && data.items.length < 10) {
	if ($sp.canReadRecord(gr)) {
		data.items.push(gr.getDisplayValue("name"));
	}
}
```
<br />
HTML Template

```html
<div class="panel panel-default">
	<div class="panel-heading">Hi, {{c.data.userName}}!</div>
	<div class="panel-body">
		Here are some things you can order:
		<ul><li ng-repeat="item in c.data.items">{{item}}</li></ul>
	</div>
</div>
```
<br/>
Result
![Screenshot](/assets/widget_server_script_apis/canReadRecord.png)

> Notice how the list of items is different based on the logged in user

<a name="getCatalogItem"></a> $sp.getCatalogItem()
-----
A quick way to get all of the data necessary to render and order a catalog item using \<sp-model />. If you just need to get a catalog item to show its picture or name, consider using GlideRecord to query the sp_cat_item table.

The following example demonstrates how to use getCatalogItem and \<sp-model /> together.

- $sp.getCatalogItem( sys_id ): Object
	- **Parameters**
		- (*String*) sys_id  
		 The sys_id of the catalog item(sc_cat_item) or order guide(sc_cat_item_guide).
	- **Returns**
		- (*Object*) An object containing the catalog item variable model, view, sections, pricing and client scripts.

Server Script

```javascript
(function() {
	var sys_id = $sp.getParameter("sys_id")
	data.catItem = $sp.getCatalogItem(sys_id);
})();
```
<br/>
Client Script

```javascript
function($http, spUtil) {
	var c = this;
	var submitting = false;
	c.getIt = function() {
		if (submitting) return;
		$http.post(spUtil.getURL('sc_cat_item'), c.data.catItem).success(function(response) {
			if (response.answer) {
				c.req = response.answer;
				c.req.page = c.req.table == 'sc_request' ? 'sc_request' : 'ticket';
			}
		});
	}
}
```

<br/>
SCSS

```css

.img-bg {
	padding: 5px;
	background-color: $brand-primary;
}

.img-responsive {
	margin: 0 auto;
}

.cat-icon {
	display: block;
	margin: -40px auto 0;
}
```
<br/>

HTML Template

```html
<div class="col-sm-4">
  <div class="panel panel-default">
    <div class="img-bg">
      <img ng-src="{{::data.catItem.picture}}" class="img-responsive" />
    </div>
    <span class="cat-icon fa fa-stack fa-lg fa-3x hidden-xs">
      <i class="fa fa-circle fa-stack-2x text-success"></i>
      <i class="fa fa-desktop fa-stack-1x fa-inverse"></i>
    </span>
    <div class="panel-body">
      <p class="lead text-center">{{::data.catItem.name}}</p>
      <ul class="list-unstyled">
        <li class="text-center" ng-if="::data.catItem.price">${Price}: {{::data.catItem.price}}</li>
      </ul>
      <sp-model form-model="::data.catItem" mandatory="mandatory"></sp-model>
      <p ng-if="c.req" class="text-center text-success">
        ${Request created!} <a href="?id={{c.req.page}}&table={{c.req.table}}&sys_id={{c.req.sys_id}}">{{c.req.number}}</a>
      </p>
      <button ng-if="!c.req" class="btn btn-default btn-block" ng-click="c.getIt()">${Get it}</button>
    </div>
  </div>
</div>
```

<br/>

Result

![Screenshot](/assets/widget_server_script_apis/getCatalogItem.png)


<a name="getDisplayValue"></a> $sp.getDisplayValue()
-----
Returns the display value of a given field (if it exists and has a value) from either the widget's sp_instance or the sp_portal record. Refer to the following diagram:

![Page map with widget instance](/assets/widget_server_script_apis/getDisplayValue_pagemap.png)

This map visualizes a service portal page with one widget on it. Calling $sp.getDisplayValue("title") would return the display value of the title field on the widget's sp_instance record. If the title field didn't exist or was empty, then it would try the same operation on the the sp_portal record for the current portal context.

> Note - Embedded widgets do not have sp_instance records.

<br/>

- $sp.getDisplayValue( fieldName ): String
	- **Parameters**
		- (*String*) fieldName
		 The field name to get the display value of.
	- **Returns**
		- (*String*) A display value from either the sp_instance record or sp_portal record.

<br/>
Server Script

```javascript
(function() {
	data.title = $sp.getDisplayValue("title");
	data.catalog = $sp.getDisplayValue("sc_catalog");
})();
```

<br/>
HTML Template

```html
<div>
	<h1>sp_instance.title: {{::data.title}}</h1>
	<h1>sp_portal.sc_catalog: {{::data.catalog}}</h1>
</div>
```

<br/>
Result

![Screenshot](/assets/widget_server_script_apis/getDisplayValue.png)

<a name="getRecordElements"></a> $sp.getRecordElements()
-----
Copies display values for the specified field names from a GlideRecord into the data parameter.


- $sp.getRecordElements( Object, GlideRecord, String ): void 
	- **Parameters**
		- (*Object*) data 
		 Must pass data object instantiated by the server.
		- (*GlideRecord*) GlideRecord 
		 Any GlideRecord of data
		- (*String*) String 
		 Comma-delimited string of fieldnames

	- **Returns**
		- (*Void*)
		 Field objects will be added to data
<br/>
Server Script

```javascript
(function($sp) {
        var gr = new GlideRecord("tablename");
	var fieldnames = "sys_id,field_name";
 	$sp.getRecordElements(data, gr, fieldnames); 
})($sp);
```

<a name="getValue"></a> $sp.getValue()
-----
Returns the value of a given field (if it exists and has a value) from either the widget's sp_instance or the sp_portal record. See [getDisplayValue](#getDisplayValue) for more info.


- $sp.getValue( fieldName ): Object
	- **Parameters**
		- (*String*) fieldName
		 The field name to get the value of.
	- **Returns**
		- (*Object*) A value from either the sp_instance record or sp_portal record.

<br/>
Server Script

```javascript
(function() {
	data.title = $sp.getValue("title");
	data.catalog = $sp.getValue("sc_catalog");
})();
```

<br/>
HTML Template

```html
<div>
	<h1>sp_instance.title: {{::data.title}}</h1>
	<h1>sp_portal.sc_catalog: {{::data.catalog}}</h1>
</div>
```

<br/>
Result

![Screenshot](/assets/widget_server_script_apis/getValue.png)
