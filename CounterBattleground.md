local screenGui = Instance.new("ScreenGui")
screenGui.Name = "Script"
screenGui.Parent = game.Players.LocalPlayer:WaitForChild("PlayerGui")
screenGui.Enabled = true

local menuFrame = Instance.new("Frame")
menuFrame.Name = "Menu"
menuFrame.Parent = screenGui
menuFrame.Visible = false
menuFrame.Size = UDim2.new(0.511, 0, 0.658, 0)
menuFrame.Position = UDim2.new(0.244, 0, 0.170, 0)
menuFrame.BackgroundColor3 = Color3.new(0.117, 0.117, 0.117)
menuFrame.ZIndex = 1
menuFrame.SizeConstraint = Enum.SizeConstraint.RelativeXY
menuFrame.ClipsDescendants = false

local menuUICorner = Instance.new("UICorner")
menuUICorner.CornerRadius = UDim.new(0, 8)
menuUICorner.Parent = menuFrame

local menuGradient = Instance.new("UIGradient")
menuGradient.Parent = menuFrame
menuGradient.Rotation = -90

local textLabel = Instance.new("TextLabel")
textLabel.Name = "TextLabel"
textLabel.Parent = menuFrame
textLabel.Visible = true
textLabel.Text = "AKZX Hub 0"
textLabel.TextScaled = true
textLabel.BackgroundTransparency = 1
textLabel.Size = UDim2.new(0.67, 0, 0.142, 0)
textLabel.Position = UDim2.new(0.164, 0, -0.085, 0)
textLabel.BackgroundColor3 = Color3.new(1, 1, 1)
textLabel.TextColor3 = Color3.new(1, 1, 1)
textLabel.TextSize = 14
textLabel.TextWrapped = true
textLabel.Font = Enum.Font.SourceSansBold
textLabel.SizeConstraint = Enum.SizeConstraint.RelativeXY
textLabel.ZIndex = 1

local scrollingFrame = Instance.new("ScrollingFrame")
scrollingFrame.Name = "List"
scrollingFrame.Parent = menuFrame
scrollingFrame.Visible = true
scrollingFrame.Size = UDim2.new(1, 0, 0.943, 0)
scrollingFrame.Position = UDim2.new(0, 0, 0.057, 0)
scrollingFrame.BackgroundColor3 = Color3.new(1, 1, 1)
scrollingFrame.BackgroundTransparency = 1
scrollingFrame.ZIndex = 1
scrollingFrame.ClipsDescendants = true
scrollingFrame.CanvasSize = UDim2.new(0, 0, 2, 0)
scrollingFrame.ScrollBarThickness = 12

local listLayout = Instance.new("UIListLayout")
listLayout.Parent = scrollingFrame
listLayout.FillDirection = Enum.FillDirection.Vertical

local iconButton = Instance.new("TextButton")
iconButton.Name = "Icon"
iconButton.Parent = screenGui
iconButton.Visible = true
iconButton.Text = ""
iconButton.Size = UDim2.new(0.119, 0, 0.111, 0)
iconButton.Position = UDim2.new(0, 0, 0.338, 0)
iconButton.BackgroundColor3 = Color3.new(0.117, 0.117, 0.117)
iconButton.TextColor3 = Color3.new(0.105, 0.165, 0.208)
iconButton.TextSize = 8
iconButton.ZIndex = 1
iconButton.Font = Enum.Font.Legacy

local aspectConstraint = Instance.new("UIAspectRatioConstraint")
aspectConstraint.Parent = iconButton
aspectConstraint.AspectRatio = 1

local iconUICorner = Instance.new("UICorner")
iconUICorner.CornerRadius = UDim.new(0, 811)
iconUICorner.Parent = iconButton

local yLabel = Instance.new("TextLabel")
yLabel.Name = "AK"
yLabel.Parent = iconButton
yLabel.Visible = true
yLabel.Text = "AK"
yLabel.TextScaled = true
yLabel.Size = UDim2.new(0.58, 0, 0.832, 0)
yLabel.Position = UDim2.new(0, 0, 0, 0)
yLabel.TextColor3 = Color3.new(1, 1, 1)
yLabel.TextSize = 14
yLabel.Font = Enum.Font.SourceSansBold
yLabel.BackgroundTransparency = 1

local cLabel = Instance.new("TextLabel")
cLabel.Name = "ZX"
cLabel.Parent = iconButton
cLabel.Visible = true
cLabel.Text = "ZX"
cLabel.TextScaled = true
cLabel.Size = UDim2.new(0.58, 0, 0.832, 0)
cLabel.Position = UDim2.new(0.42, 0, 0.168, 0)
cLabel.TextColor3 = Color3.new(1, 1, 1)
cLabel.TextSize = 14
cLabel.Font =Enum.Font.SourceSansBold
cLabel.BackgroundTransparency = 1

local B12 = Instance.new('TextButton', scrollingFrame)
B12.Text = 'Awaken'
B12.TextColor = BrickColor.new('White')
B12.Size = UDim2.new(1, 0,0.1, 0)
B12.BackgroundColor3 = Color3.fromRGB(0,0,0)
B12.BackgroundTransparency = 0.9
B12.TextScaled = true


B12.MouseButton1Click:Connect(function()
	game.ReplicatedStorage.UltActive:FireServer()
end)

local B13 = Instance.new('TextButton', scrollingFrame)
B13.Text = 'Auto Farm Awaken [Off]'
B13.Size = UDim2.new(1, 0,0.1, 0)
B13.BackgroundColor3 = Color3.fromRGB(0,0,0)
B13.BackgroundTransparency = 0.9
B13.TextColor = BrickColor.new('White')
B13.TextScaled = true

local AF = false

B13.MouseButton1Click:Connect(function()
	if AF then
		AF = false
		B13.Text = 'Auto Farm Awaken [Off]'
	else
		AF = true
		B13.Text = 'Auto Farm Awaken [On]'
	end
end)

iconButton.MouseButton1Click:Connect(function()
	menuFrame.Visible = not menuFrame.Visible
end)

local Player = game.Players.LocalPlayer
local Character= Player.Character
local Torso :BasePart = Character.Torso

while true do
	wait()
	if AF then
		Torso.CFrame = workspace.Dummy.Torso.CFrame
		
		for _, Movessets in pairs(Player.Backpack:GetChildren()) do
			if Movessets:IsA('Tool') then
				Movessets.Parent = Character
				if Character.Clique:FindFirstChild('RemoteEvent') then
					Character.Clique.RemoteEvent:FireServer(4, game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame * CFrame.new(0, 0, -3).p)
				end
				
			end
		end
		
	end
end
