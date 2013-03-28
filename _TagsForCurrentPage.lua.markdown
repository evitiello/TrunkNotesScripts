Title: _TagsForCurrentPage.lua
Timestamp: 2013-03-27 05:27:54 +0000
Created: 2012-10-08 18:21:39 +0000
Last Accessed: 2013-03-27 05:28:00 +0000
Times Accessed:
Tags: Lua
Metadata: 

--
-- Displays the tags for the current page.
--

returnValue = ""

if (#page.tags > 0) then
  returnValue = returnValue .. "###Tags###\n "
  for i, tag in ipairs(page.tags) do
    returnValue = returnValue .. "[[" .. tag .. "]] "
  end
end

return returnValue