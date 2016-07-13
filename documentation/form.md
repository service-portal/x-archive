# Form Widget
Out of the box, Service Portal ships with an implementation of the ServiceNow Form, entirely contained within a widget. The Form widget works in much the same way as the forms you are probably already familiar with in the ServiceNow platform.

However, there are a few caveats, which will be described in depth below.

___

## Form Scripts
Here, we will go over different types of form scripts and what is supported in Service Portal.

### Client Scripts
Service Portal has support for Client Scripts that are marked with a UI Type of either **Mobile** or **Both**. Client Scripts marked Desktop will not be executed, as those scripts rely on legacy APIs that are not supported by Service Portal.

### UI Actions
All **Server-side UI Actions** are supported, with one important distinction - setRedirectURL() operations are ignored, due to the fact that Service Portal forms do not handle redirection the same way that forms in the platform do.

Any UI Actions marked Client are **not compatible with Service Portal** and will be ignored by the Form widget.

### UI Macros
UI Macros are **not supported** in Service Portal (they use Jelly, and Service Portal doesn't).

### UI Policies
UI Policies are supported in Service Portal forms.

### Formatters
Formatters are **not supported** in Service Portal (they use Jelly, and Service Portal doesn't).

