# spModal api
spModal provides an alternative way to show alerts, prompts, and confirmation dialogs. Additionally you can use spModal.open() to display a widget in a modal dialog.

## Examples

### Alert



```html
  <button ng-click="c.onAlert()" class="btn btn-default">
    Alert
  </button>
```

```javascript
  c.onAlert = function () {
		spModal.alert('How do you feel today?').then(function (answer) {
			c.simple = answer;
		});
	}
```
