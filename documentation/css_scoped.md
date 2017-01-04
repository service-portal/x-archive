# Scoped Page/Widget CSS

CSS Variable inclusion order: 
  1. sp_theme.css_variables 
  2. sp_portal.css_variables 
  3. sp_page.css 
  4. sp_widget.css 
  5. sp_instance.css 


Service Portal stylesheet inclusion order: 

  1. sp-bootstrap.scss (file from the file system, compiled with sass compiler) 
  2. sp-theme (css includes - asc order, css includes are not compiled) 
  3. sp_page.css (compiled with sass compiler) 
  4. sp_widget.css (compiled with sass compiler) 
  5. sp_instance.css (compiled with sass compiler) 


Note, the branding editor mainly writes to the sp_portal.css_variables field of whatever portal you have selected
