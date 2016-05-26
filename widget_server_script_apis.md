### $sp API
Service Portal provides a set of convenience methods found on the global `$sp` object, which is available in any widget server script.

| Method | Description |
| :------ | :----------- |
| [getPortalRecord](#getPortalRecord)() : GlideRecord   | Returns the portal's GlideRecord |
| [getValue](#getValue)(String) : Object | Returns a value from an object or GlideRecord in this order: <br/>1. The http request<br/> 2. The widget's sp_instance* record<br/>3. The current sp_portal record<br />or returns null |
| [getDisplayValue](#getDisplayValue)(String): String | Like [getValue](#getValue) except that it returns the display value.|
| [getValues](#getValues)(Object, String): void | Copies values from the request or instance into the data parameter. |
| [getValues](#getValues)(Object): void | Copies values from the widget's sp_instance GlideRecord into the data parameter. |
| [getRecordValues](#getRecordValues) (Object, GlideRecord, String): void | Copies values of the specified field names into the data parameter. Field names should be a comma separated string. |
| [getRecordDisplayValues](#getRecordDisplayValues) (Object, GlideRecord, String): void |Copies display values of the specified field names into the data parameter. |
| [getRecordElements](#getRecordElements)(Object, GlideRecord, String): void | Copies the record element's name, display value, and value into the data parameter. |
| [getWidget](#getWidget)(String, Object): Object | Returns a widget model for embedding a widget inside another widget. |
| [getRecord](#getRecord) () | GlideRecord for instance / input parms. Returns null if the GlideRecord cannot be found.|
| getStream(String table, String sys_id)|Get the activity stream for a record.|
| getListColumns(String tableName, String view)|Returns a list of the specified table's columns in the specified view|
| getUserInitials () | Returns the user's initials as a string |
| getField(GlideRecord, String) | Returns the field's information|
| getFields(GlideRecord, String) | Checks the specified field names, and returns a comma seperated list of valid names. |
| getFieldsObject(GlideRecord, String) | Checks the specified field names, and returns an object containing the valid names. |
| canReadRecord(GlideRecord)|Determines if the user can read the specified GlideRecord|
| canReadRecord(String table, String id)|Determines if the user can read the specified GlideRecord|
| getCatalogItem(String itemID)|Returns the catalog item|
| getForm(String table, String sys_id, /*Optional String*/ encodedQuery, /*Optional String*/ view)|Returns the form|
| getMenuItems (String sys_id) | Returns the menu items for the specified instance|
| getMenuHREF (GlideRecord gr)|Builds the href (?id=) portion of the URL for the specifed page |

<a name="getPortalRecord"></a> $sp.getPortalRecord
------
$sp.getPortalRecord(): GlideRecord

Useful for getting the current portal context. It returns the sp_portal GlideRecord if there is one.

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
![Screenshot](./assets/widget_server_script_apis/getPortalRecord.png)

<a name="getWidget"></a> $sp.getWidget
-----

$sp.getWidget(String, Object): Object

Gets a widget by id or sys_id, executes that widget's server script using the provided options, then returns the widget model.

**Parameters**  

- (*String*) widget\_id  
   Can be a widget_id or widget sys_id.  
- (*Object*) options  
   An object to pass to the widget's server script. Refer to this object as **options** in your server script.
   
**Returns**  

A widget model to be used with \<sp-widget />.

```javascript
var w = $sp.getWidget('widget_id', {p1: param1, p2: param2});
```