local UI = {}
UI.__index = UI

function UI.new(title)
    local self = setmetatable({}, UI)

    -- Cria a janela principal
    self.window = Instance.new("ScreenGui")
    self.frame = Instance.new("Frame")
    
    self.window.Name = title
    self.window.Parent = game.Players.LocalPlayer:WaitForChild("PlayerGui")
    
    self.frame.BackgroundColor3 = Color3.fromRGB(40, 40, 40)
    self.frame.Size = UDim2.new(0, 300, 0, 450)
    self.frame.Position = UDim2.new(0.5, -150, 0.5, -225)
    self.frame.Parent = self.window
    self.frame.BorderSizePixel = 0
    self.frame.BackgroundTransparency = 0.05
    self.frame.ClipsDescendants = true

    local corner = Instance.new("UICorner")
    corner.CornerRadius = UDim.new(0, 15)
    corner.Parent = self.frame

    self.titleLabel = Instance.new("TextLabel")
    self.titleLabel.Text = "Rafox Hub !!"
    self.titleLabel.Size = UDim2.new(1, 0, 0, 50)
    self.titleLabel.BackgroundColor3 = Color3.fromRGB(60, 60, 60)
    self.titleLabel.TextColor3 = Color3.fromRGB(255, 255, 255)
    self.titleLabel.Font = Enum.Font.SourceSansBold
    self.titleLabel.TextSize = 24
    self.titleLabel.Parent = self.frame

    local scrollFrame = Instance.new("ScrollingFrame")
    scrollFrame.Size = UDim2.new(1, 0, 0, 350)
    scrollFrame.Position = UDim2.new(0, 0, 0, 50)
    scrollFrame.BackgroundColor3 = Color3.fromRGB(50, 50, 50)
    scrollFrame.CanvasSize = UDim2.new(0, 0, 0, 0)
    scrollFrame.ScrollBarThickness = 10
    scrollFrame.Parent = self.frame

    local scrollCorner = Instance.new("UICorner")
    scrollCorner.CornerRadius = UDim.new(0, 15)
    scrollCorner.Parent = scrollFrame

    local contentFrame = Instance.new("Frame")
    contentFrame.Size = UDim2.new(1, 0, 1, 0)
    contentFrame.BackgroundTransparency = 1
    contentFrame.Parent = scrollFrame

    self.centerText = Instance.new("TextLabel")
    self.centerText.Text = "Bem-vindo ao Rafox Hub!"
    self.centerText.Size = UDim2.new(1, 0, 0, 50)
    self.centerText.Position = UDim2.new(0, 0, 0.1, 0)
    self.centerText.BackgroundColor3 = Color3.fromRGB(40, 40, 40)
    self.centerText.TextColor3 = Color3.fromRGB(255, 255, 255)
    self.centerText.Font = Enum.Font.SourceSans
    self.centerText.TextSize = 20
    self.centerText.Parent = contentFrame

    local notification = Instance.new("TextLabel")
    notification.Text = "Rafox Hub O mais brabo Executado !!"
    notification.Size = UDim2.new(1, 0, 0, 40)
    notification.Position = UDim2.new(0, 0, 0, 0)
    notification.BackgroundColor3 = Color3.fromRGB(0, 255, 0)
    notification.TextColor3 = Color3.fromRGB(0, 0, 0)
    notification.Font = Enum.Font.SourceSansBold
    notification.TextSize = 18
    notification.Parent = contentFrame
    notification.Visible = true

    wait(2)
    notification.Visible = false
    self.centerText.Visible = false

    local playerInput = Instance.new("TextBox")
    playerInput.PlaceholderText = "Digite o nome do jogador"
    playerInput.Size = UDim2.new(1, -20, 0, 40)
    playerInput.Position = UDim2.new(0, 10, 0.35, 0)
    playerInput.BackgroundColor3 = Color3.fromRGB(70, 70, 70)
    playerInput.TextColor3 = Color3.fromRGB(255, 255, 255)
    playerInput.Font = Enum.Font.SourceSans
    playerInput.TextSize = 18
    playerInput.Parent = contentFrame

    local inputCorner = Instance.new("UICorner")
    inputCorner.CornerRadius = UDim.new(0, 10)
    inputCorner.Parent = playerInput

    local teleportButton = Instance.new("TextButton")
    teleportButton.Text = "Teletransportar"
    teleportButton.Size = UDim2.new(1, 0, 0, 50)
    teleportButton.Position = UDim2.new(0, 0, 0.45, 0)
    teleportButton.BackgroundColor3 = Color3.fromRGB(0, 120, 255)
    teleportButton.TextColor3 = Color3.fromRGB(255, 255, 255)
    teleportButton.Font = Enum.Font.SourceSansBold
    teleportButton.TextSize = 20
    teleportButton.Parent = contentFrame

    local teleportButtonCorner = Instance.new("UICorner")
    teleportButtonCorner.CornerRadius = UDim.new(0, 10)
    teleportButtonCorner.Parent = teleportButton

    teleportButton.MouseButton1Click:Connect(function()
        local playerName = playerInput.Text
        local targetPlayer = game.Players:FindFirstChild(playerName)

        if targetPlayer then
            local character = game.Players.LocalPlayer.Character
            if character and character:FindFirstChild("HumanoidRootPart") then
                character.HumanoidRootPart.CFrame = targetPlayer.Character.HumanoidRootPart.CFrame
                notification.Text = "Teletransportado para " .. playerName
                notification.Visible = true
                wait(2)
                notification.Visible = false
                self.centerText.Visible = false
            end
        else
            notification.Text = "Jogador não encontrado!"
            notification.Visible = true
            wait(2)
            notification.Visible = false
            self.centerText.Visible = false
        end
    end)

    -- Modo Flash
    local flashFrame = Instance.new("Frame")
    flashFrame.Size = UDim2.new(1, 0, 0, 50)
    flashFrame.BackgroundColor3 = Color3.fromRGB(50, 50, 50)
    flashFrame.Parent = contentFrame

    local flashLabel = Instance.new("TextLabel")
    flashLabel.Text = "Modo Flash"
    flashLabel.Size = UDim2.new(0.7, 0, 1, 0)
    flashLabel.BackgroundColor3 = Color3.fromRGB(50, 50, 50)
    flashLabel.TextColor3 = Color3.fromRGB(255, 255, 255)
    flashLabel.Font = Enum.Font.SourceSansBold
    flashLabel.TextSize = 20
    flashLabel.Parent = flashFrame

    local flashCheckbox = Instance.new("TextButton")
    flashCheckbox.Text = "☐"
    flashCheckbox.Size = UDim2.new(0.3, 0, 1, 0)
    flashCheckbox.Position = UDim2.new(0.7, 0, 0, 0)
    flashCheckbox.BackgroundColor3 = Color3.fromRGB(70, 70, 70)
    flashCheckbox.TextColor3 = Color3.fromRGB(255, 255, 255)
    flashCheckbox.Font = Enum.Font.SourceSansBold
    flashCheckbox.TextSize = 20
    flashCheckbox.Parent = flashFrame

    local isFlashActive = false

    flashCheckbox.MouseButton1Click:Connect(function()
        isFlashActive = not isFlashActive
        local character = game.Players.LocalPlayer.Character
        if character and character:FindFirstChild("Humanoid") then
            if isFlashActive then
                flashCheckbox.Text = "☑"
                character.Humanoid.WalkSpeed = 200
                -- Ativa Noclip
                character.HumanoidRootPart.CanCollide = false
                for _, part in pairs(character:GetDescendants()) do
                    if part:IsA("BasePart") then
                        part.CanCollide = false
                    end
                end
            else
                flashCheckbox.Text = "☐"
                character.Humanoid.WalkSpeed = 16
                -- Desativa Noclip
                character.HumanoidRootPart.CanCollide = true
                for _, part in pairs(character:GetDescendants()) do
                    if part:IsA("BasePart") then
                        part.CanCollide = true
                    end
                end
            end
        end
    end)

    -- Botão de fechar
    local closeButton = Instance.new("TextButton")
    closeButton.Text = "Fechar"
    closeButton.Size = UDim2.new(1, 0, 0, 50)
    closeButton.Position = UDim2.new(0, 0, 1, -50)
    closeButton.BackgroundColor3 = Color3.fromRGB(255, 0, 0)
    closeButton.TextColor3 = Color3.fromRGB(255, 255, 255)
    closeButton.Font = Enum.Font.SourceSansBold
    closeButton.TextSize = 20
    closeButton.Parent = self.frame

    local closeCorner = Instance.new("UICorner")
    closeCorner.CornerRadius = UDim.new(0, 15)
    closeCorner.Parent = closeButton

    closeButton.MouseButton1Click:Connect(function()
        self.window:Destroy()
    end)

    -- Variáveis para arrastar
    local dragging = false
    local dragStart = Vector2.new()
    local startPos = UDim2.new()

    self.titleLabel.InputBegan:Connect(function(input)
        if input.UserInputType == Enum.UserInputType.MouseButton1 then
            dragging = true
            dragStart = input.Position
            startPos = self.frame.Position
            
            input.Changed:Connect(function()
                if input.UserInputState == Enum.UserInputState.End then
                    dragging = false
                end
            end)
        end
    end)

    self.titleLabel.InputChanged:Connect(function(input)
        if dragging and input.UserInputType == Enum.UserInputType.MouseMovement then
            local delta = input.Position - dragStart
            self.frame.Position = UDim2.new(startPos.X.Scale, startPos.X.Offset + delta.X, startPos.Y.Scale, startPos.Y.Offset + delta.Y)
        end
    end)

    return self
end

-- Exemplo de uso
local myUI = UI.new("Rafox Hub !!")  -- Título atualizado
