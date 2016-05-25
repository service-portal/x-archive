# Debugging

| Property | Where Used | Description |
| :------ | :----------- | :------------ |
| `console.log(String|Object)`   | Server Script, Client Controller | Ouputs into the Browser console, server-side JavaScript objects and strings that can be displayed. When used in the Client Controller, this command is not ServiceNow specific and is managed by each individual browser (may not work in all browsers: http://stackoverflow.com/questions/14086675/which-browsers-support-console-log). |
| `$sp.log(String|Object)` | Server Script | Outputs into the Java console, server-side JavaScript objects and strings that can be displayed |
| `debugger` | Client Controller | (not ServiceNow-specific) Available in Chrome and Firefox to set a browser breakpoint, letting an admin step through script line by line |
| `gs.print(String)` | Server Script | Standard ServiceNow function to output text to the Java console. |
| `gs.log(String)` | Server Script | Standard ServiceNow function to output text to both the Java console and the `syslog` database table. |
| `gs.warn(String)` | Server Script | Standard ServiceNow function to output text to both the Java console and the `syslog` database table as a WARNING. |
| `gs.error(String)` | Server Script | Standard ServiceNow function to output text to both the Java console and the `syslog` database table as an ERROR. |
| `gs.addInfoMessage(String)` | Server Script | Standard ServiceNow function to output a message to the page in the browser, visible in the ServiceNow UI |
| `gs.addErrorMessage(String)` | Server Script | Standard ServiceNow function to output an error to the page in the browser, visible in the ServiceNow UI |
