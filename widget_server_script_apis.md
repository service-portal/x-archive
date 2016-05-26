### $sp API
Service Portal provides a set of convenience methods found on the global `$sp` object, which is available in any widget server script.

| Method | Description |
| :------ | :----------- |
| [getPortalRecord](#getPortalRecord) () : <small>GlideRecord</small>   | Returns the portal's GlideRecord |
| [getValue](#getValue) (<small>**String**</small> field) : <small>Object</small> | Returns a value from an object or GlideRecord in this order: <br/>1. The http request<br/> 2. The widget's sp_instance* record<br/>3. The current sp_portal record<br />or returns null |
| [getWidgetParameters](#getWidgetParameters) () | Returns the widget's parameters in an object, or an empty object if the widget has no parameters.|
| [getDisplayValue](#getDisplayValue) (<small>**String**</small> name) | Returns the display value of the specified parameter. Returns an empty string if the request, instance, and portal do not exist. Returns null if the request exists but has no such parameter, or the instance exists but has no such parameter.|
| [getValues](#getValues) (<small>**Object**</small> data, <small>**String**</small> names) : <small>void</small> |Copies values from the request or instance into the data parameter. |
| [getValues](#getValues) (<small>**Object**</small> data) : <small>void</small> | Copies values from the widget's sp_instance GlideRecord into the data parameter |
| [getRecordValues](#getRecordValues) (<small>**Object**</small> data, <small>**GlideRecord**</small> from, <small>**String**</small> fieldNames) : <small>void</small> |Copies values of the specified field names into the data parameter. Field names should be a comma separated string. |
| [getRecordDisplayValues](#getRecordDisplayValues) (<small>**Object**</small> data, <small>**GlideRecord**</small> from, <small>**String**</small> fieldNames) : <small>void</small> |Copies display values of the specified field names into the data parameter. |
| [getRecordElements](#getRecordElements) (<small>**Object**</small> data, <small>**GlideRecord**</small> from, <small>**String**</small> names) : <small>void</small> | Copies the record element's name, display value, and value into the data parameter. |
| [getWidgetScope](#getWidgetScope) (<small>**String**</small> instanceId) : <small>Object</small> | Used for including a widget inside another widget (eg. menu inside header). InstanceId can be a widget instance sys_id or ID. Returns a widget, or an empty object if the instanceID is empty or invalid.|
| [getWidgetFromInstance](#getWidgetFromInstance) (<small>**String**</small> instanceID) | Returns a widget from the specified instance.|
| [getWidget](#getWidget) (<small>**String**</small> widgetID, <small>**Object**</small> widgetParams) | Used for embedding a widget inside another widget. |
| [getRelatedList](#getRelatedList) (<small>**String**</small> tableName, <small>**String**</small> foreignKey)|Gets the related list of data for a instance. Returns [{}, {}, ...]|
| [getRecord](#getRecord) () | GlideRecord for instance / input parms. Returns null if the GlideRecord cannot be found.|
| [getVariables](#getVariables)() | Returns the table's variables.|
| [getFilterBreadcrumbs](#getFilterBreadcrumbs) (<small>**String**</small> table, <small>**String**</small> query, <small>**String**</small> fixedQuery): <small>Array</small> | Returns an array of objects where each object contains the breadcrumb label, value, and flags for if fixed and if removed. |
| [getRecordVariables](#getRecordVariables) (<small>**GlideRecord**</small> gr) | Returns the task variables for a requested catalog item. | 
| getVariablesArray () | Returns the tables variables. |
| getRecordVariablesArray(<small>**GlideRecord**</small> gr)|Returns the records variables|
| getStreamEntries()|Get activity stream entries by the instance context.|
| getStream()|Get the activity stream by the instance context.|
| getStream(<small>**String**</small> table, <small>**String**</small> sys_id)|Get the activity stream for a record.|
| getListColumns(<small>**String**</small> tableName)|Returns list of columns for the specified table's mobile view|
| getListColumns(<small>**String**</small> tableName, <small>**String**</small> view)|Returns a list of the specified table's columns in the specified view|
| getUserInitials () | Returns the user's initials as a string |
| getField(<small>**GlideRecord**</small> gr, <small>**String**</small> name)|Returns the field's information|
| getFields(<small>**GlideRecord**</small> gr, <small>**String**</small> names)|Checks the specified field names, and returns a comma seperated list of valid names.|
| getFieldsObject(<small>**GlideRecord**</small> gr, <small>**String**</small> names)|Checks the specified field names, and returns an object containing the valid names.|
| logStat(<small>**String**</small> type, <small>**String**</small> table, <small>**String**</small> id, /*Optional String*/ text)|Adds a record to the Service Portal statistics log |
| logSearch ( <small>**String**</small> table, <small>**String**</small> terms, <small>**Int**</small> count ): <small>void</small> | Adds a record to the Service Portal statistics log, specifically for a search|
| canSeePage(<small>**String**</small> pageID)|Determines if the user is allowed to see the specified page|
| canReadRecord(<small>**GlideRecord**</small> gr)|Determines if the user can read the specified GlideRecord|
| canReadRecord(<small>**String**</small> table, <small>**String**</small> id)|Determines if the user can read the specified GlideRecord|
| getCatalogItem(<small>**String**</small> itemID)|Returns the catalog item|
| getForm(<small>**String**</small> table, <small>**String**</small> sys_id, /*Optional String*/ encodedQuery, /*Optional String*/ view)|Returns the form|
| getKBCategoryArticles(<small>**String**</small> category, /*Optional int*/ limit)|Returns KB articles in the specified category, includes all subcategories.|
| getKBSiblingCategories(<small>**String**</small> categoryID)| Returns KB categories with the same parent as the specified category.|
| getKBCount(<small>**String**</small> knowledgeBaseID)|Returns the number of KB articles|
| getSubCategories(<small>**String**</small> categoryId)|Returns the KB subcategories of the specified category|
| getKBTopCategoryID(<small>**String**</small> catId)|Returns the top category in the hierarch containing the specified category.|
| getKBRecord()|Returns KB record for the portal's knowledge base with workflow_state = published in the query|
| getSCRecord()|Returns the service catalog record for the portal's catalog with proper class name and active = true in the query|
| stripHTML(<small>**String**</small> html)|Removes non breaking spaces from the specified string|
| getMenuItems(<small>**String**</small> sys_id)|Returns the menu items for the specified instance|
| getMenuHREF(<small>**GlideRecord**</small> gr)|Builds the href (?id=) portion of the URL for the specifed page|
| log(<small>**Object**</small> message)|Sends the message to the console log |

<a name="getPortalRecord"></a> $sp.getPortalRecord(): GlideRecord
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
<br/>
Result
![Screenshot](./assets/widget_server_script_apis/getPortalRecord.png)

<a name="getWidget"></a> $sp.getWidget(String, Object): Object
-----

```javascript
var w = $sp.getWidget('widget_id', {p1: param1, p2: param2});
```