### $sp API
Service Portal provides a set of convenience methods found on the global `$sp` object, which is available in any widget server script.

<table width="100%">
	<tr>
		<th valign="top" colspan="3" align="left"><a href="#props" name="props">$sp</a></th>
	</tr>
	<tr>
		<th valign="top" width="120px" align="left">Method</th>
		<th valign="top" align="left">Description</th>
	</tr>
	<tr>
		<td valign="top"><code>getPortalRecord()</code></td>
		<td valign="top">Returns the portal's GlideRecord</td>
	</tr>
	<tr>
		<td valign="top"><code>getValue(/*String*/ name)</code></td>
		<td valign="top">Returns the value of the specified field. Null if the request does not exist or has no such parameter, the instance does not exist or has no such parameter, or the portal is null or has no such parameter</td>
	</tr>
	<tr>
		<td valign="top"><code>getWidgetParameters()</code></td>
		<td valign="top">Returns the widget's parameters in an object, or an empty object if the widget has no parameters.</td>
	</tr>
	<tr>
		<td valign="top"><code>getDisplayValue(/*String*/ name)</code></td>
		<td valign="top">Returns the display value of the specified parameter. Returns an empty string if the request, instance, and portal do not exist. Returns null if the request exists but has no such parameter, or the instance exists but has no such parameter.</td>
	</tr>
	<tr>
		<td valign="top"><code>getValues(/*Scriptable*/ data, /*String*/ names)</code></td>
		<td valign="top">Copies values from the request or instance into the data parameter. Returns void.</td>
	</tr>
	<tr>
		<td valign="top"><code>getValues(/*Scriptable*/ data)</code></td>
		<td valign="top">Copies values from the instance GlideRecord into the data parameter. Returns void.</td>
	</tr>
	<tr>
		<td valign="top"><code>getRecordValues(/*Scriptable*/ data, /*GlideRecord*/ from, /*String*/ names)</code></td>
		<td valign="top"Copies values of the specified field names into the data parameter. Returns void.></td>
	</tr>
	<tr>
		<td valign="top"><code>getRecordDisplayValues(/*Scriptable*/ data, /*GlideRecord*/ from, /*String*/ names)</code></td>
		<td valign="top">Copies display values of the specified field names into the data parameter. Returns void.</td>
	</tr>
	<tr>
		<td valign="top"><code>getRecordElements(/*Scriptable*/ data, /*GlideRecord*/ from, /*String*/ names)</code></td>
		<td valign="top">Copies the record element's name, display value, and value into the data parameter. Returns void.</td>
	</tr>
	<tr>
		<td valign="top"><code>getWidgetScope(/*String*/ instanceID)</code></td>
		<td valign="top">Used for including a widget inside another widget (eg. menu inside header). InstanceID can be a widget instance sys_id or ID. Returns a widget, or an empty object if the instanceID is empty or invalid.</td>
	</tr>
	<tr>
		<td valign="top"><code>getWidgetFromInstance(String instanceID)</code></td>
		<td valign="top">Returns a widget from the specified instance.</td>
	</tr>
	<tr>
		<td valign="top"><code>getWidget(/*String*/ widgetID, /*Object*/ widgetParams)</code></td>
		<td valign="top">Used for including a widget inside another widget without a instance.<pre>var w = $sp.getWidget('widget_id', {p1: param1, p2: param2});</pre></td>
	</tr>
	<tr>
		<td valign="top"><code>getRelatedList(/*String*/ tableName, /*String*/ foreignKey)</code></td>
		<td valign="top">Gets the related list of data for a instance. Returns [{}, {}, ...]</td>
	</tr>
	<tr>
		<td valign="top"><code>getParameter(/*String*/ name)</code></td>
		<td valign="top">Returns the value of the specified parameter from URL, JSON Body.</td>
	</tr>
	<tr>
		<td valign="top"><code>getRecord()</code></td>
		<td valign="top">GlideRecord for instance / input parms. Returns null if the GlideRecord cannot be found.</td>
	</tr>
	<tr>
		<td valign="top"><code>getVariables()</code></td>
		<td valign="top">Returns the table's variables.</td>
	</tr>
	<tr>
		<td valign="top"><code>getFilterBreadcrumbs(/*String*/ table, /*String*/ query, /*String*/ fixedQuery)</code></td>
		<td valign="top">Returns an array of objects where each object contains the breadcrumb label, value, and flags for if fixed and if removed.</td>
	</tr>
	<tr>
		<td valign="top"><code>getRecordVariables(/*GlideRecord*/ gr)</code></td>
		<td valign="top">Returns the task variables.</td>
	</tr>
	<tr>
		<td valign="top"><code>getVariablesArray()</code></td>
		<td valign="top">Returns the tables variables.</td>
	</tr>
	<tr>
		<td valign="top"><code>getRecordVariablesArray(/*GlideRecord*/ gr)</code></td>
		<td valign="top">Returns the records variables</td>
	</tr>
	<tr>
		<td valign="top"><code>getStreamEntries()</code></td>
		<td valign="top">Get activity stream entries by the instance context.</td>
	</tr>
	<tr>
		<td valign="top"><code>getStream()</code></td>
		<td valign="top">Get the activity stream by the instance context.</td>
	</tr>
	<tr>
		<td valign="top"><code>getStream(/*String*/ table, /*String*/ sys_id)</code></td>
		<td valign="top">Get the activity stream for a record.</td>
	</tr>
	<tr>
		<td valign="top"><code>getListColumns(/*String*/ tableName)</code></td>
		<td valign="top">Returns list of columns for the specified table's mobile view</td>
	</tr>
	<tr>
		<td valign="top"><code>getListColumns(/*String*/ tableName, /*String*/ view)</code></td>
		<td valign="top">Returns a list of the specified table's columns in the specified view</td>
	</tr>
	<tr>
		<td valign="top"><code>getUserInitials()</code></td>
		<td valign="top">Returns the user's initials as a string</td>
	</tr>
	<tr>
		<td valign="top"><code>getField(/*GlideRecord*/ gr, /*String*/ name)</code></td>
		<td valign="top">Returns the field's information</td>
	</tr>
	<tr>
		<td valign="top"><code>getFields(/*GlideRecord*/ gr, /*String*/ names)</code></td>
		<td valign="top">Checks the specified field names, and returns a comma seperated list of valid names.</td>
	</tr>
	<tr>
		<td valign="top"><code>getFieldsObject(/*GlideRecord*/ gr, /*String*/ names)</code></td>
		<td valign="top">Checks the specified field names, and returns an object containing the valid names.</td>
	</tr>
	<tr>
		<td valign="top"><code>logStat(/*String*/ type, /*String*/ table, /*String*/ id, /*Optional String*/ text)</code></td>
		<td valign="top">Adds a record to the Service Portal statistics log</td>
	</tr>
	<tr>
		<td valign="top"><code>logSearch(/*String*/ table, /*String*/ terms, /*int*/ count)</code></td>
		<td valign="top">Adds a record to the Service Portal statistics log, specifically for a search</td>
	</tr>
	<tr>
		<td valign="top"><code>canSeePage(/*String*/ pageID)</code></td>
		<td valign="top">Determines if the user is allowed to see the specified page</td>
	</tr>
	<tr>
		<td valign="top"><code>canReadRecord(/*GlideRecord*/ gr)</code></td>
		<td valign="top">Determines if the user can read the specified GlideRecord</td>
	</tr>
	<tr>
		<td valign="top"><code>canReadRecord(/*String*/ table, /*String*/ id)</code></td>
		<td valign="top">Determines if the user can read the specified GlideRecord</td>
	</tr>
	<tr>
		<td valign="top"><code>getCatalogItem(/*String*/ itemID)</code></td>
		<td valign="top">Returns the catalog item</td>
	</tr>
	<tr>
		<td valign="top"><code>getForm(/*String*/ table, /*String*/ sys_id, /*Optional String*/ encodedQuery, /*Optional String*/ view)</code></td>
		<td valign="top">Returns the form</td>
	</tr>
	<tr>
		<td valign="top"><code>getKBCategoryArticles(/*String*/ category, /*Optional int*/ limit)</code></td>
		<td valign="top">Returns KB articles in the specified category, includes all subcategories.</td>
	</tr>
	<tr>
		<td valign="top"><code>getKBSiblingCategories(/*String*/ categoryID)</code></td>
		<td valign="top">Returns KB categories with the same parent as the specified category.</td>
	</tr>
	<tr>
		<td valign="top"><code>getKBCount(/*String*/ knowledgeBaseID)</code></td>
		<td valign="top">Returns the number of KB articles</td>
	</tr>
	<tr>
		<td valign="top"><code>getSubCategories(/*String*/ categoryId)</code></td>
		<td valign="top">Returns the KB subcategories of the specified category</td>
	</tr>
	<tr>
		<td valign="top"><code>getKBTopCategoryID(/*String*/ catId)</code></td>
		<td valign="top">Returns the top category in the hierarch containing the specified category.</td>
	</tr>
	<tr>
		<td valign="top"><code>getKBRecord()</code></td>
		<td valign="top">Returns KB record for the portal's knowledge base with workflow_state = published in the query</td>
	</tr>
	<tr>
		<td valign="top"><code>getSCRecord()</code></td>
		<td valign="top">Returns the service catalog record for the portal's catalog with proper class name and active = true in the query</td>
	</tr>
	<tr>
		<td valign="top"><code>stripHTML(/*String*/ html)</code></td>
		<td valign="top">Removes non breaking spaces from the specified string</td>
	</tr>
	<tr>
		<td valign="top"><code>getMenuItems(/*String*/ sys_id)</code></td>
		<td valign="top">Returns the menu items for the specified instance</td>
	</tr>
	<tr>
		<td valign="top"><code>getMenuHREF(/*GlideRecord*/ gr)</code></td>
		<td valign="top">Builds the href (?id=) portion of the URL for the specifed page</td>
	</tr>
	<tr>
		<td valign="top"><code>log(/*Object*/ message)</code></td>
		<td valign="top">Sends the message to the console log</td>
	</tr>
</table>
