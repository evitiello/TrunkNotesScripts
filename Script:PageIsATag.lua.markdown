Title: Script:PageIsATag.lua
Timestamp: 2013-03-27 05:28:19 +0000
Created: 2012-10-09 05:35:56 +0000
Last Accessed: 2013-03-27 05:28:22 +0000
Times Accessed: 2
Tags: Lua, Script, CoreMeta
Metadata: 

--
-- Returns text stating if this page is also a tag.
--

function Set(list)
	local set = {}
	for _, l in ipairs(list) do set[l] = true end
	return set
end

returnValue = ""
if Set(wiki.tags())[page.title] then
	returnValue = "*This Page is also a Tag*"
end
return returnValue