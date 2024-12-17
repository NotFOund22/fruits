if game.PlaceId == 2753915549 or game.PlaceId == 4442272183 or game.PlaceId == 7449423635 then
task.wait(3)
local playerGui = game:GetService("Players").LocalPlayer.PlayerGui
local mainGui = playerGui:WaitForChild("Main")
local chooseTeamGui = mainGui:WaitForChild("ChooseTeam")

local piratesButton = chooseTeamGui:WaitForChild("Container"):WaitForChild("Pirates"):WaitForChild("Frame"):WaitForChild("TextButton")
local marinesButton = chooseTeamGui:WaitForChild("Container"):WaitForChild("Marines"):WaitForChild("Frame"):WaitForChild("TextButton")

local selectedTeam = getgenv().Team or "Pirate"  -- Se getgenv().Team não for definido, usa "Pirate" como padrão

if string.find(tostring(selectedTeam), "Pirate") then
    piratesButton:Click()  -- Clica no botão de "Pirates"
elseif string.find(tostring(selectedTeam), "Marine") then
    marinesButton:Click()  -- Clica no botão de "Marines"
else
    piratesButton:Click()  -- Se não for "Pirate" nem "Marine", clica em "Pirates" por padrão
end
local queueteleport = syn and syn.queue_on_teleport or queue_on_teleport or fluxus and fluxus.queue_on_teleport
if queueteleport then
local script = [[loadstring(game:HttpGet('https://raw.githubusercontent.com/VNT-UNIVERSAL/Panda-Hub/main/Release/fruit.lua'))()]]
queueteleport(script)
end
loadstring(game:HttpGet('https://raw.githubusercontent.com/VNT-UNIVERSAL/Panda-Hub/main/Release/fruit.lua'))()
end
