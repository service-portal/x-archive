# spModal api
_Available in Helsinki Patch 5_

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
| shared | object | null | A client-side object to share data with the embedded widget client script |
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

Open
------

### Example 1: Prompt with label

![spModal prompt with message](/assets/spmodal/prompt_with_label.png)

**Html Template**
```html
  <button ng-click="c.onOpen()" class="btn btn-default">
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
  c.onOpen = function() {
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

### Example 2: Agree with custom buttons

![spModal agree dialog](/assets/spmodal/open_with_promise.png)

**Html Template**
```html
  <button ng-click="c.onAgree()" class="btn btn-default">
    Agree
  </button>
  <div ng-show="c.agree">
    You answered {{c.agree}}
  </div>
```

**Client Script**
```javascript
function(spModal) {
  var c = this;
  c.onAgree = function() {
		// ask the user for a string
		// note embedded html in message
		var h = '<h4>Apple likes people to agree to lots of stuff</h4>'
		var m = 'Your use of Apple software or hardware products is based on the software license and other terms and conditions in effect for the product at the time of purchase. Your agreement to these terms is required to install or use the product. '
		spModal.open({
			title: 'Do you agree?',
			message: h + m,
			buttons: [
				{label:'✘ ${No}', cancel: true},
				{label:'✔ ${Yes}', primary: true}
			]
		}).then(function() {
			c.agree = 'yes';
		}, function() {
			c.agree = 'no';
		})
	}
}
```


<br /> <br />

### Example 3: Embedded widget 

![spModal embedded widget](/assets/spmodal/embedded_widget.png)

**Html Template**
```html
  <button ng-click="c.onWidget('widget-cool-clock')" class="btn btn-default">
    Cool Clock
  </button>
```

**Client Script**
```javascript
function(spModal) {
  var c = this;
  c.onWidget = function(widgetId, widgetInput) {
		spModal.open({
			title: 'Displaying widget ' + widgetId,
			widget: widgetId, 
			widgetInput: widgetInput || {}
		}).then(function(){
			console.log('widget dismissed');
		})		
	}
}
```

<br /> <br />

### Example 4: Modal sizes 

![spModal size small](/assets/spmodal/size_sm.png)
![spModal size medium](/assets/spmodal/size_md.png)
![spModal size large](/assets/spmodal/size_lg.png)

**Html Template**
```html
  <button ng-click="c.onSize('sm')" class="btn btn-default">
    Small
  </button>
  <button ng-click="c.onSize()" class="btn btn-default">
    Default
  </button>
  <button ng-click="c.onSize('lg')" class="btn btn-default">
    Large
  </button>
```

**Client Script**
```javascript
function(spModal) {
  var c = this;
  c.onSize = function(size) {
		spModal.open({
			title: 'Bootstrap modal sizes, sm, lg',
			size: size,
			message: 'Size set to ' + size
		})
	}
}
```


<br /> <br />

### Example 5: Embedded widget with shared data

![open_shared_data](/assets/spmodal/open_shared_data.gif)

This example requires 2 widgets.

#### Parent Widget

**Html Template**
```html
<div>
  <button ng-click="c.onChangeSchedule()">
    Open
  </button>
  
  <div ng-if="c.selectedValue">
    You picked: {{c.selectedValue.text}}
  </div>
</div>
```

**Client Script**
```javascript
function ($scope,spModal) {	
	var c = this;
	var shared = {};
	c.onChangeSchedule = function(){
		spModal.open({
			title: 'Select a value',
			widget: 'bec1438bdbf276009ed8f81d0f96193e',
			widgetInput: { hint: "Soup or Nuts?" },
			shared: shared
		}).then(function() {
			// Shared object was updated
			c.selectedValue = shared.selection;
		});
	}
}
```

#### Embedded Widget

Name: **bec1438bdbf276009ed8f81d0f96193e**

**Html Template**
```html
<div>
	<select ng-model="c.selection" ng-model-options="{getterSetter: true}" ng-options="v.text for (k, v) in data.questions">
  <option value="">{{::c.data.hint}}</option>
  </select>
</div>
```

**Client Script**
```javascript
function() {
  var c = this;
	
	var shared = c.widget.options.shared;
	c.selection = function selection(newVal) {
		return angular.isDefined(newVal) ? (shared.selection = newVal) : shared.selection;
	}
}
```

**Server Script**
```javascript
(function() {
	data.hint = input.hint;
	data.questions=[];
	data.questions.push({text: 'Soup', value: 'soup'});
	data.questions.push({text: 'Nuts', value: 'nuts'});
})();
```
