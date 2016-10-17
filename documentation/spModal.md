# spModal api
spModal provides an alternative way to show alerts, prompts, and confirmation dialogs. Additionally you can use spModal.open() to display a widget in a modal dialog. spModal is a lightweight wrapper for angular UI bootstrap's $uibModal. See here for more info: https://angular-ui.github.io/bootstrap/#/modal

| Method | Description |
| :------ | :----------- |
| [alert](#alert)(message).then(fn) | Alert a message. The promise contains a single argument that returns true/false. |
| [confirm](#confirm)(message).then(fn) | Display a confirmation message. The promise contains a boolean of the user's response.  |
| [prompt](#prompt)(message, *defaultValue*).then(fn) | Prompt the user for input. Provide a message and an optional default value for the input field. The promise contains the user's response as a string. |
| [open](#open)(object options).then(fn) | Open a modal with a customized set of options. See the options table below. |

**Options** object definition

| Option | type | Default | Description |
| :------ | :------ | :------ | :----------- |
| title | string | empty | goes in header - can be HTML | 
| message | string | empty | goes in the body - can be HTML |
| buttons | array | Cancel & OK | buttons to show on the dialog |
| input | bool | false | if true, shows an input field on the dialog |
| value | string | empty | The value of the input field |
| widget | string | empty | The Widget Id or sys_id to embed in the modal |
| widgetInput | object | null | An object to send to the embedded widget as input |
| size | string | empty | 'sm' or 'lg' |

## Examples

Alert
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

Confirm
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


<br /> <br />

Prompt
------

![spModal prompt dialog](/assets/spmodal/prompt.png)

**Html Template**
```html
  <button ng-click="c.onPrompt()" class="btn btn-default">
    Prompt
  </button>
  <div ng-show="c.name">
    You answered <span>{{c.name}}</span>
  </div>
```

**Client Script**
```javascript
function(spModal) {
  var c = this;
  c.onPrompt = function() {
		spModal.prompt("Your name please", c.name).then(function(name) {
			c.name = name;
		})
	}
}
```


<br /> <br />

Prompt (with label)
------

![spModal prompt with custom label](/assets/spmodal/prompt_with_label.png)

**Html Template**
```html
  <button ng-click="c.onPromptEx()" class="btn btn-default">
    Prompt with label
  </button>
  <div ng-show="c.name">
    You answered <span>{{c.name}}</span>
  </div>
```

**Client Script**
```javascript
function(spModal) {
  var c = this;
  c.onPromptEx = function() {
		//ask the user for a string
		spModal.open({
			title: 'Give me a name',
			message: 'What would you like to name it?',
			input: true,
			value: c.name
		}).then(function(name) {
			c.name = name;
		})
	}
}
```


<br /> <br />

Heading
------

![alt](/assets/spmodal/img.png)

**Html Template**
```html
  
```

**Client Script**
```javascript
function(spModal) {
  var c = this;
  
}
```


<br /> <br />

Heading
------

![alt](/assets/spmodal/img.png)

**Html Template**
```html
  
```

**Client Script**
```javascript
function(spModal) {
  var c = this;
  
}
```
