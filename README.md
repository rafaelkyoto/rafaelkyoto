local plr = game.Players.LocalPlayer
local gui = Instance.new("ScreenGui", plr.PlayerGui)
gui.Name = "AutoKyotoGUI"


local button = Instance.new("TextButton", gui)
button.Position = UDim2.new(0, 10, 0.1, 0)  -- Position it on the left side of the screen
button.Size = UDim2.new(0, 200, 0, 50)
button.Text = "Auto Kyoto WIP"
button.TextScaled = true
button.BackgroundColor3 = Color3.fromRGB(0, 128, 255)  -- Blue background
button.TextColor3 = Color3.fromRGB(255, 255, 255)  -- White text


local function fireServer(args)
    game:GetService("Players").LocalPlayer.Character.Communicate:FireServer(unpack(args))
end


local function sendKeyEvent(isPressed, key)
    local VIM = game:GetService('VirtualInputManager')
    VIM:SendKeyEvent(isPressed, key, false, game)
end


local function swipeCamera(swipeSpeed)
    local camera = game.Workspace.CurrentCamera
    local originalPosition = camera.CFrame.Position
    local targetPosition = originalPosition + camera.CFrame.RightVector * swipeSpeed
    camera.CFrame = CFrame.new(targetPosition, camera.CFrame.Position + camera.CFrame.LookVector)
end

 
    sendKeyEvent(true, Enum.KeyCode.D)
    
    sendKeyEvent(false, Enum.KeyCode.Q)

    sendKeyEvent(true, Enum.KeyCode.Q)
    
    sendKeyEvent(false, Enum.KeyCode.D)

   
    swipeCamera(13)

   
    wait(0.001)
    local toolArgs1 = {
        [1] = {
            ["Tool"] = game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Flowing Water"),
            ["Goal"] = "Console Move"
        }
    }
    fireServer(toolArgs1)
    wait(2.27)

 
    sendKeyEvent(true, Enum.KeyCode.D)
    
    sendKeyEvent(false, Enum.KeyCode.Q)

    sendKeyEvent(true, Enum.KeyCode.Q)
    
    sendKeyEvent(false, Enum.KeyCode.D)

  
    swipeCamera(10)

 
    local toolArgs2 = {
        [1] = {
            ["Tool"] = game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Lethal Whirlwind Stream"),
            ["Goal"] = "Console Move"
        }
    }
    fireServer(toolArgs2)

 
    wait(1)
    local endArgs = {
        [1] = {
            ["Goal"] = "Auto Use End",
            ["Tool"] = game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Lethal Whirlwind Stream")
        }
    }
    fireServer(endArgs)
end)
