drupal-custom-import
====================

Drupal module for exporting/importing nodes in a generic sense (title, content, and book hierarchy).
It allows for a simple transfer of node data maintaining: 

		* Node Title
		* Node Body including summary
		* Book TOC position if it is a book.
		
The process involves exporting the node data from the source site into a base64 string and 
using that string to import the data into the target site.

Exporting Nodes:

	This part of the module works on the source site with Views Bulk Operation to provide a simple means to export select modules. 
	It adds an option/action "Custom Migrate (Shanti)" to the VBO menu of a view, when activated.
	One can then select several nodes and perform this actual. This will give a form with a text area that contains a 
	base64 version of the serialized data. This base64 string in the textarea needs to be copied and pasted into the import
	form of this same module on the target site.
	
	Right now, it automatically switches description language automatically to 'bo' and assumes that the content type names for book is
	"shanti_essay_top" and "shanti_essay_page" for books and pages respectively.
	
	The resulting page has a text area with a long string in base 64 that contains the serialized information of the selected nodes. 
	This needs to be copied.
	
Importing Nodes:

	This part of the module works on the target site. To import nodes exported from this module on a source site into a separate target site,
	one goes to the URL {target site base url}/custom/import and paste the base64 string into the data text area of that form and fill in 
	the other requisite information, and pressing the button "Import".
	
	The result will appear in drupal messages and the form will be reloaded.
	
Created by ndg8f on Oct. 11, 2013

TO DOS:
========

	* Create a view of all migrations/imports from the custom_migrate_migrations. Allowing user to see information about migrations
	* Create ability to enter target site language.
	* Add ability to import user/creator with node, setting whether to import user
	* Indicate in View whether an item has already been exported.
	* Do not allow same node to be imported more than once (or providing setting to enforce that)
	* Add Notes/Description field to the Import form and save to table a description or notes on each import/migration
