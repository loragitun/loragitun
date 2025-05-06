-- // Dead Rails Script by Lora
-- Fly + ESP + NoClip + Aimbot + Bring Parts

local Players = game:GetService("Players")
local LocalPlayer = Players.LocalPlayer
local Camera = workspace.CurrentCamera
local RunService = game:GetService("RunService")
local UIS = game:GetService("UserInputService")

-- // FLY
local flying = false
local flySpeed = 60
local BodyGyro, BodyVelocity

function startFly()
    local char = LocalPlayer.Character
    if not char then return end
    BodyGyro = Instance.new("BodyGyro", char.HumanoidRootPart)
    BodyVelocity = Instance.new("BodyVelocity", char.HumanoidRootPart)
    BodyGyro.P = 9e4
    BodyGyro.MaxTorque = Vector3.new(9e9, 9e9, 9e9)
    BodyVelocity.MaxForce = Vector3.new(9e9, 9e9, 9e9)
    flying = true
end

function stopFly()
    flying = false
    if BodyGyro then BodyGyro:Destroy() end
    if BodyVelocity then BodyVelocity:Destroy() end
end

UIS.InputBegan:Connect(function(input)
    if input.KeyCode == Enum.KeyCode.F then
        if flying then stopFly() else startFly() end
    end
end)

RunService.RenderStepped:Connect(function()
    if flying and LocalPlayer.Character and LocalPlayer.Character:FindFirstChild("HumanoidRootPart") then
        local dir = Vector3.zero
        if UIS:IsKeyDown(Enum.KeyCode.W) then dir = dir + Camera.CFrame.LookVector end
        if UIS:IsKeyDown(Enum.KeyCode.S) then dir = dir - Camera.CFrame.LookVector end
        if UIS:IsKeyDown(Enum.KeyCode.A) then dir = dir - Camera.CFrame.RightVector end
        if UIS:IsKeyDown(Enum.KeyCode.D) then dir = dir + Camera.CFrame.RightVector end
        BodyVelocity.Velocity = dir * flySpeed
        BodyGyro.CFrame = Camera.CFrame
    end
end)

-- // ESP
for _, v in pairs(Players:GetPlayers()) do
    if v ~= LocalPlayer then
        local box = Instance.new("BoxHandleAdornment")
        box.Name = "ESPBox"
        box.Size = Vector3.new(2, 3, 1)
        box.Adornee = v.Character and v.Character:FindFirstChild("HumanoidRootPart
