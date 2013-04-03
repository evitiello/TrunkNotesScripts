Title: Script:RecentlyModified.lua
Timestamp: 2013-03-27 22:50:49 +0000
Created: 2013-03-27 05:41:29 +0000
Last Accessed: 2013-03-27 23:51:11 +0000
Times Accessed: 10
Tags: Lua, Script, CoreMeta
Metadata: gpslongitude=-121.942206,gpslatitude=37.392341

--
-- Displays the last 20 pages that have been modified.
--

function string.starts(String,Start)
   return string.sub(String,1,string.len(Start))==Start
end

returnString = ""

pageTimes = {}
pageTimeMapping = {}

for pageIteration, pageTitle in ipairs(wiki.titles()) do
	pageUpdatedTime = wiki.get(pageTitle).updated
	table.insert(pageTimes, pageUpdatedTime)
	pageTimeMapping[pageUpdatedTime] = pageTitle
end
table.sort(pageTimes, function(a,b) return a>b end)

for i=1,20 do
	returnString = returnString .. "[[" .. pageTimeMapping[pageTimes[i]] .. "]] "
end

return returnString