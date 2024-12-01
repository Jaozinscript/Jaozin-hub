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

local autoFarmButton = createButton("Auto Farm", 0.1)
local statusButton = createButton("Status", 0.3)
local fruitsButton = createButton("Fruits", 0.5)

-- Funções dos botões
autoFarmButton.MouseButton1Click:Connect(function()
    print("Auto Farm ativado")
    -- Mostrar opções de Auto Farm
    createAutoFarmOptions()
end)

statusButton.MouseButton1Click:Connect(function()
    print("Status mostrado")
    -- Mostrar opções de Status
    createStatusOptions()
end)

fruitsButton.MouseButton1Click:Connect(function()
    print("Fruits coletado")
    -- Mostrar opções de Frutas
    createFruitOptions()
end)

print("Interface gráfica criada com sucesso!")

-- Funções adicionais para as opções

function createAutoFarmOptions()
    -- Adicione aqui a lógica para mostrar as opções de Auto Farm
    -- Incluindo a lógica de Auto Farm Level e Auto Farm Baú
end

function createStatusOptions()
    -- Adicione aqui a lógica para mostrar as opções de Status
    -- Incluindo a lógica de seleção de Status
end

function createFruitOptions()
    -- Adicione aqui a lógica para mostrar as opções de Frutas
    -- Incluindo a lógica de girar frutas, guardar frutas e teleportar para frutas
end
