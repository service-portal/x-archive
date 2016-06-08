# Record Watch
Record Watch is a tool that allows a widget developer to respond to table updates in real-time. For instance, by using Record Watch, the Simple List widget can listen for changes to its data table and if new records are added, removed, or updated, the widget can update itself in real-time.

Below is an example of how to use Record Watch in a widget's Client Script.

##### Client Script
```javascript
function(spUtil, $scope) {
  /* widget controller */
  var c = this;

  spUtil.recordWatch($scope, "incident", "active=true", function(name, data) {
    console.log(name); //Returns information about the event that has occurred
    console.log(data); //Returns the data inserted or updated on the table
  });
}
```

The above code is registering a listener on the incident table with the filter "active=true", meaning that whenever something changes on that table with that filter, our callback function will be executed.

The callback function takes two parameters:
* `name` - An object which contains information about the scope of the update.
* `data` - An object containing information about the operation that has taken place ('insert', 'update', or 'delete'), as well as the data for the record itself and, if applicable, a list of the changes that have occurred on that record.

### Usage Notes
* When passing the `$scope` argument into the `spUtil.recordWatch` function, be sure to inject `$scope` into the parameters of your Client Script function. For details, see the code snippet above.
* For a real example of using Record Watch, see the **Simple List Widget**.
* Tables that are (periodically) subject to a high frequency of database events are blacklisted from Record Watcher to prevent event storms. 
