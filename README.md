# Inventory Controller with Profile Service

## Overview
I developed the Inventory Controller so that it can easily read data returned from Profile Service and implement them into my UI structure through OOP and built-in sorting. The primary concepts to look at is how the client reads the Profile data, the usage of OOP, and the built-in sorting system. So if you're interested with that, please take a look at the basic usage implementation shown below!

## Basic Usage 
The Controller's functionality is actually pretty straight forward; all it does is once the client loads in, the client-side Knit will call a :LoadCharacter function to return their Profile Service data. It then reads the Profile Service data, and creates empty inventory slot objects *(Based on the players InventorySpace data)* in the UI structure I built.
```
local data = Knit.GetService("PlayerService"):LoadCharacter() -->>: The variable data holds the player profile service data which is used later on

for i = 1, data.InventorySpace, 1 do -->>: Creates empty inventory slot objects into UI structure
  local EmptyFrame = InventoryController.newEmpty("ScrollingFrame")
  EmptyFrame:setEmpty()
end
```
After the empty slots are created, the Controller will fill the slots in based on data found in the specified index
```
for i,v in pairs (data.Inventory) do -->>: Fills in empty inventory slot objects if data exists within slot
  local ItemFrame = InventoryController.newItem(v.Name, v.Rarity, v.Upgrades, v.Bonus, v.Equipped, nil, "ScrollingFrame")
  ItemFrame:setItem()
end
```
Afterwards that's pretty much it! The controller will do all the backend work and format it accordingly to my UI structure. *(If you're interested on the **backend OOP coding and the built-in sorting** please take a look at the repo!)*

## Important Links
**Profile Service - https://github.com/MadStudioRoblox/ProfileService**

**(Used in my Fall Accelerator) Demo - https://www.roblox.com/games/9127181027/Accelerator-Game-Concept**
