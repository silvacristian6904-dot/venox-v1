--[[

VENOX HUB 😈
QUEM NÃO XITA NÃO BRILHA

]]

local Rayfield = loadstring(game:HttpGet('https://sirius.menu/rayfield'))()

local Players = game:GetService("Players")
local RunService = game:GetService("RunService")
local UserInputService = game:GetService("UserInputService")

local LocalPlayer = Players.LocalPlayer
local Camera = workspace.CurrentCamera

local Window = Rayfield:CreateWindow({
   Name = "VENOX HUB",
   LoadingTitle = "VENOX HUB",
   LoadingSubtitle = "QUEM NÃO XITA NÃO BRILHA 😈",
   ConfigurationSaving = {
      Enabled = false,
   },
   Discord = {
      Enabled = false,
   },
   KeySystem = false,
})

-- TEXTO
local TextLabel = Instance.new("TextLabel")
TextLabel.Parent = game.CoreGui
TextLabel.BackgroundTransparency = 1
TextLabel.Position = UDim2.new(0.67,0,0.75,0)
TextLabel.Size = UDim2.new(0,300,0,80)
TextLabel.Font = Enum.Font.GothamBlack
TextLabel.Text = "QUEM NÃO\nXITA NÃO\nBRILHA!"
TextLabel.TextColor3 = Color3.fromRGB(255,255,255)
TextLabel.TextScaled = true

-- VARIÁVEIS
local Fly = false
local Noclip = false
local ESP = false
local Aimbot = false
local FOV = 200

-- FOV BALL
local Circle = Drawing.new("Circle")
Circle.Visible = true
Circle.Radius = FOV
Circle.Color = Color3.fromRGB(255,0,0)
Circle.Thickness = 2
Circle.Filled = false
Circle.NumSides = 100

-- PLAYER MAIS PRÓXIMO
local function GetClosestPlayer()

    local Closest = nil
    local ShortestDistance = FOV

    for _,v in pairs(Players:GetPlayers()) do

        if v ~= LocalPlayer and v.Character and v.Character:FindFirstChild("Head") then

            local Pos, Visible =
            Camera:WorldToViewportPoint(v.Character.Head.Position)

            if Visible then

                local Distance =
                (Vector2.new(Pos.X,Pos.Y) -
                Vector2.new(Camera.ViewportSize.X/2,
                Camera.ViewportSize.Y/2)).Magnitude

                if Distance < ShortestDistance then
                    Closest = v
                    ShortestDistance = Distance
                end
            end
        end
    end

    return Closest
end

-- AIMBOT LOOP
RunService.RenderStepped:Connect(function()

    Circle.Position = Vector2.new(
        Camera.ViewportSize.X/2,
        Camera.ViewportSize.Y/2
    )

    if Aimbot then

        local Target = GetClosestPlayer()

        if Target and Target.Character and Target.Character:FindFirstChild("Head") then

            Camera.CFrame = CFrame.new(
                Camera.CFrame.Position,
                Target.Character.Head.Position
            )

        end
    end

    if Noclip and LocalPlayer.Character then

        for _,v in pairs(LocalPlayer.Character:GetDescendants()) do
            if v:IsA("BasePart") then
                v.CanCollide = false
            end
        end

    end
end)

-- AIM TAB
local AimTab = Window:CreateTab("AIM", 4483362458)

AimTab:CreateButton({
   Name = "Aimbot GRUDADO",
   Callback = function()

      Aimbot = not Aimbot

      Rayfield:Notify({
         Title = "VENOX HUB",
         Content = "Aimbot: ".. tostring(Aimbot),
         Duration = 3,
      })

   end,
})

AimTab:CreateSlider({
   Name = "FOV",
   Range = {50, 500},
   Increment = 10,
   Suffix = "FOV",
   CurrentValue = 200,
   Callback = function(Value)

      FOV = Value
      Circle.Radius = Value

   end,
})

-- PLAYER TAB
local PlayerTab = Window:CreateTab("PLAYER", 4483362458)

PlayerTab:CreateButton({
   Name = "Speed x120",
   Callback = function()

      LocalPlayer.Character.Humanoid.WalkSpeed = 120

   end,
})

PlayerTab:CreateButton({
   Name = "Reset Speed",
   Callback = function()

      LocalPlayer.Character.Humanoid.WalkSpeed = 16

   end,
})

PlayerTab:CreateButton({
   Name = "Super Jump",
   Callback = function()

      LocalPlayer.Character.Humanoid.JumpPower = 150

   end,
})

PlayerTab:CreateButton({
   Name = "Fly ON/OFF",
   Callback = function()

      Fly = not Fly

      if Fly then

         local BV = Instance.new("BodyVelocity")
         BV.Name = "VenoxFly"
         BV.MaxForce = Vector3.new(100000,100000,100000)
         BV.Velocity = Vector3.new(0,0,0)
         BV.Parent = LocalPlayer.Character.HumanoidRootPart

         repeat
            task.wait()

            BV.Velocity =
            Camera.CFrame.LookVector * 80

         until Fly == false

         BV:Destroy()

      end

   end,
})

-- VISUAL TAB
local VisualTab = Window:CreateTab("VISUAL", 4483362458)

VisualTab:CreateButton({
   Name = "ESP PLAYER",
   Callback = function()

      ESP = not ESP

      for _,v in pairs(Players:GetPlayers()) do

         if v ~= LocalPlayer and v.Character then

            if ESP then

               local Highlight = Instance.new("Highlight")
               Highlight.Name = "VenoxESP"
               Highlight.FillColor = Color3.fromRGB(255,0,0)
               Highlight.Parent = v.Character

            else

               if v.Character:FindFirstChild("VenoxESP") then
                  v.Character.VenoxESP:Destroy()
               end

            end
         end
      end

   end,
})

VisualTab:CreateButton({
   Name = "NoClip ON/OFF",
   Callback = function()

      Noclip = not Noclip

   end,
})

-- FUN TAB
local FunTab = Window:CreateTab("FUN", 4483362458)

FunTab:CreateButton({
   Name = "Fling",
   Callback = function()

      local HRP = LocalPlayer.Character.HumanoidRootPart

      local BV = Instance.new("BodyAngularVelocity")
      BV.AngularVelocity = Vector3.new(0,99999,0)
      BV.MaxTorque = Vector3.new(0,math.huge,0)
      BV.Parent = HRP

      task.wait(5)

      BV:Destroy()

   end,
})

FunTab:CreateButton({
   Name = "Infinite Jump",
   Callback = function()

      local InfiniteJumpEnabled = true

      UserInputService.JumpRequest:Connect(function()

         if InfiniteJumpEnabled then

            LocalPlayer.Character:FindFirstChildOfClass("Humanoid"):ChangeState("Jumping")

         end
      end)

   end,
})

Rayfield:Notify({
   Title = "VENOX HUB",
   Content = "MENU INJETADO 😈",
   Duration = 6,
   Image = 4483362458,
})
