# SSO, Login & Redirect

#### A few words on SSO
If you use SSO, Service Portal should just work like you would expect. If you are using the system property to automatically redirect to your primary IDP, then Service Portal will automatically redirect to that IDP. If you have multiple identity providers, Service Portal shows a link on the login page to "Use external login". You can conditionally redirect users to Service Portal after login by following the steps in this guide.

Follow this guide to configure one of the following scenarios:

 * Make Service Portal your default login page
 * Conditionally redirect to Service Portal after login


### Make Service Portal your login page

To make Service Portal the login page for your instance
set the system property glide.entry.page.script = "new SPEntryPage().getLoginURL()"

#### Configuring SPEntryPage

**Setting the portal**

Out of the box, SPEntryPage uses /sp/ as the portal path to redirect to. Edit the SPEntryPage Script Include and change the assigned portal to any portal_suffix you want.

![Screenshot](/assets/sso/portal_suffix.png)


**Changing the redirect behavior**

After a user authenticates SPEntryPage.getFirstPageURL() is called. Out of the box, this function does 2 primary things:

  1. Redirects to login_redirect.do in order to break out of the frameset (if there is one).
  2. Redirects to Service Portal if the user has no roles, or the full platform for everyone else.
