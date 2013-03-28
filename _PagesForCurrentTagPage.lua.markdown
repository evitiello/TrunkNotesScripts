Title: _PagesForCurrentTagPage.lua
Timestamp: 2013-03-27 22:39:13 +0000
Created: 2012-10-08 22:56:58 +0000
Last Accessed: 2013-03-27 22:39:15 +0000
Times Accessed: 0
Tags: Lua
Metadata: 

--
-- Generates a list of pages that have a tag named the same as the current page.
--

returnValue = ""
titles = ""
pagesWithTag = 0

for pageIteration, currentPageTitle in ipairs(wiki.titles()) do
	
	for tagIteration, tag in ipairs(wiki.get(currentPageTitle).tags) do
	
		if (tag == page.title) then
			pagesWithTag = pagesWithTag + 1
			titles = titles .. "[[" .. currentPageTitle .. "]] "
		end
	
	end
	
end


if (pagesWithTag > 0) then
  returnValue = "###Pages With This Tag###\n " .. titles
end

return returnValue