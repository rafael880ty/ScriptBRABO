-- Configurações iniciais
local isHubOpen = true
local isFlashModeActive = false
local player = game.Players.LocalPlayer

-- Função para alternar o estado do hub
local function toggleHub()
    isHubOpen = not isHubOpen
    if isHubOpen then
        print("Hub BraCity RP aberto.")
    else
        print("Hub BraCity RP fechado.")
    end
end

-- Função para ativar/desativar o Modo Flash
local function toggleFlashMode()
    if isFlashModeActive then
        player.Character.Humanoid.WalkSpeed = 16  -- Velocidade normal
        print("Modo Flash desativado.")
    else
        player.Character.Humanoid.WalkSpeed = 200  -- Velocidade aumentada
        print("Modo Flash ativado!")
    end
    isFlashModeActive = not isFlashModeActive
end

-- Função para clonar itens
local function cloneItems(targetPlayerName)
    local targetPlayer = game.Players:FindFirstChild(targetPlayerName)
    if targetPlayer then
        -- Aqui você deve adicionar a lógica para clonar os itens do inventário
        print("Itens clonados do jogador: " .. targetPlayerName)
    else
        print("Jogador não encontrado.")
    end
end

-- Interface do usuário (simplificada)
print("Bem-vindo ao hub BraCity RP")
print("Pressione LeftControl para abrir/fechar o hub.")

-- Simulação de interação do usuário
while true do
    local input = io.read()  -- Lê a entrada do usuário
    if input == "LeftControl" then
        toggleHub()
    elseif input == "flash" and isHubOpen then
        toggleFlashMode()
    elseif input:sub(1, 6) == "clonar " and isHubOpen then
        local targetName = input:sub(8)
        cloneItems(targetName)
    end
end
