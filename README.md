TrunkNotesScripts
=================

Lua Scripts for use in Trunk Notes

##Pages are Tags, Tags are Pages.##

This set of scripts makes Pages and Tags synonymous.  Add the following to your Special:Footer page:

	{{lua _TagsForCurrentPage.lua}}

	{{lua _PagesForCurrentTagPage.lua}}

This will give you a list of tags for this page, which are links to pages of that same name, as well as a list of Pages that are tagged with the name of the current page.

For example, if the page we are viewing is named HighPriority, with "Tasks" and "GTD" as tags, the first script will list those tags as links to pages named "Tasks" and "GTD".  The second script will list out all pages that are tagged "HighPriority".


and something like this in your Special:Header page

	#{{lua _PageTitle.lua}}#

	{{lua _PageIsATag.lua}}

These simply print out the PageTitle as an H1, and prints the test "This page is also a tag" under it, if that is true.

##Other Scripts##

There are a few other scripts here that are fairly self explainatory.