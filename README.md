local Players = game:GetService("Players")
local RunService = game:GetService("RunService")
local Workspace = game:GetService("Workspace")
local Camera = Workspace.CurrentCamera

local LocalPlayer = Players.LocalPlayer
local Mouse = LocalPlayer:GetMouse()

local AimbotEnabled = false
local ESPEnabled = false
local maxDistance = 36

local function IsEnemy(player)
	return player.Team ~= nil and LocalPlayer.Team ~= nil and player.TeamColor ~= LocalPlayer.TeamColor
end

-- GUI
local function SetupGUI()
	local playerGui = LocalPlayer:WaitForChild("PlayerGui")
	if playerGui:FindFirstChild("AimbotESP_GUI") then return end

	local gui = Instance.new("ScreenGui")
	gui.Name = "AimbotESP_GUI"
	gui.ResetOnSpawn = false
	gui.Parent = playerGui

	local aimbotBtn = Instance.new("TextButton")
	aimbotBtn.Size = UDim2.new(0, 120, 0, 40)
	aimbotBtn.Position = UDim2.new(0, 10, 0, 10)
	aimbotBtn.Text = "Aimbot: OFF"
	aimbotBtn.BackgroundColor3 = Color3.fromRGB(255, 0, 0)
	aimbotBtn.Parent = gui

	local espBtn = Instance.new("TextButton")
	espBtn.Size = UDim2.new(0, 120, 0, 40)
	espBtn.Position = UDim2.new(0, 10, 0, 60)
	espBtn.Text = "ESP: OFF"
	espBtn.BackgroundColor3 = Color3.fromRGB(255, 0, 0)
	espBtn.Parent = gui

	aimbotBtn.MouseButton1Click:Connect(function()
		AimbotEnabled = not AimbotEnabled
		aimbotBtn.Text = "Aimbot: " .. (AimbotEnabled and "ON" or "OFF")
		aimbotBtn.BackgroundColor3 = AimbotEnabled and Color3.fromRGB(0, 255, 0) or Color3.fromRGB(255, 0, 0)
	end)

	espBtn.MouseButton1Click:Connect(function()
		ESPEnabled = not ESPEnabled
		espBtn.Text = "ESP: " .. (ESPEnabled and "ON" or "OFF")
		espBtn.BackgroundColor3 = ESPEnabled and Color3.fromRGB(0, 255, 0) or Color3.fromRGB(255, 0, 0)
	end)
end

SetupGUI()
LocalPlayer.CharacterAdded:Connect(function()
	task.wait(1)
	SetupGUI()
end)

-- ESP
local espObjects = {}

local function CreateESP(player)
	local box = Drawing.new("Square")
	box.Thickness = 1.5
	box.Filled = false
	box.Visible = false

	local name = Drawing.new("Text")
	name.Size = 14
	name.Center = true
	name.Outline = true
	name.Visible = false

	espObjects[player] = {Box = box, Name = name}
end

local function RemoveESP(player)
	if espObjects[player] then
		for _, obj in pairs(espObjects[player]) do
			obj:Remove()
		end
		espObjects[player] = nil
	end
end

for _, p in pairs(Players:GetPlayers()) do
	if p ~= LocalPlayer then
		CreateESP(p)
	end
end

Players.PlayerAdded:Connect(function(p)
	if p ~= LocalPlayer then
		CreateESP(p)
	end
end)

Players.PlayerRemoving:Connect(RemoveESP)

-- Raycast Visibilidade
local rayParams = RaycastParams.new()
rayParams.FilterType = Enum.RaycastFilterType.Blacklist
rayParams.IgnoreWater = true

local function IsVisible(part)
	if not part then return false end
	local origin = Camera.CFrame.Position
	local dir = (part.Position - origin)
	rayParams.FilterDescendantsInstances = {LocalPlayer.Character}
	local result = Workspace:Raycast(origin, dir, rayParams)
	return not result or result.Instance:IsDescendantOf(part.Parent)
end

-- Loop principal
RunService.RenderStepped:Connect(function()
	local closest = nil
	local shortest = math.huge

	for _, player in ipairs(Players:GetPlayers()) do
		if player ~= LocalPlayer and player.Character and player.Character:FindFirstChild("Head") and player.Character:FindFirstChild("HumanoidRootPart") and IsEnemy(player) then
			local head = player.Character.Head
			local hrp = player.Character.HumanoidRootPart

			local distance = (hrp.Position - LocalPlayer.Character.HumanoidRootPart.Position).Magnitude
			local visible = IsVisible(head)

			if ESPEnabled then
				local screenPos, onScreen = Camera:WorldToViewportPoint(hrp.Position)
				local esp = espObjects[player]
				if onScreen and esp then
					local headPos = Camera:WorldToViewportPoint(head.Position + Vector3.new(0, 0.5, 0))
					local footPos = Camera:WorldToViewportPoint(hrp.Position - Vector3.new(0, 3, 0))
					local height = math.abs(footPos.Y - headPos.Y)
					local width = height / 2

					esp.Box.Size = Vector2.new(width, height)
					esp.Box.Position = Vector2.new(screenPos.X - width / 2, screenPos.Y - height / 2)
					esp.Box.Visible = true
					esp.Box.Color = visible and Color3.fromRGB(0, 255, 0) or Color3.fromRGB(255, 0, 0)

					esp.Name.Text = player.Name
					esp.Name.Position = Vector2.new(screenPos.X, screenPos.Y - height / 2 - 15)
					esp.Name.Color = esp.Box.Color
					esp.Name.Visible = true
				else
					if esp then
						esp.Box.Visible = false
						esp.Name.Visible = false
					end
				end
			end

			if AimbotEnabled and distance <= maxDistance and visible then
				local screenPos = Camera:WorldToViewportPoint(head.Position)
				local mouseDist = (Vector2.new(screenPos.X, screenPos.Y) - Vector2.new(Mouse.X, Mouse.Y)).Magnitude
				if mouseDist < shortest then
					shortest = mouseDist
					closest = head
				end
			end
