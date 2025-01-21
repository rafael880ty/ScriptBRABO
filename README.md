-- Criação de um modelo básico de Hub

-- Referência aos serviços do Roblox
local Players = game:GetService("Players")
local LocalPlayer = Players.LocalPlayer
local PlayerGui = LocalPlayer:WaitForChild("PlayerGui")

-- Criar a interface principal
local ScreenGui = Instance.new("ScreenGui")
local MainFrame = Instance.new("Frame")
local Title = Instance.new("TextLabel")
local ButtonTemplate = Instance.new("TextButton")

-- Configurações do ScreenGui
ScreenGui.Name = "CustomHub"
ScreenGui.Parent = PlayerGui

-- Configurações do MainFrame
MainFrame.Name = "MainFrame"
MainFrame.Parent = ScreenGui
MainFrame.BackgroundColor3 = Color3.fromRGB(40, 40, 40)
MainFrame.Size = UDim2.new(0, 400, 0, 300)
MainFrame.Position = UDim2.new(0.5, -200, 0.5, -150)
MainFrame.AnchorPoint = Vector2.new(0.5, 0.5)

-- Configurações do Título
Title.Name = "Title"
Title.Parent = MainFrame
Title.BackgroundColor3 = Color3.fromRGB(30, 30, 30)
Title.Size = UDim2.new(1, 0, 0, 50)
Title.Font = Enum.Font.SourceSansBold
Title.Text = "BraCity Rp"
Title.TextColor3 = Color3.fromRGB(255, 255, 255)
Title.TextSize = 20

-- Configurações do modelo de botão
ButtonTemplate.Name = "ButtonTemplate"
ButtonTemplate.BackgroundColor3 = Color3.fromRGB(60, 60, 60)
ButtonTemplate.Size = UDim2.new(0.9, 0, 0, 40)
ButtonTemplate.Position = UDim2.new(0.05, 0, 0, 60)
ButtonTemplate.Font = Enum.Font.SourceSansBold
ButtonTemplate.TextColor3 = Color3.fromRGB(255, 255, 255)
ButtonTemplate.TextSize = 18
ButtonTemplate.Visible = false -- O modelo não será visível

-- Função para adicionar botões dinamicamente
local function AddButton(name, callback)
    local Button = ButtonTemplate:Clone()
    Button.Text = name
    Button.Visible = true
    Button.Parent = MainFrame

    -- Atualizar a posição dos botões
    local buttonCount = #MainFrame:GetChildren() - 2 -- Ignorar Title e ButtonTemplate
    Button.Position = UDim2.new(0.05, 0, 0, 60 + (buttonCount - 1) * 50)

    -- Conectar a função do botão
    Button.MouseButton1Click:Connect(callback)
end

-- Exemplo de uso: Adicionando botões ao Hub
AddButton("Exemplo 1", function()
    print("Botão Exemplo 1 pressionado!")
end)

AddButton("Exemplo 2", function()
    print("Botão Exemplo 2 pressionado!")
end)

-- Você pode continuar adicionando botões conforme necessário!
