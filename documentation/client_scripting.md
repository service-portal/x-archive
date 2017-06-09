
# Service Portal & Client Scripts

Service Portal runs client scripts & catalog client scripts as long as the UI Type is set to "Mobile" or "Both". Many of your existing client scripts can be set to "Both" as long as the api calls are supported by the mobile client scripting environment.

Please note: This document applies to the Form widget and SC Catalog Item widget. Client Scripts are different than a widget's client controller & link script blocks.

#### Unsupported client scripting globals

The following globals and APIs are unavailable in service portal client script:

* window
* document
* $
* jQuery
* $$
* $j
* angular

#### Client scripting in widgets

Widget client controllers are full angular controllers and are not subject to the restrictions listed above. Feel free to use jQuery and Angular as needed.

#### Embedded widgets & g_form

When using the Service Catalog variable type "Macro" and "Macro with Label" you can pick a widget to embed in a catalog item form. Within that embedded widget's client controller you can access the field object and catalog item g_form instance using:

* $scope.page.field
* $scope.page.g_form()

#### Checking desktop vs mobile runtime

You might want to mark a client script compatible with both Desktop and Mobile but still do something different depending on the runtime use this:

```javascript
  if (window === null)
    // Write your mobile compatible code here
  else
    // Write your desktop compatible code here
```

## Supported client scripting APIs

These are the officially supported client scripting APIs you can use in onLoad, onChange, and onSubmit client scripts.

### g_form

* addDecoration(fieldName, icon, title)
* addErrorMessage(message)
* addInfoMessage(message)
* addOption(fieldName, value, label, index)
* clearMessages()
* clearOptions(fieldName)
* clearValue(fieldName)
* getActionName()
* getBooleanValue(fieldName)
* getDecimalValue(fieldName)
* getDisplayValue(fieldName)
* getEncodedRecord()
* getFieldNames()
* getIntValue(fieldName)
* getLabel(fieldName)
* getReference(fieldName, callback)
* getRelatedListNames()
* getSectionNames()
* getSysId()
* getTableName()
* getValue(fieldName)
* hasField(fieldName)
* hideAllFieldMsgs(type: "info |  error")
* hideErrorBox(fieldName)
* hideFieldMsg(fieldName, clearAll)
* hideRelatedList(listTableName)
* hideRelatedLists()
* isMandatory(fieldName)
* isNewRecord()
* isReadOnly(fieldName)
* isVisible(fieldName)
* removeDecoration(fieldName, icon, title)
* removeOption(fieldName, value)
* save()
* serialize(onlyDirtyFields)
* setFieldPlaceholder(fieldName, placeholder)
* setLabel(fieldName, label)
* setMandatory(fieldName, isMandatory)
* setReadOnly(fieldName, isReadOnly)
* setSectionDisplay(sectionName, isVisible)
* setValue(fieldName, value, displayValue)
* setVisible(fieldName, isVisible)
* showErrorBox(fieldName, message, scrollForm)
* showFieldMsg(fieldName, message, type: "info | error", scrollForm)
* showRelatedList(relatedTableName)
* showRelatedLists()
* submit(submitActionName)

### g_list
* [get(fieldName)](#g_list)
  * addItem(value, displayValue)
  * removeItem(value)
  * reset()
  * setQuery(queryString)
  * setDefaultOperator(operator)
  * getDefaultOperator()


### g_service_catalog
* [isOrderGuide()](#g_service_catalog)

### GlideAjax

* new GlideAjax(scriptIncludeName)
  * addParam (name, value)
  * getParam (name)
  * getXML(callback)
  * getXMLAnswer(callback)
  * getJSON(callback)
  * setErrorCallback(errorCallback)
  * getURL()
  * getParams()
  * execute()
  * successCalback(data, status, xhr)
  * errorCallback(xhr)
  * setScope(scope)


### GlideRecord
* new GlideRecord(tableName)
  * addQuery(encodedQuery)
  * addQuery(fieldName, operator, value)
  * getEncodedQuery()
  * deleteRecord(callback)
  * get(id)
  * getTableName()
  * hasNext()
  * insert(callback)
  * gotoTop()
  * next()
  * loadRow(rowObj)
  * getValue(fieldName)
  * setValue(fieldName, value)
  * isDotWalkField(fieldName)
  * addOrderBy(fieldName)
  * orderBy(fieldName)
  * orderByDesc(fieldName)
  * setDisplayFields(fieldNames)
  * query(callback)
  * setRows(rowsArray)
  * setTableName(tableName)
  * update(callback)
  * setLimit(maxInt)
  * getLimit()


### getMessage(messageKey, callback)


# Usage examples

<a name="g_list"></a>g_list
-----
g_list helps you set the filter of a glide list element or a list collector variable. Use this api in place of the "g_filter" api on desktop client scripts.

```javascript
function onLoad() {
  var myListCollector = g_list.get("my_list_collector");
  myListCollector.reset();
  myListCollector.setQuery("active=true^category=8c7b22230b402200b0b02c6317673a62");
  myListCollector.addItem('3a700d39af5f4fc0aab978df90f4c692', 'Power Supply');
  myListCollector.addItem('1cb93419a3a248318da8f814140b42f6', 'Backpack');
}
```

<a name="g_service_catalog"></a>g_service_catalog
-----
g_service_catalog is only available in Service Portal service catalog item scripts. Use this API to know if your catalog item script is being run as part of an order guide or on its own.

 ```javascript
 function onLoad() {
   if (window) // if CMS don't run this
    return;

    // g_service_catalog api for Service Portal and Mobile
    var isOrderGuide = g_service_catalog.isOrderGuide();
    g_form.setValue("is_order_guide", isOrderGuide ? "Yes!" : "Nope :(");
}
 ```
