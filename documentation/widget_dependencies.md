## Widget Dependencies
In Service Portal, it is possible to link Javascript and CSS files to widgets. This allows developers to create dependencies between their widgets and third party libraries, external style sheets, and angular modules. Dependencies are loaded asynchronous from the server at the time that they are needed.

Following is a step-by-step guide on creating new dependency packages and associating them with widgets.

### Creating a Dependency Package
A dependency package is a collection of Javascript and CSS files that can be then connected to a widget. Dependencies can be found in the table `sp_dependency`, or by navigating to the Service Portal module in the navigator and selecting the Dependencies submodule.

In a dependency record, you will define the following: 

1. Name - The name that your dependency will be referred to by (Useful for selecting a dependency from a dropdown list)

2. Include on page load - Select if you want your dependency to be loaded onto the page on initial page load of Service Portal, or leave unchecked to load the dependency only when the linked widget is loaded onto a page.

3. Angular module name - Only necessary if the linked Javascript is an Angular module. Provide the name of the Angular module name that you are loading in, so that it can be injected into the Service Portal angular application. Leave blank if not applicable.

Once these fields are defined, you can start creating records in the `sp_js_include` and `sp_css_include` table and adding them to the JS Includes and CSS Includes related lists in a dependency record.

### Adding Files to a Dependency Package
Here, we will quickly go over how to add files to a dependency package. Individual JS and CSS files can be found in the tables `sp_js_include` and `sp_css_include`, respectively.

In a include record, you will define the following:

1. Display Name - The name of the include (Useful for selecting includes from a dropdown list).

2. Source - Your options here are going to depend on whether you are making a new JS include or a CSS include.

 Both JS and CSS includes have URL as an option, which is a way to provide a simple URL path to the file you want to include. ex. 	https://code.highcharts.com/highcharts.js
 
 The second option will depend on the file type. JS includes allow you to reference a UI Script record. CSS includes allow you to reference a SP CSS record, found in the table `sp_css`.

Once you have created your include records, you can add them to your dependency package. Navigate back to your dependency record that you created earlier, and open up the related lists. In both the JS Includes and the CSS Includes related lists, you will do the following:

1. Select the tab for the related list
2. Click the Edit button
3. Using the slushbucket that has appeared on your screen, move any includes you with to add to your dependency package into the column on the right hand side of the screen. 
4. Press Save
5. From the Related List on the Dependency record, update the Order field on each included file to specify what order the files should be loaded into the page. Files with lower Order values are loaded first. This is important if your fields depend on one another to be on the page to load correctly.

### Adding a Dependency Package to a Widget
Finally, we can create a relationship between our new Dependency and a widget. To do this, follow these steps:

1. Navigate to the widget record you wish to update
2. Scroll to the bottom of the record, and open the Dependencies related list
3. Select the Edit button on the list
4. Find the dependency you want to add to the widget in the left column of the slushbucket, and move it to the right column.
5. Press Save

That's it! Remember - a widget can have as many or as few dependencies as you want it to have, but the more you add, the more content your widget will need to download to render on the page. Keep the dependencies as small as possible for fast load times.
