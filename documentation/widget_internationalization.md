# Internationalization
Internationalizing strings in a widget is very simple with Service Portal. In any widget's HTML Template, simply write the following:

##### HTML Template
```html
<div>
  <p>${This message will be internationalized.}</p>
  <p>However, this will NOT be.</p>
</div>
```

Writing text as ``${message}`` is the equivalent of writing ``${gs.getMessage("message")}`` in other parts of the system, but written as a more legible shorthand.

Text can be internationalized the same way inside a client script.

##### Client Script
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
