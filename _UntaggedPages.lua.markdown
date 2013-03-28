Title: _UntaggedPages.lua
Timestamp: 2013-03-27 05:44:13 +0000
Created: 2012-10-09 17:50:14 +0000
Last Accessed: 2013-03-27 05:44:15 +0000
Times Accessed:
Tags: Lua
Metadata: 

--
-- Displays all of the pages that do not have tags
--

function string.starts(String,Start)
   return string.sub(String,1,string.len(Start))==Start
end


returnValue = ""

for pageIteration, currentPageTitle in ipairs(wiki.titles()) do
	
	if (string.starts(currentPageTitle,"Docs:") == false and string.starts(currentPageTitle, "Special:") == false) then
	
		currentPageTags = wiki.get(currentPageTitle).tags
		
		if (#currentPageTags == 0) then
			returnValue = returnValue .. "[[" .. currentPageTitle .. "]] "
		end
	end
end

return returnValue