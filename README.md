-- DownSlam 💬🔥
-- Local Script put inside button 💬📝
-- Made by potato dev 😎👍
-- Like and Subscribe 🥳🥳🥳


local button = script.Parent
local animationId = "rbxassetid://184574340" -- You can use your Animation 📝
local animationSpeed = 3 -- Animation speed 📝
local soundId = "rbxassetid://7128851174" -- You can change the sound id 📝
 
local punchEvent = game.ReplicatedStorage:WaitForChild("PunchEvent")
 
local function playAnimation()
    local player = game.Players.LocalPlayer
    local character = player.Character or player.CharacterAdded:Wait()
    local humanoid = character:FindFirstChildOfClass("Humanoid")
    
    if humanoid then
        local animator = humanoid:FindFirstChildOfClass("Animator") or humanoid:WaitForChild("Animator")
        local animation = Instance.new("Animation")
        animation.AnimationId = animationId
        
        local animationTrack = animator:LoadAnimation(animation)
        animationTrack:Play()
        animationTrack:AdjustSpeed(animationSpeed)
        
        
        local sound = Instance.new("Sound", character)
        sound.SoundId = soundId
        sound:Play()
        sound.Ended:Connect(function()
            sound:Destroy()
        end)
        
       
        punchEvent:FireServer(10, true)
    end
end
 
button.MouseButton1Click:Connect(playAnimation)
