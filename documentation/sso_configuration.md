# SSO, Login & Redirect 

_Working since Helsinki Patch 2_

#### A few words on SSO
If you use SSO, Service Portal should just work like you would expect. If you are using the system property to automatically redirect to your primary IDP, then Service Portal will automatically redirect to that IDP. If you have multiple identity providers, Service Portal shows a link on the login page to "Use external login". You can conditionally redirect users to Service Portal after login by following the steps in this guide.

 * Require authentication for every Service Portal
 * Make Service Portal your default login page
 * Conditionally redirect to Service Portal after login

### Require authentication for every Service Portal

Some companies want their portal content available to only authenticated users. To do this, create a record in the sys_public table with the following values:

Page: $sp  
Active: false

Now when you go to [instance]/sp or [instance]/$sp.do you will be redirected to the platform configured login page if you're unauthenticated. This may be useful for companies with more complex SSO environments.

### Make Service Portal your login page

To make Service Portal the login page for your instance
set the system property glide.entry.page.script = "new SPEntryPage().getLoginURL()"

#### Configuring SPEntryPage

**Setting the portal**

SPEntryPage uses /sp/ as the portal path to redirect to. If you must, edit the SPEntryPage Script Include and change the assigned portal to any portal_suffix you want. (Once you make changes to this script include it won't be upgraded with future updates)

![Screenshot](/assets/sso/portal_suffix.png)


### Conditionally redirect to Service Portal after login

To conditionally redirect a user to Service Portal after login, set the system property glide.entry.first.page.script = "new SPEntryPage().getFirstPageURL()"

getFirstPageURL does 2 primary things:

  1. Redirects to login_redirect.do in order to break out of the frameset (if there is one).
  2. Redirects to Service Portal if the user has no roles, or the full platform for everyone else.

You can customize this behavior within the "SPEntryPage" script include. (Once you make changes to this script include it won't be upgraded with future updates)

### Debugging

To view debug output from SPEntryPage and see the session variables it redirects based on:

  1. Make sure the system property "glide.entry.first.page.script" has the value: new SPEntryPage().getFirstPageURL()

  2. Open the SPEntryPage script include and find and set "this.logVariables = true"

  3. In a different browser, log in.

  4. The log output can be viewed by going to "System Logs > System Log > All" in the navigator.

      Or by going directly to: /syslog_list.do?sysparm_query=level%3D0%5EORDERBYDESCsys_created_on&sysparm_first_row=1&sysparm_view=
