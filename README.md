#Overview

oUF Maelstrom is a way for Enhancement shaman to trakc their Maelstrom Weapon stacks like combo points.

#How to make it work

If the layout you use already supports it you can just download it and it should work.

Otherwise here are the guidelines

1. Create a frame like you would do for just any element
2. Create 5 frames (one for each stack), it can be a StatusBar or just a frame with a texture
3. Add your own flavor if you want to with Pre/PostUpdate functions

A barebone code would look like this

```
local maelstrom = CreateFrame("Frame", nil, self)
maelstrom:SetPoint('CENTER', self.Health, 'TOP', 0, 1)
maelstrom:SetHeight(5)
maelstrom:SetWidth(5)

for i = 1,5 do
	maelstrom[i] = CreateFrame("StatusBar", self:GetName().."_Maelstrom"..i, self)
	maelstrom[i]:SetHeight(5)
	maelstrom[i]:SetWidth(maelstrom:GetWidth()/5-2)
	maelstrom[i]:SetStatusBarTexture(texture)
	maelstrom[i]:SetStatusBarColor(.32,.19,.63)
	maelstrom[i]:SetFrameLevel(10)

	if (i == 1) then
		maelstrom[i]:SetPoint('LEFT', maelstrom, 'LEFT', 1, 0)
	else
		maelstrom[i]:SetPoint('TOPLEFT', maelstrom[i-1], 'TOPRIGHT', 2, 0)
	end
end

self.Maelstrom = maelstrom
```