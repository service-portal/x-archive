# Debugging

## Client Side

| Command / Function | Description |
| :------ | :----------- |
| `console.log(String|Object)`   | Outputs to the browser console. When used in the Client Controller, this command is native to the browser. |
| `<pre>{{data|json}}</pre>` | Add this to the template. Uses Angular [json filter](https://docs.angularjs.org/api/ng/filter/json) to display content of `data` object in an easy-to-read fashion |
| `debugger;` | Native to Chrome and Firefox to set a browser breakpoint, letting an admin step through script line by line |


## Server Side


| Command / Function | Description |
| :------ | :----------- |
| `console.log(String|Object)` | Outputs to the browser console. When used in the Server Script, can log server-side JavaScript Objects and Strings |
| `$sp.log(String|Object)` | Outputs to a Service Portal page. Can log server-side JavaScript Objects and Strings. Similar to `gs.addInfoMessage(String)` but only outputs if user has `sp_admin` role or is impersonating. |
| `gs.log(String)` | Normal ServiceNow function to output text to the `syslog` database table. |
| `gs.warn(String)` | Normal ServiceNow function to output text to the `syslog` database table as a WARNING. |
| `gs.error(String)` | Normal ServiceNow function to output text to the `syslog` database table as an ERROR.|
| `gs.addInfoMessage(String)` | Normal ServiceNow function to output a message to the page in the browser, visible in the ServiceNow UI|
| `gs.addErrorMessage(String)` | Normal ServiceNow function to output an error to the page in the browser, visible in the ServiceNow UI|
