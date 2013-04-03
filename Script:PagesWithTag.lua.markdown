Title: Script:PagesWithTag.lua
Timestamp: 2013-03-27 05:26:17 +0000
Created: 2012-10-09 17:29:19 +0000
Last Accessed: 2013-03-27 05:26:21 +0000
Times Accessed: 2
Tags: Lua, Script, CoreMeta
Metadata: 

-- 
-- Displays a list of Pages with a specified tag
-- arg1 = the tag to search for
-- arg2 = "true" / "false" : Show the Header?

function Set(list)
	local set = {}
	for _, l in ipairs(list) do set[l] = true end
	return set
end

returnValue = ""
titles = ""
tagToFind = args[1]
pagesWithTag = 0

for pageIteration, currentPageTitle in ipairs(wiki.titles()) do	
	if Set(wiki.get(currentPageTitle).tags)[tagToFind] then
		pagesWithTag = pagesWithTag + 1
		titles = titles .. "[[" .. currentPageTitle .. "]] "
	end
end

if (pagesWithTag > 0) then
	if (args[2] == "true") then
		returnValue = returnValue .. "## [[" .. tagToFind .. "]] ##\n"
	end
	returnValue = returnValue .. titles
else	
	returnValue = "*No pages found tagged " .. tagToFind .. "*"
end

return returnValue