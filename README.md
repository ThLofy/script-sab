-- LocalScript (coloque em StarterPlayer.StarterPlayerScripts)
local Players = game:GetService("Players")
local TweenService = game:GetService("TweenService")
local player = Players.LocalPlayer
local playerGui = player:WaitForChild("PlayerGui")

-- Criar GUI única
local screenGui = Instance.new("ScreenGui")
screenGui.Name = "UltimateBypassUI"
screenGui.ResetOnSpawn = false
screenGui.ZIndexBehavior = Enum.ZIndexBehavior.Sibling
screenGui.Parent = playerGui

-- Fundo escuro com transparência
local background = Instance.new("Frame")
background.Name = "Background"
background.Size = UDim2.new(1, 0, 1, 0)
background.BackgroundColor3 = Color3.fromRGB(0, 0, 0)
background.BackgroundTransparency = 0.4
background.BorderSizePixel = 0
background.Parent = screenGui

-- Container principal com gradiente
local main = Instance.new("Frame")
main.Name = "MainFrame"
main.AnchorPoint = Vector2.new(0.5, 0.5)
main.Position = UDim2.new(0.5, 0, 0.5, 0)
main.Size = UDim2.new(0, 350, 0, 280)
main.BackgroundColor3 = Color3.fromRGB(20, 20, 20)
main.BorderSizePixel = 0
main.Parent = screenGui

-- Gradiente profissional
local gradient = Instance.new("UIGradient")
gradient.Rotation = 90
gradient.Color = ColorSequence.new({
    ColorSequenceKeypoint.new(0, Color3.fromRGB(30, 30, 30)),
    ColorSequenceKeypoint.new(1, Color3.fromRGB(15, 15, 15))
})
gradient.Parent = main

local mainCorner = Instance.new("UICorner")
mainCorner.CornerRadius = UDim.new(0, 16)
mainCorner.Parent = main

local mainStroke = Instance.new("UIStroke")
mainStroke.Thickness = 2
mainStroke.Color = Color3.fromRGB(80, 80, 80)
mainStroke.Parent = main

-- Efeito de brilho sutil
local glow = Instance.new("ImageLabel")
glow.Name = "Glow"
glow.Size = UDim2.new(1, 20, 1, 20)
glow.Position = UDim2.new(0, -10, 0, -10)
glow.BackgroundTransparency = 1
glow.Image = "rbxassetid://8992231221"
glow.ImageColor3 = Color3.fromRGB(0, 170, 255)
glow.ScaleType = Enum.ScaleType.Slice
glow.SliceCenter = Rect.new(100, 100, 100, 100)
glow.Parent = main

-- Título estilizado
local titleContainer = Instance.new("Frame")
titleContainer.Size = UDim2.new(1, 0, 0, 60)
titleContainer.BackgroundTransparency = 1
titleContainer.Parent = main

local title = Instance.new("TextLabel")
title.Size = UDim2.new(1, 0, 1, 0)
title.BackgroundTransparency = 1
title.Text = "ULTIMATE BYPASS"
title.TextColor3 = Color3.fromRGB(0, 170, 255)
title.Font = Enum.Font.GothamBlack
title.TextSize = 24
title.TextXAlignment = Enum.TextXAlignment.Center
title.TextYAlignment = Enum.TextYAlignment.Center
title.Parent = titleContainer

local subtitle = Instance.new("TextLabel")
subtitle.Size = UDim2.new(1, 0, 0, 20)
subtitle.Position = UDim2.new(0, 0, 0, 35)
subtitle.BackgroundTransparency = 1
subtitle.Text = "Premium Access System"
subtitle.TextColor3 = Color3.fromRGB(150, 150, 150)
subtitle.Font = Enum.Font.GothamMedium
subtitle.TextSize = 12
subtitle.TextXAlignment = Enum.TextXAlignment.Center
subtitle.Parent = titleContainer

-- Linha decorativa
local line = Instance.new("Frame")
line.Size = UDim2.new(0.7, 0, 0, 1)
line.Position = UDim2.new(0.15, 0, 0, 55)
line.BackgroundColor3 = Color3.fromRGB(0, 170, 255)
line.BorderSizePixel = 0
line.Parent = main

-- Container dos botões
local buttonContainer = Instance.new("Frame")
buttonContainer.Size = UDim2.new(1, 0, 0, 180)
buttonContainer.Position = UDim2.new(0, 0, 0, 80)
buttonContainer.BackgroundTransparency = 1
buttonContainer.Parent = main

-- Botão Get Key (Destaque)
local getBtn = Instance.new("TextButton")
getBtn.Size = UDim2.new(0.8, 0, 0, 50)
getBtn.Position = UDim2.new(0.1, 0, 0.1, 0)
getBtn.Text = "GET KEY"
getBtn.TextColor3 = Color3.fromRGB(255, 255, 255)
getBtn.Font = Enum.Font.GothamBlack
getBtn.TextSize = 18
getBtn.BackgroundColor3 = Color3.fromRGB(0, 100, 255)
getBtn.BorderSizePixel = 0
getBtn.AutoButtonColor = false
getBtn.Parent = buttonContainer

-- Gradiente no botão
local btnGradient = Instance.new("UIGradient")
btnGradient.Color = ColorSequence.new({
    ColorSequenceKeypoint.new(0, Color3.fromRGB(0, 120, 255)),
    ColorSequenceKeypoint.new(1, Color3.fromRGB(0, 80, 200))
})
btnGradient.Parent = getBtn

local btnCorner = Instance.new("UICorner")
btnCorner.CornerRadius = UDim.new(0, 12)
btnCorner.Parent = getBtn

local btnStroke = Instance.new("UIStroke")
btnStroke.Thickness = 2
btnStroke.Color = Color3.fromRGB(100, 180, 255)
btnStroke.Parent = getBtn

-- Ícone no botão
local icon = Instance.new("ImageLabel")
icon.Size = UDim2.new(0, 20, 0, 20)
icon.Position = UDim2.new(0, 15, 0.5, -10)
icon.BackgroundTransparency = 1
icon.Image = "rbxassetid://3926305904"
icon.ImageColor3 = Color3.fromRGB(255, 255, 255)
icon.Parent = getBtn

-- Texto descritivo
local desc = Instance.new("TextLabel")
desc.Size = UDim2.new(0.8, 0, 0, 40)
desc.Position = UDim2.new(0.1, 0, 0.6, 0)
desc.BackgroundTransparency = 1
desc.Text = "Click to copy the premium access link to your clipboard"
desc.TextColor3 = Color3.fromRGB(150, 150, 150)
desc.Font = Enum.Font.Gotham
desc.TextSize = 12
desc.TextWrapped = true
desc.TextXAlignment = Enum.TextXAlignment.Center
desc.Parent = buttonContainer

-- Efeitos de hover no botão
getBtn.MouseEnter:Connect(function()
    TweenService:Create(getBtn, TweenInfo.new(0.3), {BackgroundColor3 = Color3.fromRGB(0, 140, 255)}):Play()
    TweenService:Create(btnStroke, TweenInfo.new(0.3), {Color = Color3.fromRGB(150, 210, 255)}):Play()
end)

getBtn.MouseLeave:Connect(function()
    TweenService:Create(getBtn, TweenInfo.new(0.3), {BackgroundColor3 = Color3.fromRGB(0, 100, 255)}):Play()
    TweenService:Create(btnStroke, TweenInfo.new(0.3), {Color = Color3.fromRGB(100, 180, 255)}):Play()
end)

getBtn.MouseButton1Down:Connect(function()
    TweenService:Create(getBtn, TweenInfo.new(0.1), {Size = UDim2.new(0.78, 0, 0, 48)}):Play()
end)

getBtn.MouseButton1Up:Connect(function()
    TweenService:Create(getBtn, TweenInfo.new(0.1), {Size = UDim2.new(0.8, 0, 0, 50)}):Play()
end)

-- Função de copiar link
local URL = "https://rebrand.ly/get_key"

getBtn.MouseButton1Click:Connect(function()
    if setclipboard then
        setclipboard(URL)
        
        -- Feedback visual
        local originalText = getBtn.Text
        getBtn.Text = "COPIED!"
        
        TweenService:Create(getBtn, TweenInfo.new(0.3), {BackgroundColor3 = Color3.fromRGB(0, 200, 100)}):Play()
        TweenService:Create(btnStroke, TweenInfo.new(0.3), {Color = Color3.fromRGB(100, 255, 150)}):Play()
        
        wait(1.5)
        
        getBtn.Text = originalText
        TweenService:Create(getBtn, TweenInfo.new(0.3), {BackgroundColor3 = Color3.fromRGB(0, 100, 255)}):Play()
        TweenService:Create(btnStroke, TweenInfo.new(0.3), {Color = Color3.fromRGB(100, 180, 255)}):Play()
    else
        -- Fallback para caso setclipboard não exista
        getBtn.Text = "COPY MANUALLY"
        print("Link: " .. URL)
    end
end)

-- Efeito de entrada da UI
main.Size = UDim2.new(0, 0, 0, 0)
main.BackgroundTransparency = 1

TweenService:Create(main, TweenInfo.new(0.8, Enum.EasingStyle.Back, Enum.EasingDirection.Out), {
    Size = UDim2.new(0, 350, 0, 280),
    BackgroundTransparency = 0
}):Play()

TweenService:Create(background, TweenInfo.new(0.5), {
    BackgroundTransparency = 0.4
}):Play()
