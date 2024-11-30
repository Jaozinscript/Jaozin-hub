# Jaozin-hub
-- Biblioteca do Hub
local library = loadstring(game:HttpGet("https://raw.githubusercontent.com/xHeptc/Kavo-UI-Library/main/source.lua"))()
local window = library.CreateLib("Script João", "Synapse") -- Tema visual ajustado para atratividade

-- Guias do Hub
local farmTab = window:NewTab("Farm")
local chestTab = window:NewTab("Baús")
local teleportTab = window:NewTab("Teleporte")
local configTab = window:NewTab("Configurações")

-- Variáveis
local farmEnabled = false
local chestEnabled = false
local autoSeaTeleport = false

local settings = {
    clickInterval = 0.5, -- Intervalo entre cliques
    voarAltura = 10, -- Altura ao atacar NPCs
    velocidade = 100 -- Velocidade do jogador
}

-- Função de Farm de NPCs
local function autoFarm()
    while farmEnabled do
        local player = game.Players.LocalPlayer
        local questNPC = nil

        -- Encontrar NPC de missão
        for _, npc in pairs(game.Workspace.NPCs:GetChildren()) do
            if npc:IsA("Model") and npc:FindFirstChild("Humanoid") and npc.Name:lower():find("quest") then
                questNPC = npc
                break
            end
        end

        if questNPC then
            -- Aceitar missão
            local humanoidRootPart = questNPC:FindFirstChild("HumanoidRootPart")
            if humanoidRootPart then
                player.Character.HumanoidRootPart.CFrame = humanoidRootPart.CFrame + Vector3.new(0, 3, 0)
                wait(1)
                local prompt = humanoidRootPart:FindFirstChildOfClass("ProximityPrompt")
                if prompt then
                    fireproximityprompt(prompt)
                end
            end

            -- Encontrar e derrotar inimigos da missão
            for _, inimigo in pairs(game.Workspace.Enemies:GetChildren()) do
                if inimigo:IsA("Model") and inimigo:FindFirstChild("Humanoid") and inimigo.Humanoid.Health > 0 then
                    local humanoidRootPart = inimigo:FindFirstChild("HumanoidRootPart")
                    if humanoidRootPart then
                        player.Character.HumanoidRootPart.CFrame = humanoidRootPart.CFrame + Vector3.new(0, settings.voarAltura, 0)
                        wait(settings.clickInterval)
                        game:GetService("VirtualUser"):Button1Down(Vector2.new(0, 0), humanoidRootPart.Position)
                        wait(0.1)
                        game:GetService("VirtualUser"):Button1Up(Vector2.new(0, 0), humanoidRootPart.Position)
                    end
                end
            end
        end
        wait(1)
    end
end

-- Função de Farm de Baús
local function autoChest()
    while chestEnabled do
        for _, chest in pairs(game.Workspace:GetDescendants()) do
            if chest:IsA("Model") and chest.Name:lower():find("chest") then
                local humanoidRootPart = chest:FindFirstChild("HumanoidRootPart")
                if humanoidRootPart then
                    game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = humanoidRootPart.CFrame + Vector3.new(0, 3, 0)
                    wait(1)
                end
            end
        end
        wait(1)
    end
end

-- Função de Teleporte entre Seas
local function teleportSea(seaNumber)
    local seaLocations = {
        [1] = Vector3.new(0, 0, 0), -- Coordenadas do Sea 1
        [2] = Vector3.new(1000, 0, 1000), -- Coordenadas do Sea 2
        [3] = Vector3.new(2000, 0, 2000) -- Coordenadas do Sea 3
    }

    if seaLocations[seaNumber] then
        game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(seaLocations[seaNumber])
    end
end

-- Configuração de velocidade
local function toggleSpeed(estado)
    local player = game.Players.LocalPlayer
    if estado then
        player.Character.Humanoid.WalkSpeed = settings.velocidade
    else
        player.Character.Humanoid.WalkSpeed = 16 -- Velocidade padrão
    end
end

-- Configuração para andar na água (caso permitido)
local function andarAgua()
    local player = game.Players.LocalPlayer
    if player.Character:FindFirstChild("HumanoidRootPart") then
        player.Character.HumanoidRootPart.Touched:Connect(function(hit)
            if hit.Name == "Water" then
                player.Character.HumanoidRootPart.CFrame = player.Character.HumanoidRootPart.CFrame + Vector3.new(0, 5, 0)
            end
        end)
    end
end

-- Configuração de Hub
farmTab:NewToggle("Ativar Auto Farm", "Liga/desliga o Auto Farm", function(state)
    farmEnabled = state
    if state then
        autoFarm()
    end
end)

chestTab:NewToggle("Ativar Auto Baús", "Liga/desliga o Auto Baús", function(state)
    chestEnabled = state
    if state then
        autoChest()
    end
end)

teleportTab:NewButton("Ir para Sea 1", "Teleporta para o Sea 1", function()
    teleportSea(1)
end)
teleportTab:NewButton("Ir para Sea 2", "Teleporta para o Sea 2", function()
    teleportSea(2)
end)
teleportTab:NewButton("Ir para Sea 3", "Teleporta para o Sea 3", function()
    teleportSea(3)
end)

configTab:NewSlider("Velocidade", "Ajuste de velocidade", 16
