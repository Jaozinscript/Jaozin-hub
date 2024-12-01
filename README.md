local player = game.Players.LocalPlayer
local screenGui = Instance.new("ScreenGui", player:WaitForChild("PlayerGui"))
screenGui.Name = "BloxFruitsGui"
screenGui.ResetOnSpawn = false

-- Adicionando o título "Jaozin Hub"
local title = Instance.new("TextLabel", screenGui)
title.Size = UDim2.new(0.8, 0, 0.1, 0)
title.Position = UDim2.new(0.1, 0, 0, 0)
title.BackgroundColor3 = Color3.fromRGB(0, 0, 0)
title.BackgroundTransparency = 0.5
title.Text = "Jaozin Hub"
title.TextColor3 = Color3.fromRGB(255, 255, 255)
title.Font = Enum.Font.SourceSansBold
title.TextScaled = true

-- Configuração da Interface
local frame = Instance.new("Frame", screenGui)
frame.Size = UDim2.new(0.2, 0, 1, 0)
frame.Position = UDim2.new(0, 0, 0.1, 0)
frame.BackgroundColor3 = Color3.fromRGB(0, 0, 0)
frame.BackgroundTransparency = 0.5

-- Criação dos botões
local function createButton(name, position)
    local button = Instance.new("TextButton", frame)
    button.Size = UDim2.new(0.8, 0, 0.1, 0)
    button.Position = UDim2.new(0.1, 0, position, 0)
    button.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
    button.BackgroundTransparency = 0.3
    button.Text = name
    button.TextColor3 = Color3.fromRGB(0, 0, 0)
    return button
end

local autoFarmButton = createButton("Farm", 0.1)
local statusButton = createButton("Status", 0.3)
local seaEventButton = createButton("Sea Evento", 0.5)
local questsButton = createButton("Quests", 0.7)
local settingsButton = createButton("Configurações", 0.9)

-- Funções dos botões
autoFarmButton.MouseButton1Click:Connect(function()
    print("Farm ativado")
    createFarmOptionsRedz()
end)

statusButton.MouseButton1Click:Connect(function()
    print("Status mostrado")
    createStatusOptionsRedz()
end)

seaEventButton.MouseButton1Click:Connect(function()
    print("Sea Evento ativado")
    createSeaEventOptionsAzure()
end)

questsButton.MouseButton1Click:Connect(function()
    print("Quests mostradas")
    createQuestsOptionsRedz()
end)

settingsButton.MouseButton1Click:Connect(function()
    print("Configurações mostradas")
    createSettingsOptionsRedz()
end)

print("Interface gráfica criada com sucesso!")

-- Funções adicionais para as opções
local optionsFrame = Instance.new("Frame", screenGui)
optionsFrame.Size = UDim2.new(0.6, 0, 0.8, 0)
optionsFrame.Position = UDim2.new(0.25, 0, 0.15, 0)
optionsFrame.BackgroundColor3 = Color3.fromRGB(0, 0, 0)
optionsFrame.BackgroundTransparency = 0.5
optionsFrame.Visible = false

function createFarmOptionsRedz()
    optionsFrame:ClearAllChildren()
    optionsFrame.Visible = true
    local farmLabel = Instance.new("TextLabel", optionsFrame)
    farmLabel.Size = UDim2.new(1, 0, 0.1, 0)
    farmLabel.Position = UDim2.new(0, 0, 0, 0)
    farmLabel.BackgroundColor3 = Color3.fromRGB(0, 0, 0)
    farmLabel.BackgroundTransparency = 0.5
    farmLabel.Text = "Opções de Farm do Redz"
    farmLabel.TextColor3 = Color3.fromRGB(255, 255, 255)
    farmLabel.Font = Enum.Font.SourceSansBold
    farmLabel.TextScaled = true

    -- Botão para ativar/desativar Auto Farm
    local autoFarmToggle = Instance.new("TextButton", optionsFrame)
    autoFarmToggle.Size = UDim2.new(0.8, 0, 0.1, 0)
    autoFarmToggle.Position = UDim2.new(0.1, 0, 0.2, 0)
    autoFarmToggle.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
    autoFarmToggle.BackgroundTransparency = 0.3
    autoFarmToggle.Text = "Ativar Auto Farm"
    autoFarmToggle.TextColor3 = Color3.fromRGB(0, 0, 0)

    local autoFarmActive = false
    autoFarmToggle.MouseButton1Click:Connect(function()
        autoFarmActive = not autoFarmActive
        autoFarmToggle.Text = autoFarmActive and "Desativar Auto Farm" or "Ativar Auto Farm"
        print("Auto Farm " .. (autoFarmActive and "ativado" or "desativado"))
    end)
end

function createStatusOptionsRedz()
    optionsFrame:ClearAllChildren()
    optionsFrame.Visible = true
    local statusLabel = Instance.new("TextLabel", optionsFrame)
    statusLabel.Size = UDim2.new(1, 0, 0.1, 0)
    statusLabel.Position = UDim2.new(0, 0, 0, 0)
    statusLabel.BackgroundColor3 = Color3.fromRGB(0, 0, 0)
    statusLabel.BackgroundTransparency = 0.5
    statusLabel.Text = "Opções de Status do Redz"
    statusLabel.TextColor3 = Color3.fromRGB(255, 255, 255)
    statusLabel.Font = Enum.Font.SourceSansBold
    statusLabel.TextScaled = true

    -- Botão para ativar/desativar Status
    local statusToggle = Instance.new("TextButton", optionsFrame)
    statusToggle.Size = UDim2.new(0.8, 0, 0.1, 0)
    statusToggle.Position = UDim2.new(0.1, 0, 0.2, 0)
    statusToggle.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
    statusToggle.BackgroundTransparency = 0.3
    statusToggle.Text = "Ativar Status"
    statusToggle.TextColor3 = Color3.fromRGB(0, 0, 0)

    local statusActive = false
    statusToggle.MouseButton1Click:Connect(function()
        statusActive = not statusActive
        statusToggle.Text = statusActive and "Desativar Status" or "Ativar Status"
        print("Status " .. (statusActive and "ativado" or "desativado"))
    end)
end

function createSeaEventOptionsAzure()
    optionsFrame:ClearAllChildren()
    optionsFrame.Visible = true
    local seaEventLabel = Instance.new("TextLabel", optionsFrame)
    seaEventLabel.Size = UDim2.new(1, 0, 0.1, 0)
    seaEventLabel.Position = UDim2.new(0, 0, 0, 0)
    seaEventLabel.BackgroundColor3 = Color3.fromRGB(0, 0, 0)
    seaEventLabel.BackgroundTransparency = 0.5
    seaEventLabel.Text = "Opções de Auto Sea Event do W Azure"
    seaEventLabel.TextColor3 = Color3.fromRGB(255, 255, 255)
    seaEventLabel.Font = Enum.Font.SourceSansBold
    seaEventLabel.TextScaled = true

    -- Botão para ativar/desativar Sea Event
    local seaEventToggle = Instance.new("TextButton", optionsFrame)
    seaEventToggle.Size = UDim2.new(0.8, 0, 0.1, 0)
    seaEventToggle.Position = UDim2.new(0.1, 0, 0.2, 0)
    seaEventToggle.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
    seaEventToggle.BackgroundTransparency = 0.3
    seaEventToggle.Text = "Ativar Sea Event"
    seaEventToggle.TextColor3 = Color3.fromRGB(0, 0, 0)

    local seaEventActive = false
    seaEventToggle.MouseButton1Click:Connect(function()
        seaEventActive = not seaEventActive
        seaEventToggle.Text = seaEventActive and "Desativar Sea Event" or "Ativar Sea Event"
        print("Sea Event " .. (seaEventActive and "ativado" or "desativado"))
    end)
end

function createQuestsOptionsRedz()
    optionsFrame:ClearAllChildren()
    optionsFrame.Visible = true
    local questsLabel = Instance.new("TextLabel", optionsFrame)
    questsLabel.Size = UDim2.new(1, 0, 0.1, 0)
    questsLabel.Position = UDim2.new(0, 0, 0, 0)
    questsLabel.BackgroundColor3 = Color3.fromRGB(0, 0, 0)
    questsLabel.BackgroundTransparency = 0.5
