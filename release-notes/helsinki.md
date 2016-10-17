# Helsinki change log

## Helsinki Patch 4 Changes

* Every out-of-box widget translated
* Service Portal Designer translated
* spPanel directive failed if title attribute had a single quote
* Fixing JS error on toolip close
* Fix to make sure a utc date is passed into the <sn-day-ago /> directive. Otherwise a dd/mm/yy date format will throw it off
* Keyboard shortcuts do not work on Service portal designer
* In the widget editor, if you open a widget that has dependencies a JavaScript error might appear in the console
* SQANDA - Subscribed Questions. Header color can't be set from instance options
* Fixing bug with glyphicon element in platform ui because value changes weren't saved
* De-duplicate page load dependencies
	* Added "Include on page load" to dependency
	* If checked, shows optional glide_list of portals; if none selected, dependency loads for all
	* applies to angular dependencies too
* Couldn't remove Glyph in widget instance options
* spGlyphPicker directive wrongly removed first three characters even if value didn't start with "fa-"
* Adding sc_cat_item_content items to search results and doing all of the special handling
* Oracle needs larger sp_widget script fields or OOB scripts get truncated
* Uploading a logo in the branding editor doesn't change the logo in the portal
* **Catalog support**
	* Prevent duplicate labels showing up in a choice list
	* variables max_length inconsistent with normal Catalog UI. single line text should allow more than 40 characters, and field-mapped vars should honor target field max_length
	* variables use maxlength="-1" but that's not supported by IE
	* Changing the sp_ref_list_data processor so that it uses the VariableModel to get Variable Choice List items, and adding pricing support to the reference variable type
	* Variable read_roles not being honored
	* ref_ac_columns attribute for reference variables ignored fields not in the "mobile" list view
	* Record Producers are not mapping variables to fields unless "Map to field" is selected, should also map if variable name matches a target field
	* Added option to sc_cat_item widget to allow redirecting after ordering a catalog item
		* auto_redirect (bool)
		* url (string)
	* Adding the variable editor formatter/widget
	* The Service Catalog category list widget now has the ability to show a hierarchical view of categories. Great for usability, great for performance
	* Configuring the SC Category widget to default to Nested if layout is not specified
	* Render description as HTML in sc_cat_item widget
* **Form Widget** 
	* Related list links should inherit view param
	* Now you can add an attachment to a new record
	* Reference icon on service portal was enabled regardless of readOnly status of the reference field - should honor system property and dictionary attribute
	* ref_ac_columns doesn't work for reference fields in Form widget
	* Adding ui formatters to form model
		* Adding variable editor as an oob sp_ui_formatter
	* Making g_form available to formatter widgets as $scope.page.g_form
	* Choice list will now clear the old value if it isn't in the list of choices.
	* Allow scoped apps to use/clone the form widget. Fix to get the client scripts and ui policy in a scoped app.
	* Adding placeholder attribute to text fields.
* **Service Portal Designer**
	* Now rendering page specific CSS




<br /><br /><br />

## Helsinki Patch 3 Changes

* Dozens of translations added
* Don't base64 encode record values when saving a form
* Removed spnavto processor
* Honor glide.sc.price.display when set to "never" (search results)
* My Requests widget should show same query as Requests in header
* Services Status page shows wrong/missing dates with custom date format
* link-button widget didn't let you set color in Widget Options
* Setting glide.spform.log_sql to false by default
* CSS class names were not being set on nested rows
* Typeahead search wrongly shows no_search=true and visible_standalone=false catalog items
* /sp portal homepage has no search input in mobile (xs) view
* data table widget might fail to show column label
* New portal should have out of the box Bootstrap colors and settings
* g_user_date_time_format and other globals were not available
* **Catalog support**
	* Bringing variable type "label" into the form field model so you can show/hide it using g_form.setDisplay() or ui policy actions
	* Don't show price/submit/attachments footer for Content Item catalog item, it's HTML only
	* Conversation stream didn't show image attachments added before insert (e.g., from the Create a New Incident catalog item)
	* If a catalog item has no short description it wouldn't show up on an order guide
	* Catalog variable Help Text isn't shown when specified
	* Catalog variable tooltip isn't shown
	* Fix for cascading variables. Reference field display values were using the wrong model property
	* Cleaning up the mandatory field processing in order guides
	* Update Price/Recurring when checkbox variable is unchecked
	* Firing submitted events from "SC Order Guide" and "SC Cat Item"
		* $sp.sc_order_guide.submitted
		* $sp.sc_cat_item.submitted	
* **Service Portal Designer**
	* Fix: When you drag and drop a widget to another location it will copy the widget instead of moving it
* Fix: Widget code is running twice
