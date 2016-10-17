# spModal api
spModal provides an alternative way to show alerts, prompts, and confirmation dialogs. Additionally you can use spModal.open() to display a widget in a modal dialog.

| Method | Description |
| :------ | :----------- |
| [alert](#alert)(message).then(fn) | Alert a message. The promise contains a single argument that returns true/false. |
| [confirm](#confirm)(message).then(fn) | Display a confirmation message. The promise contains a boolean of the user's response.  |
| [prompt](#prompt)(message, *defaultValue*).then(fn) | Prompt the user for input. Provide a message and an optional default value for the input field. The promise contains the user's response as a string. |



## Examples

<a name="alert"></a> Alert
------

![alert modal](/assets/spmodal/alert.png)

**Html Template**
```html
  <button ng-click="c.onAlert()" class="btn btn-default">
    Alert
  </button>
```

**Client Script**
```javascript
function(spModal) {
	var c = this;
  c.onAlert = function () {
		spModal.alert('How do you feel today?').then(function (answer) {
			c.simple = answer;
		});
	}
 }
```
<br /> <br />

<a name="confirm"></a> Confirm
------

![confirm modal](/assets/spmodal/confirm.png)

**Html Template**
```html
  <button ng-click="c.onConfirm()" class="btn btn-default">
    Confirm
  </button>
  <span>{{c.confirmed}}</span>
```

**Client Script**
```javascript
function(spModal) {
  var c = this;
  c.onConfirm = function() {
		c.confirmed = "asking";
		spModal.confirm("Can you confirm or deny this?").then(function(confirmed) {
			c.confirmed = confirmed; // true or false
		})
	}
 }
```
<br /> <br />

Confirm with HTML message
------

![confirm modal with html message](/assets/spmodal/confirm_html_message.png)

**Html Template**
```html
  <button ng-click="c.onConfirmEx()" class="btn btn-default">
    Confirm - HTML message
  </button>
  <span>{{c.confirmed}}</span>
```

**Client Script**
```javascript
function(spModal) {
  var c = this;
  // more control, passing options
	c.onConfirmEx = function() {
		c.confirmed = "asking";
		var warn = '<i class="fa fa-warning" aria-hidden="true"></i>';
		spModal.open({
			title: 'Delete this Thing?',
			message: warn + ' Are you <b>sure</b> you want to do that?'
		}).then(function(confirmed) {
			c.confirmed = confirmed;
		})
	}
}
```
