# Internationalization

To internationalize strings in a widget, use `${string}` or `gs.getMessage("message")`. See when to use one form or another below:

[Translating strings in the HTML template](#translating-strings-in-the-html-template)

[Translating strings in the Client Script](#translating-strings-in-the-client-script)

[Translating strings in the Server Script](#translating-strings-in-the-server-script)

[Safe translations](#safe-translations)

[Language Switch Widget](#language-switch-widget)


### Translating strings in the HTML template
#### HTML Template
```html
<div>
  <p>${This message will be internationalized.}</p>
  <p>However, this will NOT be.</p>
</div>
```
Writing text as ``${message}`` is the equivalent of writing ``${gs.getMessage("message")}`` in other parts of the system, but written as a more legible shorthand.

<br/>

### Translating strings in the Client Script
#### Client Script
Text can be internationalized the same way inside a client script.
```javascript
function() {
  var c = this;
  c.message = "${This message will be internationalized}";
}
```
#### HTML Template
```html
<div>
  <!-- The output of this text will be internationalized. -->
  <p>{{c.message}}</p>
</div>
```

<br/>

### Translating strings in the Server Script

Great for translating schema options and other values fetch during server-side runtime. 

#### Server Script
```javascript
function() {  
  data.message = gs.getMessage("this message contains 'quotes'");
}
```

##### HTML Template
```html
<div>  
  <p>{{c.data.message}}</p>
</div>
```

<br/>

### Safe translations
In some cases, the translation might have quotes or double quotes on it. That could lead to JavasScript errors if you are using the ${} syntax in the client script.  
The safest way to fetch a translated message is to do it in the server script. 
Then, assign the value to a client-side angular binding.

<br/>

### Language Switch Widget

Users might want to change the language on the portal. The following Widget can be used as template to implement a customized language switch:

##### HTML Template:
```html
<div>
  ${Change Language}:
  <sn-record-picker 
  table="'sys_language'" 
  display-field="'name'" 
  value-field="'id'" 
  field="c.language" 
  default-query="'active=true'"></sn-record-picker> 
  <button class="btn btn-default" ng-click="c.changed()">Apply</button> 
</div>
```

##### Client Script:
```javascript
function($window) {  
  var c = this;		
	c.language = {value: 'en', displayValue: 'English'};		
	c.changed = function(a) {							
		c.server.get(c.language).then(function() {			
			$window.location.reload();			
		})		
	}	
}
```

##### Server Script:
```javascript
(function() {			
 if (input) {	 	 
	 var user = gs.getUser();	 	 	 
	 user.setPreference("user.language", input.value);
	 user.savePreferences();	 
 }
})();
```
