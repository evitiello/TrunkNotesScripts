Title: Script:TagCloud.lua
Timestamp: 2012-10-12 18:30:40 +0000
Created: 2012-10-09 17:29:19 +0000
Last Accessed: 2012-10-12 18:30:44 +0000
Times Accessed: 2
Tags: Lua, Script, CoreMeta
Metadata: 

--
-- Makes a Tag Cloud.
--

function Set(list)
	local set = {}
	for _, l in ipairs(list) do set[l] = set[l] + 1 end
	return set
end

function allValues(obj)
	local values = {}
	for k,v in pairs(obj) do
		values[#values+1] = v
	end
	return values
end

function valueSort(t, fn)
	-- if #t == 0 then return nil, nil end
	values = allValues(t)
	value = values[1]
	for k, v in pairs(t) do
		if fn(value, v) then value = v end
	end
	return value
end

function adjustScale(marker, oldMin, oldMax, newMin, newMax)
	return math.floor((((marker - oldMin) * (newMax - newMin)) / (oldMax - oldMin)) + newMin)
end

returnValue = ""

-- tag = # of occurances
tagSet = {}
for pageIteration, currentPageTitle in ipairs(wiki.titles()) do	
	for tagIteration, tag in ipairs(wiki.get(currentPageTitle).tags) do
		if tagSet[tag] then
			tagSet[tag] = tagSet[tag] + 1
		else
			tagSet[tag] = 1
		end
	end
end

lowestTagCount = valueSort(tagSet, function(a,b) return a > b end)
highestTagCount = valueSort(tagSet, function(a,b) return a < b end)

for key, value in pairs(tagSet) do
	spanSize = adjustScale(value, lowestTagCount, highestTagCount, 1, 20)
	returnValue = returnValue .. "<span class='tagCloud_" .. spanSize .. "'>[[" .. key .. "]]</span> "
end
return returnValue

