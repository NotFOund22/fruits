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

-- Função para coletar frutas aleatórias (se estiver ativado)
local function coletarFrutas()
    if getgenv().RandomFruit then
        -- Código para encontrar e coletar frutas aleatórias
        -- Isso depende de como as frutas estão localizadas no jogo
        print("Buscando frutas aleatórias...")

        -- Simulação de coleta de frutas (exemplo simples)
        local fruits = {"Fruit1", "Fruit2", "Fruit3"}  -- Exemplo de frutas disponíveis
        local chosenFruit = fruits[math.random(1, #fruits)]  -- Escolhe uma fruta aleatória
        
        -- Adiciona a fruta coletada ao inventário
        table.insert(inventory, chosenFruit)
        print("Fruta coletada: " .. chosenFruit)
        
        -- Exemplo de como mostrar o inventário no console
        print("Inventário atual: ")
        for _, fruit in pairs(inventory) do
            print(fruit)
        end
    end
end

-- Função para ativar ESP de frutas (se estiver ativado)
local function ativarEsp()
    if getgenv().EspFruit then
        -- Código para ativar o ESP
        -- Isso depende de como o ESP está implementado no jogo
        print("ESP de frutas ativado!")
        -- Exemplo: Mostrar frutas no mapa
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
