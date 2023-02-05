getgenv().SecureMode = true 

local Rayfield = loadstring(game:HttpGet('https://raw.githubusercontent.com/shlexware/Rayfield/main/source'))()
local UIS = game:GetService("UserInputService")

local tweenService = game:GetService("TweenService")
local tweenInfo = TweenInfo.new(0.25)

local Window = Rayfield:CreateWindow({
   Name = "FuckBitchHub",
   LoadingTitle = "FuckBitchHub",
   LoadingSubtitle = "by cl4ad",
   ConfigurationSaving = {
      Enabled = true,
      FolderName = nil, -- Create a custom folder for your hub/game
      FileName = "FuckBitchHub"
   },
   KeySystem = true, -- Set this to true to use our key system
   KeySettings = {
      Title = "FuckBitchHub",
      Subtitle = "Key System",
      Note = "Exploiting is the best way to play ROBLOX",
      FileName = "SiriusKey",
      SaveKey = true,
      GrabKeyFromSite = false, -- If this is true, set Key below to the RAW site you would like Rayfield to get the key from
      Key = "ELCPXjvL1AuTajCzfiQ3mtvl4J49nejy"
   }
})

local Tab = Window:CreateTab("Coolio", 4483362458) -- Title, Image
local Section = Tab:CreateSection("Murder Mystery 2")

local Button = Tab:CreateButton({
   Name = "TP to Gun, (only works if gun is dropped)",
   Callback = function()
    local gunTween = tweenService:Create(game.Players.LocalPlayer.Character.HumanoidRootPart, TweenInfo.new(1.5, Enum.EasingStyle.Quad, Enum.EasingDirection.Out),{CFrame = workspace.GunDrop.CFrame})
    gunTween:Play()
   end,
})

local Slider = Tab:CreateSlider({
   Name = "Walkspeed",
   Range = {0, 200},
   Increment = 5,
   Suffix = "Walkspeed",
   CurrentValue = 10,
   Flag = "Slider1", -- A flag is the identifier for the configuration file, make sure every element has a different flag if you're using configuration saving to ensure no overlaps
   Callback = function(Value)
        game.Players.LocalPlayer.Character.Humanoid.WalkSpeed = Value

   end,
})

local NewSlider = Tab:CreateSlider({
   Name = "Jump power",
   Range = {0, 200},
   Increment = 5,
   Suffix = "Jump power",
   CurrentValue = 10,
   Flag = "Slider2", -- A flag is the identifier for the configuration file, make sure every element has a different flag if you're using configuration saving to ensure no overlaps
   Callback = function(Value)
        game.Players.LocalPlayer.Character.Humanoid.JumpPower = Value

   end,
})

local Button1 = Tab:CreateButton({
    Name = "Aimbot (Sheriff only)",
    Callback = function()
        local dwCamera = workspace.CurrentCamera
local dwRunService = game:GetService("RunService")
local dwUIS = game:GetService("UserInputService")
local dwEntities = game:GetService("Players")
local dwLocalPlayer = dwEntities.LocalPlayer
local dwMouse = dwLocalPlayer:GetMouse()

local settings = {
    Aimbot = true,
    Aiming = false,
    Aimbot_AimPart = "HumanoidRootPart",
    Aimbot_TeamCheck = false,
    Aimbot_Draw_FOV = true,
    Aimbot_FOV_Radius = 50,
    Aimbot_FOV_Color = Color3.fromRGB(255,255,255)
}

local fovcircle = Drawing.new("Circle")
fovcircle.Visible = settings.Aimbot_Draw_FOV
fovcircle.Radius = settings.Aimbot_FOV_Radius
fovcircle.Color = settings.Aimbot_FOV_Color
fovcircle.Thickness = 1
fovcircle.Filled = false
fovcircle.Transparency = 1

fovcircle.Position = Vector2.new(dwCamera.ViewportSize.X / 2, dwCamera.ViewportSize.Y / 2)

dwUIS.InputBegan:Connect(function(i)
    if i.UserInputType == Enum.UserInputType.MouseButton2 then
        settings.Aiming = true
    end
end)

dwUIS.InputEnded:Connect(function(i)
    if i.UserInputType == Enum.UserInputType.MouseButton2 then
        settings.Aiming = false
    end
end)

dwRunService.RenderStepped:Connect(function()
    
    local dist = math.huge
    local closest_char = nil

    if settings.Aiming then

        for i,v in next, dwEntities:GetChildren() do 

            if v ~= dwLocalPlayer and
            v.Character and
            v.Character:FindFirstChild("HumanoidRootPart") and
            v.Character:FindFirstChild("Humanoid") and
            v.Character:FindFirstChild("Humanoid").Health > 0 then

                if settings.Aimbot_TeamCheck == true and
                v.Team ~= dwLocalPlayer.Team or
                settings.Aimbot_TeamCheck == false then

                    local char = v.Character
                    local char_part_pos, is_onscreen = dwCamera:WorldToViewportPoint(char[settings.Aimbot_AimPart].Position)

                    if is_onscreen then

                        local mag = (Vector2.new(dwMouse.X, dwMouse.Y) - Vector2.new(char_part_pos.X, char_part_pos.Y)).Magnitude

                        if mag < dist and mag < settings.Aimbot_FOV_Radius then

                            dist = mag
                            closest_char = char

                        end
                    end
                end
            end
        end

        if closest_char ~= nil and
        closest_char:FindFirstChild("HumanoidRootPart") and
        closest_char:FindFirstChild("Humanoid") and
        closest_char:FindFirstChild("Humanoid").Health > 0 then

            dwCamera.CFrame = CFrame.new(dwCamera.CFrame.Position, closest_char[settings.Aimbot_AimPart].Position)
        end
    end
end)
    end,
 })

 local Button3 = Tab:CreateButton({
    Name = "Noclip",
    Callback = function()
        local runservice = game:GetService("RunService")

        local player = game:GetService("Players").LocalPlayer
        runservice.Stepped:Connect(function()
            for i,v in pairs(player.Character:GetDescendants()) do
                if v:IsA("BasePart") then
                    v.CanCollide = false
                end
            end
        end)
    end,
 })

 local Button4 = Tab:CreateButton({
    Name = "Teleport to Lobby",
    Callback = function()
      game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-98.9611969, 135.550064, 30.7388039, -0.707134247, 0, -0.707079291, 0, 1, 0, 0.707079291, 0, -0.707134247) + Vector3.new(0, 15, 0)
    end,
 })
 
 Rayfield:LoadConfiguration()
