Title: _PageIsATag.lua
Timestamp: 2013-03-27 05:28:19 +0000
Created: 2012-10-09 05:35:56 +0000
Last Accessed: 2013-03-27 05:28:22 +0000
Times Accessed: 0
Tags: Lua
Metadata: 

--
-- Returns text stating if this page is also a tag.
--

returnValue = ""
pageIsTag = false

for tagIteration, currentTag in ipairs(wiki.tags()) do
	if (currentTag == page.title) then
		pageIsTag = true
	end
end

if (pageIsTag == true) then
  returnValue = returnValue .. "*This Page is also a Tag*"
end

return returnValue