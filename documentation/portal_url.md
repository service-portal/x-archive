
## Portal URL
Navigation is possible to a page or portal, this explains the URL schema.

##Navigating by Portal
Navigating by portal displays the portal including the header, footer, and theme defined by the [Portal](portal.md)

  `https://<base instance URL>/<sp url suffix>?id=<page id>&<page parameters>`

Elements:
  - **Base Instance URL:** unique, secure Web address for each instance. The default format is: `https://<instancename>.service-now.com.`
  - **sp url suffix:** Suffix established for the Service [Portal](portal.md)
  - **id:** The id of the [Page](page.md) to navigate to within the portal frame
  - **page parameters:** Some pages require additional parameters to lookup a record (table, sys_id)
  
##Navigating by Page
  `https://<base instance URL>/$sp.do?id=<page id>&<page parameters>`

Elements:
  - **Base Instance URL:** unique, secure Web address for each instance. The default format is: `https://<instancename>.service-now.com.`
  - **id:** The id of the [Page](page.md) to navigate to within the portal frame
  - **page parameters:** Some pages require additional parameters to lookup a record (table, sys_id)
  
