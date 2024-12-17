if game.PlaceId == 2753915549 or game.PlaceId == 4442272183 or game.PlaceId == 7449423635 then
    -- Aumentando o tempo de espera para garantir que a GUI tenha sido carregada
    task.wait(5)  -- Aumentado o tempo de espera para 5 segundos
    
    -- Acessar a GUI do jogador
    local playerGui = game:GetService("Players").LocalPlayer.PlayerGui
    local chooseTeamGui = playerGui:WaitForChild("Main"):WaitForChild("ChooseTeam")
    
    -- Acessar os botões de seleção de time
    local piratesButton = chooseTeamGui.Container.Pirates.Frame.TextButton
    local marinesButton = chooseTeamGui.Container.Marines.Frame.TextButton
    
    -- Verificar se os botões estão visíveis antes de tentar interagir com eles
    if piratesButton and marinesButton then
        print("GUI de seleção de time encontrada")
        
        -- Verificar o time configurado e ativar o botão correspondente
        if getgenv().Team == "Pirate" then
            print("Selecionando time Pirates")
            piratesButton:Activate()  -- Usando Activate() em vez de Click()
        elseif getgenv().Team == "Marine" then
            print("Selecionando time Marines")
            marinesButton:Activate()  -- Usando Activate() em vez de Click()
        else
            print("Selecionando time Pirates por padrão")
            piratesButton:Activate()  -- Usando Activate() em vez de Click()
        end
    else
        print("Botões de seleção de time não encontrados ou não visíveis")
    end

    -- Executar script externo (se necessário)
    local queueteleport = syn and syn.queue_on_teleport or queue_on_teleport or fluxus and fluxus.queue_on_teleport
    if queueteleport then
        local script = [[loadstring(game:HttpGet('https://raw.githubusercontent.com/VNT-UNIVERSAL/Panda-Hub/main/Release/fruit.lua'))()]]
        queueteleport(script)
    end
    loadstring(game:HttpGet('https://raw.githubusercontent.com/VNT-UNIVERSAL/Panda-Hub/main/Release/fruit.lua'))()
end
