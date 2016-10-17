# Helsinki change log

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
