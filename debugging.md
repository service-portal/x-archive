# Debugging

Client Side

| Command / Function | Where Used | Description |
| :------ | :----------- | :------------ |
| `console.log(String|Object)`   | Outputs to the browser console. When used in the Server Script, can log server-side JavaScript Objects and Strings. When used in the Client Controller, this command is native to the browser. |
| `<pre>{{data|json}}</pre>` | Uses AngularJS `json` filter to display content of `data` object in an easy-to-read fashion (https://docs.angularjs.org/api/ng/filter/json)|
| `debugger;` | Native to Chrome and Firefox to set a browser breakpoint, letting an admin step through script line by line |


Server Side


| Command / Function | Where Used | Description |
| :------ | :----------- | :------------ |
| `console.log(String|Object)`   | Outputs to the browser console. When used in the Server Script, can log server-side JavaScript Objects and Strings. When used in the Client Controller, this command is native to the browser. |
| `$sp.log(String|Object)` | Outputs to a Service Portal page. Can log server-side JavaScript Objects and Strings. Similar to `gs.addInfoMessage(String)` but only outputs if user has `sp_admin` role or is impersonating. |
| `gs.print(String)` | Normal ServiceNow function to output text to the Java console. |
| `gs.log(String)` | Normal ServiceNow function to output text to both the Java console and the `syslog` database table. |
| `gs.warn(String)` | Normal ServiceNow function to output text to both the Java console and the `syslog` database table as a WARNING. | `gs.error(String)` | Normal ServiceNow function to output text to both the Java console and the `syslog` database table as an ERROR. |
| `gs.addInfoMessage(String)` | Normal ServiceNow function to output a message to the page in the browser, visible in the ServiceNow UI |
| `gs.addErrorMessage(String)` | Normal ServiceNow function to output an error to the page in the browser, visible in the ServiceNow UI |
| `debugger` | Native to Chrome and Firefox to set a browser breakpoint, letting an admin step through script line by line |
