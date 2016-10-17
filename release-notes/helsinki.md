# Helsinki change log


## Helsinki Patch 6 Changes

* The Variable type checkbox value needs to be string "true"||"false" so glideform apis and ui policy conditions can work
* External content item should open in a new tab from SC category page
* g_form.setValue to empty is broken for reference fields in Service Portal
* evaluate order guide rule base condition from database, not client
* Formatter type variables like container_start would cause order guide eval fail

<br /><br /><br />

## Helsinki Patch 5 Changes
* Added a limit to typeahead search (defaults to 15)
* Several fixes for permissions and element access on search results page
* URL routing fix. When the path or portal changes, redirect to that new page
* KB article attachments moved to bottom for consistency w/ platform UI
* Clicking on links from the sc-category widget can now be intercepted and changed by a parent widget. Added the event name to the widget options schema.
* KB category article count might show -1, it shouldn't; $sp.getKBCount now only counts published articles
* Check_can_view widget option for SC Categories widget wasn't evaluated correctly after being set from true to false
* sp_admin role should be able to CRUD sp_ng_template records
* List widget did not honor glide.security.ui.filter system property or Dictionary attribute for table to force use of FilteredGlideRecord in lists
* Added spModal api for a nicer alert, confirm, prompt:
	* spModel.alert(title)
	* spModel.confirm(title)
	* spModel.prompt(title, defaultValue)
* **Form Widget**
	* In the activity stream, added a color bar to distinguish journal fields. Uses the accompanying system property (e.g., glide.ui.activity_stream.style.work_notes)
	* Support for journal stream for non-tasks
	* Pick the first choice in a choice list if none are selected
	* Don't expose short_description in ticket_conversation widget if user can't read that field
	* Don't show attachment icon or Edit link if user can't do attachments
	* Dont show 'record not found' once the form loads a record that DOES exist
	* Choice list now sets the value & displayValue
	* long, unbroken title is not wrapped in ticket conversation widget header
	* At mobile device width, the activity stream was unusable
	* Fixing some edge cases while using g_form.setValue() and the glide_list element. Like setting multiple display values at the same time.
	* Making the variable editor show display values for reference fields and list collector fields
	* Prevent duplicate --None-- in choice list
* **Catalog support**
	* Order Guide description isn't being shown
	* Fixing reference qualifiers for list collector variable types
	* Quantity picker wasn't wide enough
	* For SP catalog item requests, Attachments are now attached to the sc_req_item instead of the sc_request
	* Order Guide didn't show images for guide or included items
	* Adding support for catalog item variable and variable set layouts: 2down, 2across.
	

<br /><br /><br />

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
