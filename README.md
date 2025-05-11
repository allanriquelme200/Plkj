-- HUB para Florianópolis RP (Delta Executor - Roblox) -- Feito por ChatGPT para uso pessoal/testes

-- Serviços local Players = game:GetService("Players") local LocalPlayer = Players.LocalPlayer local RunService = game:GetService("RunService") local Workspace = game:GetService("Workspace") local ReplicatedStorage = game:GetService("ReplicatedStorage")

-- GUI Setup local ScreenGui = Instance.new("ScreenGui", game.CoreGui) ScreenGui.Name = "FloripaRPHub"

local MainFrame = Instance.new("Frame", ScreenGui) MainFrame.Size = UDim2.new(0, 300, 0, 400) MainFrame.Position = UDim2.new(0.5, -150, 0.5, -200) MainFrame.BackgroundColor3 = Color3.fromRGB(20, 20, 20) MainFrame.BorderSizePixel = 0

local UIListLayout = Instance.new("UIListLayout", MainFrame) UIListLayout.Padding = UDim.new(0, 5) UIListLayout.FillDirection = Enum.FillDirection.Vertical UIListLayout.SortOrder = Enum.SortOrder.LayoutOrder

local function createButton(name, callback) local button = Instance.new("TextButton") button.Size = UDim2.new(1, -10, 0, 40) button.Position = UDim2.new(0, 5, 0, 0) button.Text = name button.BackgroundColor3 = Color3.fromRGB(40, 40, 40) button.TextColor3 = Color3.new(1, 1, 1) button.Font = Enum.Font.SourceSansBold button.TextSize = 18 button.MouseButton1Click:Connect(callback) button.Parent = MainFrame return button end

-- Funções RP (exemplos) createButton("Teleport Hospital", function() LocalPlayer.Character:MoveTo(Vector3.new(208, 17, -127)) -- Altere para coords reais do hospital end)

createButton("Teleport Garagem", function() LocalPlayer.Character:MoveTo(Vector3.new(321, 18, 70)) -- Altere para coords reais da garagem end)

createButton("Curar Vida", function() local humanoid = LocalPlayer.Character and LocalPlayer.Character:FindFirstChildOfClass("Humanoid") if humanoid then humanoid.Health = humanoid.MaxHealth end end)

createButton("Remover Trava", function() LocalPlayer.Character.HumanoidRootPart.Anchored = false end)

createButton("Speed x2", function() local hum = LocalPlayer.Character:FindFirstChildOfClass("Humanoid") if hum then hum.WalkSpeed = 32 end end)

createButton("Reset Speed", function() local hum = LocalPlayer.Character:FindFirstChildOfClass("Humanoid") if hum then hum.WalkSpeed = 16 end end)

createButton("Invisibilidade", function() for _, v in ipairs(LocalPlayer.Character:GetDescendants()) do if v:IsA("BasePart") and v.Name ~= "HumanoidRootPart" then v.Transparency = 1 end end end)

createButton("Resetar Char", function() LocalPlayer:LoadCharacter() end)

print("[Floripa RP Hub] Carregado com sucesso.")

