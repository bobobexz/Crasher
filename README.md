if game.Players.LocalPlayer:IsInGroup(15442170) then
    game.Players.LocalPlayer.Character.BodyEffects:FindFirstChild("K.O"):Destroy()

    wait()

    XD = 0

    game.RunService.Stepped:Connect(function()
        game.ReplicatedStorage.MainEvent:FireServer("JoinCrew", 15442170)
        game.ReplicatedStorage.MainEvent:FireServer("LeaveCrew")
        game.Players.LocalPlayer.PlayerGui.MainScreenGui.Crew.CrewFrame.Visible = false
        for i,v in pairs(game.Players.LocalPlayer.Backpack:GetChildren()) do
            if v:IsA("Tool") and v.Name == "[SprayCan]" then
                XD = XD + 1
                v.Parent = game.Players.LocalPlayer.Character
            end
        end
        if XD > 1250 then
            for i,v in pairs(game.Players.LocalPlayer.Character:GetChildren()) do
                if v:IsA("BasePart") or v:IsA("Accessory") then
                    v:Destroy()
                end
            end
        end
    end)

    local ScreenGui = Instance.new("ScreenGui")
    local Title = Instance.new("TextLabel")
    local Counter = Instance.new("TextLabel")
    ScreenGui.Parent = game.CoreGui
    ScreenGui.ZIndexBehavior = Enum.ZIndexBehavior.Sibling
    Title.Name = "Title"
    Title.Parent = ScreenGui
    Title.BackgroundColor3 = Color3.fromRGB(39, 40, 60)
    Title.BorderSizePixel = 0
    Title.Position = UDim2.new(0.732716084, 0, 0.2594859, 0)
    Title.Size = UDim2.new(0, 200, 0, 29)
    Title.Font = Enum.Font.FredokaOne
    Title.Text = "Sono's Crash"
    Title.TextColor3 = Color3.fromRGB(255, 255, 255)
    Title.TextSize = 20.000
    Counter.Name = "Counter"
    Counter.Parent = Title
    Counter.BackgroundColor3 = Color3.fromRGB(20, 20, 30)
    Counter.BorderSizePixel = 0
    Counter.Position = UDim2.new(0, 0, 0.998691976, 0)
    Counter.Size = UDim2.new(0, 200, 0, 60)
    Counter.Font = Enum.Font.SourceSansItalic
    Counter.Text = "0/1250"
    Counter.TextColor3 = Color3.fromRGB(255, 255, 255)
    Counter.TextSize = 25.000
    Counter.TextWrapped = true
    Title.Active = true
    Title.Draggable = true
    local function XJXFBO_fake_script() -- Counter.LocalScript 
        local script = Instance.new('LocalScript', Counter)

        game.RunService.Stepped:Connect(function()
            Counter.Text = "Tools: "..XD.."/1250"
        end)
    end
    coroutine.wrap(XJXFBO_fake_script)()
else
    game.StarterGui:SetCore("SendNotification", {
        Title = "Error!",
        Text = "Please Join The Roblox Group For It To Work! Copied Link To Your Clipboard.",
        Duration = 7,
    })

    setclipboard("https://www.roblox.com/groups/15442170/Sono-Da-Hood#!/about")
end
