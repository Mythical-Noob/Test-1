local player = game.Players.LocalPlayer
local mouse = player:GetMouse()
local flying = false
local speed = 50
local bodyVelocity = Instance.new("BodyVelocity")
local bodyGyro = Instance.new("BodyGyro")

mouse.KeyDown:Connect(function(key)
    if key == "f" then
        flying = not flying
        if flying then
            local character = player.Character or player.CharacterAdded:Wait()
            local humanoidRootPart = character:WaitForChild("HumanoidRootPart")
            bodyVelocity.Parent = humanoidRootPart
            bodyVelocity.Velocity = Vector3.new(0, 0, 0)
            bodyVelocity.MaxForce = Vector3.new(4000, 4000, 4000)
            
            bodyGyro.Parent = humanoidRootPart
            bodyGyro.CFrame = humanoidRootPart.CFrame
            bodyGyro.MaxTorque = Vector3.new(4000, 4000, 4000)
            bodyGyro.P = 10000
            
            while flying do
                local direction = Vector3.new(
                    (mouse.Hit.p.x - humanoidRootPart.Position.x),
                    (mouse.Hit.p.y - humanoidRootPart.Position.y),
