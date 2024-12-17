task.wait(1)  -- Aguardar a GUI carregar

local playerGui = game:GetService("Players").LocalPlayer.PlayerGui.Main
local chooseTeamGui = playerGui:WaitForChild("ChooseTeam")
local piratesButton = chooseTeamGui:WaitForChild("Container"):WaitForChild("Pirates"):WaitForChild("Frame"):WaitForChild("TextButton")
local marinesButton = chooseTeamGui:WaitForChild("Container"):WaitForChild("Marines"):WaitForChild("Frame"):WaitForChild("TextButton")

-- Verificar e acionar a seleção de time
if string.find(tostring(getgenv().Team), "Pirate") then
    piratesButton:Click()
elseif string.find(tostring(getgenv().Team), "Marine") then
    marinesButton:Click()
else
    piratesButton:Click()  -- Default para Pirate se nenhum time for especificado
end
local queueteleport = syn and syn.queue_on_teleport or queue_on_teleport or fluxus and fluxus.queue_on_teleport
if queueteleport then
local script = [[loadstring(game:HttpGet('https://raw.githubusercontent.com/VNT-UNIVERSAL/Panda-Hub/main/Release/fruit.lua'))()]]
queueteleport(script)
end
loadstring(game:HttpGet('https://raw.githubusercontent.com/VNT-UNIVERSAL/Panda-Hub/main/Release/fruit.lua'))()
end
