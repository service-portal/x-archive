# Internationalization
Internationalizing strings in a widget is very simple with Service Portal. In any widget's HTML Template, simply write the following:

#### HTML Template
```html
<div>
  <p>${This message will be internationalized.}</p>
  <p>However, this will NOT be.</p>
</div>
```

<br/>

Writing text as ``${message}`` is the equivalent of writing ``${gs.getMessage("message")}`` in other parts of the system, but written as a more legible shorthand.

Text can be internationalized the same way inside a client script.

#### Client Script
```javascript
function() {
  var c = this;
  c.message = "${This message will be internationalized}";
}
```

##### HTML Template
```html
<div>
  <!-- The output of this text will be internationalized. -->
  <p>{{c.message}}</p>
</div>
```

<br/>

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

#### Translations with quotes
In some cases, the translation might have quotes or double quotes on it. That could lead to JavasScript errors if you are using the ${} syntax in the client script.  
The safest way to fetch a translated message is to do it in the server script. 
Then, assign the value to a client-side angular binding.
