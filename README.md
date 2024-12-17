-- Configurações iniciais
getgenv().SpeedTween = 350
getgenv().RandomFruit = true
getgenv().EspFruit = true
getgenv().Team = "Pirate"
getgenv().WebhookUrl = '' -- Coloque a URL do seu webhook aqui, se necessário

-- Inventário de frutas
local inventory = {}  -- Tabela para armazenar frutas coletadas

-- Função para forçar a escolha do time "Pirata"
local function escolherTime()
    local Players = game:GetService("Players")
    local player = Players.LocalPlayer

    -- Acessa o time "Pirate" diretamente
    for _, team in pairs(game:GetService("Teams"):GetChildren()) do
        if team.Name == getgenv().Team then
            player.Team = team
            print("Time definido como Pirata!")
            return
        end
    end
end

-- Função para coletar frutas no Blox Fruits
local function coletarFrutas()
    if getgenv().RandomFruit then
        print("Buscando frutas aleatórias...")

        -- Procurando frutas no mapa
        for _, v in pairs(workspace:GetChildren()) do
            if v.Name == "Fruit" then  -- Verifica se o objeto é uma fruta
                local fruit = v
                if fruit:IsA("Model") and fruit:FindFirstChild("TouchInterest") then
                    -- Verifica se a fruta tem a propriedade de toque
                    -- Aqui você pode adicionar lógica para mover o jogador até a fruta

                    -- Adiciona a fruta ao inventário
                    table.insert(inventory, fruit.Name)
                    print("Fruta coletada: " .. fruit.Name)
                    
                    -- Exibe o inventário
                    print("Inventário atual: ")
                    for _, fruitName in pairs(inventory) do
                        print(fruitName)
                    end
                    
                    -- Opcional: Tenta pegar a fruta (simulando toque)
                    firetouchinterest(game.Players.LocalPlayer.Character.HumanoidRootPart, fruit, 0)
                    wait(1)
                    firetouchinterest(game.Players.LocalPlayer.Character.HumanoidRootPart, fruit, 1)
                    return -- Apenas coleta uma fruta por vez
                end
            end
        end
    end
end

-- Função para ativar ESP de frutas (se estiver ativado)
local function ativarEsp()
    if getgenv().EspFruit then
        print("ESP de frutas ativado!")
        
        -- Para cada fruta, criamos um highlight para destacar no mapa
        for _, v in pairs(workspace:GetChildren()) do
            if v.Name == "Fruit" then
                local fruit = v
                if fruit:IsA("Model") then
                    -- Criar highlight para a fruta
                    local highlight = Instance.new("Highlight")
                    highlight.Parent = fruit
                    highlight.Adornee = fruit
                    highlight.FillColor = Color3.fromRGB(255, 0, 0)  -- Cor vermelha para a fruta
                    highlight.OutlineColor = Color3.fromRGB(255, 255, 255)  -- Cor branca para o contorno
                    highlight.OutlineTransparency = 0.5
                    highlight.FillTransparency = 0.2
                end
            end
        end
    end
end

-- Função principal que coordena as ações
local function executarScript()
    escolherTime()      -- Escolhe automaticamente o time
    coletarFrutas()     -- Coleta frutas aleatórias, se ativado
    ativarEsp()         -- Ativa o ESP, se necessário
end

-- Chama a função principal
executarScript()
