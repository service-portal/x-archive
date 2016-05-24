## Widget Dependencies
In Service Portal, it is possible to link Javascript and CSS files to widgets. This allows developers to create dependencies between their widgets and third party libraries, external style sheets, and angular modules. Dependencies are only fetched from the server at the time that they are needed, which keeps initial page loads very fast. 

Following is a step-by-step guide on creating new dependency packages and associating them with widgets.

### Creating a Dependency Package
A dependency package is a collection of Javascript and CSS files that can be then connected to a widget. Dependencies can be found in the table `sp_dependency`, or by navigating to the Service Portal module in the navigator and selecting the Dependencies submodule.

In a dependency record, you will define the following: 

1. Name - The name that your dependency will be referred to by (Useful for selecting a dependency from a dropdown list)

2. Include on page load - Select if you want your dependency to be loaded onto the page on initial page load of Service Portal, or leave unchecked to load the dependency only when the linked widget is loaded onto a page.

3. Angular module name - Only necessary if the linked Javascript is an Angular module. Provide the name of the Angular module name that you are loading in, so that it can be injected into the Service Portal angular application. Leave blank if not applicable.

Once these fields are defined, you can start creating records in the `sp_js_include` and `sp_css_include` table and adding them to the JS Includes and CSS Includes related lists in a dependency record.
