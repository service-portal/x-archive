# Service Catalog Patch 2 Changes

There have been a number of improvements made to Service Portal's Service Catalog offering with Helsinki Patch 2, which are be enumerated and documented below.

1. Values that have been assigned to variables in order guides now "cascade" down to catalog items within the order guide.
2. Variable Attributes defined on a Catalog item variable are now respected by Service Portal's Reference Element field.
3. Labels for Service Catalog items that contain HTML now render the HTML inside the tag, instead of showing the HTML in plain text.

---

## Cascading Variables
In Helsinki Patch 2 and above, any variables defined within an Order Guide marked `Cascade Variables` will cascade their values down to variables within contained Catalog Items with the same name. Below is an example:

1. Create an order guide, make sure that the checkbox titled `Cascade Variables` is checked.
2. Create a variable within the order guide, give it the name `cascading_value`. The variable can be of any type.
3. Add a rule containing a Catalog Item with a variable in it of the name `cascading_value`.
4. Notice that when you populate the Order Guide variable with a value, that value will be carried to the equivalent variable to the individual ordered items.

## Variable Attributes
In a reference element field on a Service Catalog item, you can optionally define several Variable Attributes on the variable. This give a Service Catalog administrator control over what fields to display in the autocomplete dropdown for a reference element, what fields to search over, and what order to display them in. These variables are now supported in Service Portal, and their usage is documented in full at [the ServiceNow documentation site](http://wiki.servicenow.com/index.php?title=Auto-Complete_for_Reference_Fields#gsc.tab=0).

## HTML in Labels
In Helsinki Patch 2 and above, HTML written into a label field will be rendered as HTML in the label on a Service Catalog item. This means that tags such as `<b>` and `<br />` will be rendered as HTML.

So, for example, suppose you have a Service Catalog variable with it's Question field written as this:  

``` HTML
<span style="font-weight:normal"><br/>
  For remote employees:<br/>
  Please go to CDW to order <strong>headsets, USBs, etc.</strong><br/>
  <a target="_blank"  href="https://www.cdw.com">CDW Link</a>
  <br/>
</span>
```

That field will be rendered like this on the Service Catalog page:
![Service Catalog HTML in Label](/assets/service_catalog_patch2_changes/label-html.png)
