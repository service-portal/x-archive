### $sp API
Service Portal provides a set of convenience methods found on the global `$sp` object, which is available in any widget server script.

| Method | Description |
| :------ | :----------- |
| [getPortalRecord()](#getPortalRecord)   | Returns the portal's GlideRecord |
| getValue( **string** key ) | Returns the value of the specified field. Null if the request does not exist or has no such parameter, the instance does not exist or has no such parameter, or the portal is null or has no such parameter |
| getWidgetParameters() | Returns the widget's parameters in an object, or an empty object if the widget has no parameters.|
| getDisplayValue( **string** name ) | Returns the display value of the specified parameter. Returns an empty string if the request, instance, and portal do not exist. Returns null if the request exists but has no such parameter, or the instance exists but has no such parameter.|
|`getValues(/*Scriptable*/ data, /*String*/ names)`|Copies values from the request or instance into the data parameter. Returns void.|
|`getValues(/*Scriptable*/ data)`|Copies values from the instance GlideRecord into the data parameter. Returns void.|
|`getRecordValues(/*Scriptable*/ data, /*GlideRecord*/ from, /*String*/ names)`|Copies values of the specified field names into the data parameter. Returns void.|
|`getRecordDisplayValues(/*Scriptable*/ data, /*GlideRecord*/ from, /*String*/ names)`|Copies display values of the specified field names into the data parameter. Returns void.|
|`getRecordElements(/*Scriptable*/ data, /*GlideRecord*/ from, /*String*/ names)`|Copies the record element's name, display value, and value into the data parameter. Returns void.|
|`getWidgetScope(/*String*/ instanceID)`| Used for including a widget inside another widget (eg. menu inside header). InstanceID can be a widget instance sys_id or ID. Returns a widget, or an empty object if the instanceID is empty or invalid.|
|`getWidgetFromInstance(String instanceID)`|Returns a widget from the specified instance.|
|`getWidget(/*String*/ widgetID, /*Object*/ widgetParams)`|Used for including a widget inside another widget without a instance.<pre>var w = $sp.getWidget('widget_id', {p1: param1, p2: param2});</pre>|
|`getRelatedList(/*String*/ tableName, /*String*/ foreignKey)`|Gets the related list of data for a instance. Returns [{}, {}, ...]|
|`getRecord()`|GlideRecord for instance / input parms. Returns null if the GlideRecord cannot be found.|
|`getVariables()`|Returns the table's variables.|
|`getFilterBreadcrumbs(/*String*/ table, /*String*/ query, /*String*/ fixedQuery)`|Returns an array of objects where each object contains the breadcrumb label, value, and flags for if fixed and if removed.|
|`getRecordVariables(/*GlideRecord*/ gr)`|Returns the task variables.| 
|`getVariablesArray()`|Returns the tables variables.|
|`getRecordVariablesArray(/*GlideRecord*/ gr)`|Returns the records variables|
|`getStreamEntries()`|Get activity stream entries by the instance context.|
|`getStream()`|Get the activity stream by the instance context.|
|`getStream(/*String*/ table, /*String*/ sys_id)`|Get the activity stream for a record.|
|`getListColumns(/*String*/ tableName)`|Returns list of columns for the specified table's mobile view|
|`getListColumns(/*String*/ tableName, /*String*/ view)`|Returns a list of the specified table's columns in the specified view|
|`getUserInitials()`|Returns the user's initials as a string|
|`getField(/*GlideRecord*/ gr, /*String*/ name)`|Returns the field's information|
|`getFields(/*GlideRecord*/ gr, /*String*/ names)`|Checks the specified field names, and returns a comma seperated list of valid names.|
|`getFieldsObject(/*GlideRecord*/ gr, /*String*/ names)`|Checks the specified field names, and returns an object containing the valid names.|
|`logStat(/*String*/ type, /*String*/ table, /*String*/ id, /*Optional String*/ text)`|Adds a record to the Service Portal statistics log|
|`logSearch(/*String*/ table, /*String*/ terms, /*int*/ count)`|Adds a record to the Service Portal statistics log, specifically for a search|
|`canSeePage(/*String*/ pageID)`|Determines if the user is allowed to see the specified page|
|`canReadRecord(/*GlideRecord*/ gr)`|Determines if the user can read the specified GlideRecord|
|`canReadRecord(/*String*/ table, /*String*/ id)`|Determines if the user can read the specified GlideRecord|
|`getCatalogItem(/*String*/ itemID)`|Returns the catalog item|
|`getForm(/*String*/ table, /*String*/ sys_id, /*Optional String*/ encodedQuery, /*Optional String*/ view)`|Returns the form|
|`getKBCategoryArticles(/*String*/ category, /*Optional int*/ limit)`|Returns KB articles in the specified category, includes all subcategories.|
|`getKBSiblingCategories(/*String*/ categoryID)`| Returns KB categories with the same parent as the specified category.|
|`getKBCount(/*String*/ knowledgeBaseID)`|Returns the number of KB articles|
|`getSubCategories(/*String*/ categoryId)`|Returns the KB subcategories of the specified category|
|`getKBTopCategoryID(/*String*/ catId)`|Returns the top category in the hierarch containing the specified category.|
|`getKBRecord()`|Returns KB record for the portal's knowledge base with workflow_state = published in the query|
|`getSCRecord()`|Returns the service catalog record for the portal's catalog with proper class name and active = true in the query|
|`stripHTML(/*String*/ html)`|Removes non breaking spaces from the specified string|
|`getMenuItems(/*String*/ sys_id)`|Returns the menu items for the specified instance|
|`getMenuHREF(/*GlideRecord*/ gr)`|Builds the href (?id=) portion of the URL for the specifed page|
|`log(/*Object*/ message)`|Sends the message to the console log|

<a name="getPortalRecord" href="#getPortalRecord">#</a> $sp.getPortalRecord()
------
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