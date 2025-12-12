-- 🩸 BROOKHAVEN SPAM V18 DELTA 2025 - COMANDOS EXATOS
local Players = game:GetService("Players")
local ReplicatedStorage = game:GetService("ReplicatedStorage")
local UserInputService = game:GetService("UserInputService")
local Chat = game:GetService("Chat")
local player = Players.LocalPlayer
local playerGui = player:WaitForChild("PlayerGui")

local comandos = {
    "/render",
    "/amarra", 
    "/pegar",
    "/Mat sem erro. §{🇲🇽 Família nostra🇲🇽}§"
}

local screenGui = Instance.new("ScreenGui")
screenGui.Name = "BrookSpamV18"
screenGui.ResetOnSpawn = false
screenGui.Parent = playerGui

-- BOTÃO MINI VERMELHO 🩸
local btnToggle = Instance.new("TextButton")
btnToggle.Size = UDim2.new(0, 50, 0, 50)
btnToggle.Position = UDim2.new(0, 20, 0, 20)
btnToggle.BackgroundColor3 = Color3.new(1, 0, 0)
btnToggle.Text = "🩸"
btnToggle.TextScaled = true
btnToggle.Font = Enum.Font.SourceSansBold
btnToggle.Parent = screenGui

local toggleCorner = Instance.new("UICorner")
toggleCorner.CornerRadius = UDim2.new(1, 0, 1, 0)
toggleCorner.Parent = btnToggle

-- GUI PRINCIPAL (FECHADA)
local frame = Instance.new("Frame")
frame.Size = UDim2.new(0, 280, 0, 320)
frame.Position = UDim2.new(0.5, -140, 0.5, -160)
frame.BackgroundColor3 = Color3.new(0.1, 0.1, 0.1)
frame.Visible = false
frame.Active = true
frame.Draggable = true
frame.Parent = screenGui

local frameCorner = Instance.new("UICorner")
frameCorner.CornerRadius = UDim2.new(0, 12, 0, 12)
frameCorner.Parent = frame

-- TÍTULO
local title = Instance.new("TextLabel")
title.Size = UDim2.new(1, 0, 0, 50)
title.BackgroundColor3 = Color3.new(0.2, 0.2, 0.2)
title.Text = "🩸 BROOKHAVEN SPAM V18"
title.TextColor3 = Color3.new(1, 1, 1)
title.TextScaled = true
title.Font = Enum.Font.SourceSansBold
title.Parent = frame

local titleCorner = Instance.new("UICorner")
titleCorner.CornerRadius = UDim2.new(0, 12, 0, 12)
titleCorner.Parent = title

-- BOTÃO FECHAR
local closeBtn = Instance.new("TextButton")
closeBtn.Size = UDim2.new(0, 30, 0, 30)
closeBtn.Position = UDim2.new(1, -35, 0, 10)
closeBtn.BackgroundColor3 = Color3.new(1, 0.2, 0.2)
closeBtn.Text = "✕"
closeBtn.TextColor3 = Color3.new(1, 1, 1)
closeBtn.TextScaled = true
closeBtn.Font = Enum.Font.SourceSansBold
closeBtn.Parent = title

local closeCorner = Instance.new("UICorner")
closeCorner.CornerRadius = UDim2.new(1, 0, 1, 0)
closeCorner.Parent = closeBtn

-- FUNÇÃO CHAT 100% SEGURA
local function enviarChat(msg)
    pcall(function()
        if game:GetService("TextChatService"):FindFirstChild("TextChannels") then
            local channel = game:GetService("TextChatService").TextChannels:FindFirstChild("RBXGeneral")
            if channel then channel:SendAsync(msg) end
        end
    end)
    pcall(function()
        local chatEvents = ReplicatedStorage:FindFirstChild("DefaultChatSystemChatEvents")
        if chatEvents then
            chatEvents.SayMessageRequest:FireServer(msg, "All")
        end
    end)
    pcall(function()
        if player.Character and player.Character:FindFirstChild("Head") then
            Chat:Chat(player.Character.Head, msg)
        end
    end)
end

-- 4 BOTÕES DOS COMANDOS EXATOS
for i, cmd in pairs(comandos) do
    local btn = Instance.new("TextButton")
    btn.Size = UDim2.new(0.9, 0, 0, 55)
    btn.Position = UDim2.new(0.05, 0, 0, 60 + (i-1) * 65)
    btn.BackgroundColor3 = Color3.new(0.2, 0.4, 0.8)
    btn.Text = cmd
    btn.TextColor3 = Color3.new(1, 1, 1)
    btn.TextScaled = true
    btn.Font = Enum.Font.SourceSansBold
    btn.Parent = frame
    
    local btnCorner = Instance.new("UICorner")
    btnCorner.CornerRadius = UDim2.new(0, 8, 0, 8)
    btnCorner.Parent = btn
    
    btn.MouseButton1Click:Connect(function()
        enviarChat(cmd)
        print("✅ " .. cmd .. " ENVIADO NO CHAT!")
    end)
end

-- TOGGLE GUI
btnToggle.MouseButton1Click:Connect(function()
    frame.Visible = not frame.Visible
    btnToggle.BackgroundColor3 = frame.Visible and Color3.new(0, 1, 0) or Color3.new(1, 0, 0)
    btnToggle.Text = frame.Visible and "✅" or "🩸"
end)

closeBtn.MouseButton1Click:Connect(function()
    frame.Visible = false
    btnToggle.BackgroundColor3 = Color3.new(1, 0, 0)
    btnToggle.Text = "🩸"
end)

-- INSERT TOGGLE
UserInputService.InputBegan:Connect(function(input)
    if input.KeyCode == Enum.KeyCode.Insert then
        frame.Visible = not frame.Visible
        btnToggle.BackgroundColor3 = frame.Visible and Color3.new(0, 1, 0) or Color3.new(1, 0, 0)
        btnToggle.Text = frame.Visible and "✅" or "🩸"
    end
end)

print("🩸 V18 CARREGADO - 4 COMANDOS EXATOS! CLIQUE VERMELHO 🩸")
