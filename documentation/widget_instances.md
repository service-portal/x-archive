## Configuring Widgets with Instances
In Service Portal, widgets are modular, configurable blocks of functionality and UI that are designed to be reusable.

Whenever you embed a widget onto a page, you are automatically creating an `sp_instance` record which contains three important things.

1. Reference to a column (where a widget is located)
2. Reference to a widget
3. Configuration for a widget in the form of pre-defined form fields and an Additional Options field in JSON format

There are a number of ways that you can configure a widget, so we'll go through an example to get started with the basics.

For information on working with instance options, read [Widget Options](widget_options.md) after you're done with this section.

### Configuring a Simple List Widget
Let's try configuring a Simple List widget to show a list of problems from the `problem` table, and we will make each list entry link to a Form page. Start by embedding the Simple List widget onto the index page, then navigate to that page URL either through a portal or by navigating to /$sp.do?id=index

Now, let's start configuring the widget. Hold the CTRL button and right-click the widget from the page. If you are logged in as a SP Admin, you should see a context menu appear with a list of links, one of which should say **Instance Options**. Click that link, and you will see a modal appear on the screen containing all of the configuration options that the Simple List widget exposes to you.

Now, from this modal, we will fill in the following fields:

* Table - **Problem**
* Display field - **Short description**
* Link to this page - **form**
* Secondary fields - **number**, **sys_updated_on**

Hit **Save**, and the page will refresh with your newly-configured widget. Click on one of the List entries, and notice that you will be taken to a Form page for that record.
