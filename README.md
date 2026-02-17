--REPORT THIS IN https://discord.gg/xgRpn55gmE IF THIS GOT LEAKED WE WILL GIVE U REWARD

local Players = game:GetService("Players")
local TweenService = game:GetService("TweenService")
local RunService = game:GetService("RunService")
local UserInputService = game:GetService("UserInputService")
local ProximityPromptService = game:GetService("ProximityPromptService")
local TextChatService = game:GetService("TextChatService")
local CoreGui = game:GetService("CoreGui")

local player = Players.LocalPlayer


local pos1 = Vector3.new(-352.98, -7, 74.30)            
local pos2 = Vector3.new(-352.98, -6.49, 45.76)   
local standing1 = Vector3.new(-336.36, -4.59, 99.51)
local standing2 = Vector3.new(-334.81, -4.59, 18.90)


local spot1_sequence = {
    CFrame.new(-370.810913, -7.00000334, 41.2687263, 0.99984771, 1.22364419e-09, 0.0174523517, -6.54859778e-10, 1, -3.2596418e-08, -0.0174523517, 3.25800258e-08, 0.99984771),
    CFrame.new(-336.355286, -5.10107088, 17.2327671, -0.999883354, -2.76150569e-08, 0.0152716246, -2.88224964e-08, 1, -7.88441525e-08, -0.0152716246, -7.9275118e-08, -0.999883354)
}

local spot2_sequence = {
    CFrame.new(-354.782867, -7.00000334, 92.8209305, -0.999997616, -1.11891862e-09, -0.00218066527, -1.11958298e-09, 1, 3.03415071e-10, 0.00218066527, 3.05855785e-10, -0.999997616),
    CFrame.new(-336.942902, -5.10106993, 99.3276443, 0.999914348, -3.63984611e-08, 0.0130875716, 3.67094941e-08, 1, -2.35254749e-08, -0.0130875716, 2.40038975e-08, 0.999914348)
}

if CoreGui:FindFirstChild("AriesHubGui") then 
    CoreGui["AriesHubGui"]:Destroy() 
end

if CoreGui:FindFirstChild("AdminSpammerGui") then 
    CoreGui["AdminSpammerGui"]:Destroy() 
end

-- ========== GUI MDB HALF TP ==========
local screenGui = Instance.new("ScreenGui")
screenGui.Name = "AriesHubGui"
screenGui.ResetOnSpawn = false
screenGui.Parent = CoreGui


local function createESPBox(position, labelText)
    local espFolder = Instance.new("Folder")
    espFolder.Name = "ESPBox_" .. labelText
    espFolder.Parent = workspace
    
    local box = Instance.new("Part")
    box.Name = "ESPPart"
    box.Size = Vector3.new(5, 0.5, 5)
    box.Position = position
    box.Anchored = true
    box.CanCollide = false
    box.Transparency = 0.5
    box.Material = Enum.Material.Neon
    box.Color = Color3.fromRGB(0, 0, 0)
    box.Parent = espFolder
    
    local selectionBox = Instance.new("SelectionBox")
    selectionBox.Adornee = box
    selectionBox.LineThickness = 0.05
    selectionBox.Color3 = Color3.fromRGB(255, 255, 255)
    selectionBox.Parent = box
    
    local billboard = Instance.new("BillboardGui")
    billboard.Name = "ESPLabel"
    billboard.Adornee = box
    billboard.Size = UDim2.new(0, 150, 0, 40)
    billboard.StudsOffset = Vector3.new(0, 2, 0)
    billboard.AlwaysOnTop = true
    billboard.Parent = box
    
    local textLabel = Instance.new("TextLabel")
    textLabel.Size = UDim2.new(1, 0, 1, 0)
    textLabel.BackgroundTransparency = 1
    textLabel.Text = labelText
    textLabel.TextColor3 = Color3.fromRGB(255, 255, 255)
    textLabel.TextSize = 18
    textLabel.Font = Enum.Font.GothamBold
    textLabel.TextStrokeTransparency = 0.5
    textLabel.TextStrokeColor3 = Color3.fromRGB(0, 0, 0)
    textLabel.Parent = billboard
    
    return espFolder
end

createESPBox(pos1, "Teleport Here")
createESPBox(pos2, "Teleport Here")
createESPBox(standing1, "Standing 1")
createESPBox(standing2, "Standing 2")


local autoSemiTpCFrame = CFrame.new(-349.325867, -7.00000238, 95.0031433, -0.999048233, -8.29406233e-09, -0.0436184891, -1.03892832e-08, 1, 4.78084594e-08, 0.0436184891, 4.82161227e-08, -0.999048233)
createESPBox(autoSemiTpCFrame.Position, "TP DIREITO")

local autoSemiTpCFrame = CFrame.new(-349.560211, -7.00000238, 27.0543289, -0.999961913, 5.50995267e-08, -0.00872585084, 5.48100907e-08, 1, 3.34090586e-08, 0.00872585084, 3.29295204e-08, -0.999961913)
createESPBox(autoSemiTpCFrame.Position, "TP ESQUERDO")



local mainFrame = Instance.new("Frame")
mainFrame.Name = "MainFrame"
mainFrame.Size = UDim2.new(0, 200, 0, 320) 
mainFrame.Position = UDim2.new(1, -220, 0.5, -160)
mainFrame.AnchorPoint = Vector2.new(0, 0.5)
mainFrame.BackgroundColor3 = Color3.fromRGB(15, 25, 45)
mainFrame.BackgroundTransparency = 0.1
mainFrame.BorderSizePixel = 0
mainFrame.Active = true
mainFrame.ClipsDescendants = false
mainFrame.Parent = screenGui

Instance.new("UICorner", mainFrame).CornerRadius = UDim.new(0, 10)

local uiStroke = Instance.new("UIStroke", mainFrame)
uiStroke.Thickness = 2
uiStroke.Color = Color3.fromRGB(70, 130, 200)
uiStroke.Transparency = 0.3

local title = Instance.new("TextLabel")
title.Size = UDim2.new(1, 0, 0, 35)
title.Position = UDim2.new(0, 0, 0, 0)
title.BackgroundColor3 = Color3.fromRGB(25, 45, 80)
title.BackgroundTransparency = 0.2
title.Text = "MDB"
title.TextColor3 = Color3.fromRGB(100, 180, 255)
title.TextSize = 18
title.Font = Enum.Font.GothamBold
title.Parent = mainFrame
Instance.new("UICorner", title).CornerRadius = UDim.new(0, 8)

local semiTPEnabled = false
local SPEED_BOOST = 28

-- ✅ ANTI RAGDOLL VARS - JÁ ATIVADO
local AntiRagdollEnabled = true
local antiRagdollConnection = nil
local keysPressed = {W=false,A=false,S=false,D=false,Space=false}
local lastSafePos = nil
local lastSafeTime = 0

local function isBadState(state)
    return state == Enum.HumanoidStateType.Ragdoll
        or state == Enum.HumanoidStateType.Physics
        or state == Enum.HumanoidStateType.FallingDown
        or state == Enum.HumanoidStateType.PlatformStanding
end

local function removeRagdollInstant()
    player:SetAttribute("RagdollEndTime", 0)

    local char = player.Character
    if not char then return end
    local humanoid = char:FindFirstChildOfClass("Humanoid")
    if humanoid then
        humanoid.PlatformStand = false
        humanoid:ChangeState(Enum.HumanoidStateType.GettingUp)
        task.wait()
        humanoid:ChangeState(Enum.HumanoidStateType.Running)
    end

    local camera = workspace.CurrentCamera
    if camera and humanoid and camera.CameraSubject ~= humanoid then
        camera.CameraSubject = humanoid
        camera.CameraType = Enum.CameraType.Custom
    end
end

local function startAntiRagdoll()
    if antiRagdollConnection then return end

    antiRagdollConnection = RunService.Heartbeat:Connect(function()
        if not AntiRagdollEnabled then return end

        local char = player.Character
        if not char then return end

        local humanoid = char:FindFirstChildOfClass("Humanoid")
        local root = char:FindFirstChild("HumanoidRootPart")
        if not humanoid or not root then return end

        local state = humanoid:GetState()
        local vel = root.AssemblyLinearVelocity

        if humanoid.FloorMaterial ~= Enum.Material.Air
            and not isBadState(state)
            and vel.Magnitude < 25
            and tick() - lastSafeTime > 0.4 then

            lastSafePos = Vector3.new(root.Position.X, 0, root.Position.Z)
            lastSafeTime = tick()
        end

        if isBadState(state) then
            removeRagdollInstant()

            for _, m in char:GetDescendants() do
                if m:IsA("Motor6D") and not m.Enabled then
                    m.Enabled = true
                end
            end
        end

        if isBadState(state) and lastSafePos and vel.Magnitude > 40 then
            local y = root.Position.Y
            root.CFrame = CFrame.new(lastSafePos.X, y, lastSafePos.Z)
            local newY = math.abs(vel.Y) > 40 and 0 or vel.Y
            root.AssemblyLinearVelocity = Vector3.new(0, newY, 0)
            root.AssemblyAngularVelocity = Vector3.zero
        end

        humanoid.PlatformStand = false
        humanoid.Sit = false

        local move = Vector3.new()
        if keysPressed.W then move += Vector3.new(0,0,-1) end
        if keysPressed.S then move += Vector3.new(0,0,1) end
        if keysPressed.A then move += Vector3.new(-1,0,0) end
        if keysPressed.D then move += Vector3.new(1,0,0) end

        if move.Magnitude > 0 then
            humanoid:Move(move.Unit, true)
        else
            humanoid:Move(Vector3.zero)
        end

        humanoid.Jump = keysPressed.Space

        if root.AssemblyAngularVelocity.Magnitude > 5 then
            root.AssemblyAngularVelocity = Vector3.new(0, root.AssemblyAngularVelocity.Y, 0)
        end
    end)
end

local function stopAntiRagdoll()
    if antiRagdollConnection then
        antiRagdollConnection:Disconnect()
        antiRagdollConnection = nil
    end
end


local function ResetToWork()
    local flags = {
        {"GameNetPVHeaderRotationalVelocityZeroCutoffExponent", "-5000"},
        {"LargeReplicatorWrite5", "true"},
        {"LargeReplicatorEnabled9", "true"},
        {"AngularVelociryLimit", "360"},
        {"TimestepArbiterVelocityCriteriaThresholdTwoDt", "2147483646"},
        {"S2PhysicsSenderRate", "15000"},
        {"DisableDPIScale", "true"},
        {"MaxDataPacketPerSend", "2147483647"},
        {"ServerMaxBandwith", "52"},
        {"PhysicsSenderMaxBandwidthBps", "20000"},
        {"MaxTimestepMultiplierBuoyancy", "2147483647"},
        {"SimOwnedNOUCountThresholdMillionth", "2147483647"},
        {"MaxMissedWorldStepsRemembered", "-2147483648"},
        {"CheckPVDifferencesForInterpolationMinVelThresholdStudsPerSecHundredth", "1"},
        {"StreamJobNOUVolumeLengthCap", "2147483647"},
        {"DebugSendDistInSteps", "-2147483648"},
        {"MaxTimestepMultiplierAcceleration", "2147483647"},
        {"LargeReplicatorRead5", "true"},
        {"SimExplicitlyCappedTimestepMultiplier", "2147483646"},
        {"GameNetDontSendRedundantNumTimes", "1"},
        {"CheckPVLinearVelocityIntegrateVsDeltaPositionThresholdPercent", "1"},
        {"CheckPVCachedRotVelThresholdPercent", "10"},
        {"LargeReplicatorSerializeRead3", "true"},
        {"ReplicationFocusNouExtentsSizeCutoffForPauseStuds", "2147483647"},
        {"NextGenReplicatorEnabledWrite4", "true"},
        {"CheckPVDifferencesForInterpolationMinRotVelThresholdRadsPerSecHundredth", "1"},
        {"GameNetDontSendRedundantDeltaPositionMillionth", "1"},
        {"InterpolationFrameVelocityThresholdMillionth", "5"},
        {"StreamJobNOUVolumeCap", "2147483647"},
        {"InterpolationFrameRotVelocityThresholdMillionth", "5"},
        {"WorldStepMax", "30"},
        {"TimestepArbiterHumanoidLinearVelThreshold", "1"},
        {"InterpolationFramePositionThresholdMillionth", "5"},
        {"TimestepArbiterHumanoidTurningVelThreshold", "1"},
        {"MaxTimestepMultiplierContstraint", "2147483647"},
        {"GameNetPVHeaderLinearVelocityZeroCutoffExponent", "-5000"},
        {"CheckPVCachedVelThresholdPercent", "10"},
        {"TimestepArbiterOmegaThou", "1073741823"},
        {"MaxAcceptableUpdateDelay", "1"},
        {"LargeReplicatorSerializeWrite4", "true"},
    }
    for _, data in ipairs(flags) do
        pcall(function() if setfflag then setfflag(data[1], data[2]) end end)
    end
    local char = player.Character
    if char then
        local hum = char:FindFirstChildOfClass("Humanoid")
        if hum then hum:ChangeState(Enum.HumanoidStateType.Dead) end
        char:ClearAllChildren()
        local f = Instance.new("Model", workspace)
        player.Character = f task.wait()
        player.Character = char f:Destroy()
    end
end


local function createToggle(text, position, callback, startActive)
    local container = Instance.new("Frame")
    container.Size = UDim2.new(0.9, 0, 0, 28)
    container.Position = position
    container.BackgroundTransparency = 1
    container.Parent = mainFrame

    local label = Instance.new("TextLabel")
    label.Size = UDim2.new(1, -40, 1, 0)
    label.BackgroundTransparency = 1
    label.Text = text
    label.TextColor3 = Color3.fromRGB(180, 200, 220)
    label.TextSize = 13
    label.Font = Enum.Font.Gotham
    label.TextXAlignment = Enum.TextXAlignment.Left
    label.Parent = container

    local btn = Instance.new("TextButton")
    btn.Size = UDim2.new(0, 35, 0, 18)
    btn.Position = UDim2.new(1, -35, 0.5, -9)
    btn.BackgroundColor3 = Color3.fromRGB(40, 60, 90)
    btn.Text = ""
    btn.Parent = container
    Instance.new("UICorner", btn).CornerRadius = UDim.new(1, 0)

    local stroke = Instance.new("UIStroke", btn)
    stroke.Color = Color3.fromRGB(70, 120, 170)
    stroke.Thickness = 0.8

    local dot = Instance.new("Frame")
    dot.Size = UDim2.new(0, 12, 0, 12)
    dot.Position = UDim2.new(0, 2, 0.5, -6)
    dot.BackgroundColor3 = Color3.fromRGB(100, 150, 200)
    dot.Parent = btn
    Instance.new("UICorner", dot).CornerRadius = UDim.new(1, 0)

    local active = startActive or false
    
    if active then
        dot.Position = UDim2.new(1, -14, 0.5, -6)
        dot.BackgroundColor3 = Color3.fromRGB(70, 150, 220)
        btn.BackgroundColor3 = Color3.fromRGB(50, 80, 120)
    end
    
    btn.MouseButton1Click:Connect(function()
        active = not active
        local goal = active and UDim2.new(1, -14, 0.5, -6) or UDim2.new(0, 2, 0.5, -6)
        local col = active and Color3.fromRGB(70, 150, 220) or Color3.fromRGB(100, 150, 200)
        TweenService:Create(dot, TweenInfo.new(0.2), {Position = goal, BackgroundColor3 = col}):Play()
        TweenService:Create(btn, TweenInfo.new(0.2), {BackgroundColor3 = active and Color3.fromRGB(50, 80, 120) or Color3.fromRGB(40, 60, 90)}):Play()
        callback(active)
    end)
end

createToggle("Half TP", UDim2.new(0.05, 0, 0, 40), function(state) semiTPEnabled = state end, false)

createToggle("Auto Potion", UDim2.new(0.05, 0, 0, 72), function(state)
    _G.AutoPotion = state
end, false)

createToggle("Anti Ragdoll", UDim2.new(0.05, 0, 0, 104), function(state)
    AntiRagdollEnabled = state
    if state then
        startAntiRagdoll()
        removeRagdollInstant()
    else
        stopAntiRagdoll()
    end
end, true)

createToggle("Speed Boost", UDim2.new(0.05, 0, 0, 136), function(state)
    speedEnabled = state
    if state then
        startSpeedWASD()
    else
        stopSpeedWASD()
    end
end, true)

-- ATIVAR ANTI RAGDOLL IMEDIATAMENTE
task.spawn(function()
    task.wait(0.5)
    startAntiRagdoll()
    removeRagdollInstant()
    ResetToWork()
end)


local currentEquipTask = nil
local isHolding = false

ProximityPromptService.PromptButtonHoldBegan:Connect(function(prompt, plr)
    if plr ~= player or not semiTPEnabled then return end
    isHolding = true
    if currentEquipTask then task.cancel(currentEquipTask) end
    
    currentEquipTask = task.spawn(function()
        task.wait(1)
        if isHolding and semiTPEnabled then
            local backpack = player:WaitForChild("Backpack", 2)
            if backpack then
                local carpet = backpack:FindFirstChild("Flying Carpet")
                if carpet and player.Character and player.Character:FindFirstChild("Humanoid") then 
                    player.Character.Humanoid:EquipTool(carpet) 
                end
            end
        end
    end)
end)

ProximityPromptService.PromptButtonHoldEnded:Connect(function(prompt, plr)
    if plr ~= player then return end
    isHolding = false
    if currentEquipTask then task.cancel(currentEquipTask) end
end)

ProximityPromptService.PromptTriggered:Connect(function(prompt, plr)
    if plr ~= player or not semiTPEnabled then return end

    local root = player.Character and player.Character:FindFirstChild("HumanoidRootPart")
    if root then
        local d1 = (root.Position - pos1).Magnitude
        local d2 = (root.Position - pos2).Magnitude
        local targetPos = d1 < d2 and pos1 or pos2
        root.CFrame = CFrame.new(targetPos)

        if _G.AutoPotion then
            task.wait(0.2)
            local backpack = player:FindFirstChild("Backpack")
            if backpack then
                local potion = backpack:FindFirstChild("Giant Potion")
                if potion and player.Character and player.Character:FindFirstChild("Humanoid") then
                    player.Character.Humanoid:EquipTool(potion)
                    task.wait(0.2)
                    pcall(function()
                        potion:Activate()
                    end)
                end
            end
        end
    end
    isHolding = false
end)


local dragging, dragStart, startPos
mainFrame.InputBegan:Connect(function(input)
    if input.UserInputType == Enum.UserInputType.MouseButton1 or input.UserInputType == Enum.UserInputType.Touch then
        dragging = true
        dragStart = input.Position
        startPos = mainFrame.Position
    end
end)

UserInputService.InputChanged:Connect(function(input)
    if dragging and (input.UserInputType == Enum.UserInputType.MouseMovement or input.UserInputType == Enum.UserInputType.Touch) then
        local delta = input.Position - dragStart
        mainFrame.Position = UDim2.new(startPos.X.Scale, startPos.X.Offset + delta.X, startPos.Y.Scale, startPos.Y.Offset + delta.Y)
    end
end)

UserInputService.InputEnded:Connect(function(input)
    if input.UserInputType == Enum.UserInputType.MouseButton1 or input.UserInputType == Enum.UserInputType.Touch then
        dragging = false
    end
end)


local CONFIG = {
    ANTI_STEAL_ACTIVE = false,
}

local ReplicatedStorage = game:GetService("ReplicatedStorage")
local AnimalsData = pcall(function() return require(ReplicatedStorage:WaitForChild("Datas"):WaitForChild("Animals")) end) and require(ReplicatedStorage:WaitForChild("Datas"):WaitForChild("Animals")) or {}


local allAnimalsCache = {}
local PromptMemoryCache = {}
local InternalStealCache = {}

local IsStealing = false
local StealProgress = 0
local CurrentStealTarget = nil

local AUTO_STEAL_PROX_RADIUS = 200


local function getHRP()
    local char = player.Character
    if not char then return nil end
    return char:FindFirstChild("HumanoidRootPart") or char:FindFirstChild("UpperTorso")
end

local function isMyBase(plotName)
    local plots = workspace:FindFirstChild("Plots")
    if not plots then return false end
    local plot = plots:FindFirstChild(plotName)
    if not plot then return false end
    local sign = plot:FindFirstChild("PlotSign")
    if not sign then return false end
    local yourBase = sign:FindFirstChild("YourBase")
    return yourBase and yourBase.Enabled or false
end


local function scanSinglePlot(plot)
    if not plot or not plot:IsA("Model") or isMyBase(plot.Name) then return end
    local podiums = plot:FindFirstChild("AnimalPodiums")
    if not podiums then return end

    for _, podium in ipairs(podiums:GetChildren()) do
        if podium:IsA("Model") and podium:FindFirstChild("Base") then
            table.insert(allAnimalsCache, {
                plot = plot.Name,
                slot = podium.Name,
                worldPosition = podium:GetPivot().Position,
                uid = plot.Name .. "_" .. podium.Name,
            })
        end
    end
end

local function initializeScanner()
    task.wait(2)
    local plots = workspace:WaitForChild("Plots", 10)
    if not plots then return end

    for _, plot in ipairs(plots:GetChildren()) do
        scanSinglePlot(plot)
    end

    plots.ChildAdded:Connect(scanSinglePlot)

    task.spawn(function()
        while task.wait(5) do
            table.clear(allAnimalsCache)
            for _, plot in ipairs(plots:GetChildren()) do
                scanSinglePlot(plot)
            end
        end
    end)
end


local function findPrompt(animal)
    local cached = PromptMemoryCache[animal.uid]
    if cached and cached.Parent then return cached end

    local plots = workspace:FindFirstChild("Plots")
    if not plots then return nil end
    
    local plot = plots:FindFirstChild(animal.plot)
    if not plot then return nil end
    
    local podiums = plot:FindFirstChild("AnimalPodiums")
    if not podiums then return nil end
    
    local podium = podiums:FindFirstChild(animal.slot)
    if not podium then return nil end
    
    local base = podium:FindFirstChild("Base")
    if not base then return nil end
    
    local spawn = base:FindFirstChild("Spawn")
    if not spawn then return nil end
    
    local attach = spawn:FindFirstChild("PromptAttachment")
    if not attach then return nil end
    
    local prompt = attach:FindFirstChildOfClass("ProximityPrompt")

    if prompt then
        PromptMemoryCache[animal.uid] = prompt
    end

    return prompt
end

local function buildStealCallbacks(prompt)
    if InternalStealCache[prompt] then return end

    local data = { holdCallbacks = {}, triggerCallbacks = {}, ready = true }

    local ok1, conns1 = pcall(getconnections, prompt.PromptButtonHoldBegan)
    if ok1 and conns1 then
        for _, c in ipairs(conns1) do
            if c.Function then table.insert(data.holdCallbacks, c.Function) end
        end
    end

    local ok2, conns2 = pcall(getconnections, prompt.Triggered)
    if ok2 and conns2 then
        for _, c in ipairs(conns2) do
            if c.Function then table.insert(data.triggerCallbacks, c.Function) end
        end
    end

    InternalStealCache[prompt] = data
end

-- ✅ EXECUTA AUTO STEAL E TELEPORTA AOS 88%
local function executeInternalStealAsync(prompt, animalData, useSpot)
    local data = InternalStealCache[prompt]
    if not data or not data.ready or IsStealing then return false end

    data.ready = false
    IsStealing = true
    StealProgress = 0
    CurrentStealTarget = animalData

    local tpDone = false
    local sequence = useSpot == 2 and spot2_sequence or spot1_sequence

    task.spawn(function()
        for _, fn in ipairs(data.holdCallbacks) do
            task.spawn(fn)
        end

        local startTime = tick()
        while tick() - startTime < 1.3 do
            StealProgress = (tick() - startTime) / 1.3

            -- ✅ TELEPORTA AOS 88%
            if StealProgress >= 0.88 and not tpDone then
                tpDone = true
                local hrp = getHRP()
                if hrp then
                    local char = player.Character
                    local hum = char and char:FindFirstChildOfClass("Humanoid")
                    local backpack = player:FindFirstChild("Backpack")
                    
                    if hum and backpack then
                        local carpet = backpack:FindFirstChild("Flying Carpet")
                        if carpet then
                            hum:EquipTool(carpet)
                            task.wait(0.2)
                        end
                    end

                    hrp.CFrame = sequence[1]
                    task.wait(0.1)
                    hrp.CFrame = sequence[2]
                    task.wait(0.2)

                    local d1 = (hrp.Position - pos1).Magnitude
                    local d2 = (hrp.Position - pos2).Magnitude
                    hrp.CFrame = CFrame.new(d1 < d2 and pos1 or pos2)
                    
                    if _G.AutoPotion then
                        task.wait(0.2)
                        local backpack2 = player:FindFirstChild("Backpack")
                        if backpack2 then
                            local potion = backpack2:FindFirstChild("Giant Potion")
                            if potion and player.Character and player.Character:FindFirstChild("Humanoid") then
                                player.Character.Humanoid:EquipTool(potion)
                                task.wait(0.2)
                                pcall(function()
                                    potion:Activate()
                                end)
                            end
                        end
                    end
                end
            end

            task.wait()
        end

        StealProgress = 1
        for _, fn in ipairs(data.triggerCallbacks) do
            task.spawn(fn)
        end

        task.wait(0.2)
        data.ready = true

        IsStealing = false
        StealProgress = 0
        CurrentStealTarget = nil
        CONFIG.ANTI_STEAL_ACTIVE = false
    end)
    
    return true
end

local function getNearestAnimal()
    local hrp = getHRP()
    if not hrp then return nil end

    local nearest, dist = nil, math.huge
    for _, animal in ipairs(allAnimalsCache) do
        local d = (hrp.Position - animal.worldPosition).Magnitude
        if d < dist and d <= AUTO_STEAL_PROX_RADIUS then
            dist = d
            nearest = animal
        end
    end
    return nearest
end




-- ✅ BOTÃO TP DIREITO - INICIA AUTO STEAL
local antiStealButton = Instance.new("TextButton", mainFrame)
antiStealButton.Name = "AntiStealButton"
antiStealButton.Size = UDim2.new(0.45, 0, 0, 32)
antiStealButton.Position = UDim2.new(0.05, 0, 0, 170)
antiStealButton.Text = "TP DIR"
antiStealButton.Font = Enum.Font.GothamBold
antiStealButton.TextSize = 11
antiStealButton.BackgroundColor3 = Color3.fromRGB(40, 75, 130)
antiStealButton.TextColor3 = Color3.fromRGB(100, 180, 255)
antiStealButton.Parent = mainFrame
Instance.new("UICorner", antiStealButton).CornerRadius = UDim.new(0, 6)

local strokeBtn1 = Instance.new("UIStroke", antiStealButton)
strokeBtn1.Color = Color3.fromRGB(70, 130, 200)
strokeBtn1.Thickness = 1

antiStealButton.MouseButton1Click:Connect(function()
    if IsStealing then return end

    local animal = getNearestAnimal()
    if not animal then return end

    local prompt = findPrompt(animal)
    if not prompt then return end

    buildStealCallbacks(prompt)
    executeInternalStealAsync(prompt, animal, 1)
end)


-- ✅ BOTÃO TP ESQUERDO - INICIA AUTO STEAL
local autoTpRightButton = Instance.new("TextButton", mainFrame)
autoTpRightButton.Name = "AutoTpRightButton"
autoTpRightButton.Size = UDim2.new(0.45, 0, 0, 32)
autoTpRightButton.Position = UDim2.new(0.5, 0, 0, 170)
autoTpRightButton.Text = "TP ESQ"
autoTpRightButton.Font = Enum.Font.GothamBold
autoTpRightButton.TextSize = 11
autoTpRightButton.BackgroundColor3 = Color3.fromRGB(40, 75, 130)
autoTpRightButton.TextColor3 = Color3.fromRGB(100, 180, 255)
autoTpRightButton.Parent = mainFrame
Instance.new("UICorner", autoTpRightButton).CornerRadius = UDim.new(0, 6)

local strokeBtn2 = Instance.new("UIStroke", autoTpRightButton)
strokeBtn2.Color = Color3.fromRGB(70, 130, 200)
strokeBtn2.Thickness = 1

autoTpRightButton.MouseButton1Click:Connect(function()
    if IsStealing then return end

    local animal = getNearestAnimal()
    if not animal then return end

    local prompt = findPrompt(animal)
    if not prompt then return end

    buildStealCallbacks(prompt)
    executeInternalStealAsync(prompt, animal, 2)
end)


local bar = Instance.new("Frame", mainFrame)
bar.Size = UDim2.new(0.9, 0, 0, 8)
bar.Position = UDim2.new(0.05, 0, 0, 210)
bar.BackgroundColor3 = Color3.fromRGB(30, 50, 80)
bar.Parent = mainFrame
Instance.new("UICorner", bar).CornerRadius = UDim.new(0, 5)

local strokeBar = Instance.new("UIStroke", bar)
strokeBar.Color = Color3.fromRGB(70, 130, 200)
strokeBar.Thickness = 0.8

local fill = Instance.new("Frame", bar)
fill.BackgroundColor3 = Color3.fromRGB(70, 150, 220)
fill.Size = UDim2.new(0, 0, 1, 0)
fill.Parent = bar
Instance.new("UICorner", fill).CornerRadius = UDim.new(0, 5)

local percentLabel = Instance.new("TextLabel", bar)
percentLabel.Size = UDim2.new(1, 0, 1, 0)
percentLabel.BackgroundTransparency = 1
percentLabel.Text = "0%"
percentLabel.TextColor3 = Color3.fromRGB(100, 180, 255)
percentLabel.TextSize = 8
percentLabel.Font = Enum.Font.GothamBold
percentLabel.TextXAlignment = Enum.TextXAlignment.Center

task.spawn(function()
    while true do
        fill.Size = UDim2.new(math.clamp(StealProgress, 0, 1), 0, 1, 0)
        percentLabel.Text = (math.floor(StealProgress * 100 + 0.5)) .. "%"
        task.wait(0.02)
    end
end)

initializeScanner()

--================ SPEED ENGINE (WASD) - JÁ ATIVADO =================--

local SPEED_VALUE = 28.5
local speedConnectionWASD = nil
local speedEnabled = true  -- JÁ ATIVADO

--================ INPUTS =================--
UserInputService.InputBegan:Connect(function(input, gp)
	if gp then return end
	
	local kc = input.KeyCode
	
	if kc == Enum.KeyCode.W then keysPressed.W = true
	elseif kc == Enum.KeyCode.A then keysPressed.A = true
	elseif kc == Enum.KeyCode.S then keysPressed.S = true
	elseif kc == Enum.KeyCode.D then keysPressed.D = true
	elseif kc == Enum.KeyCode.Space then keysPressed.Space = true
	end
end)

UserInputService.InputEnded:Connect(function(input)
	local kc = input.KeyCode
	if kc == Enum.KeyCode.W then keysPressed.W = false
	elseif kc == Enum.KeyCode.A then keysPressed.A = false
	elseif kc == Enum.KeyCode.S then keysPressed.S = false
	elseif kc == Enum.KeyCode.D then keysPressed.D = false
	elseif kc == Enum.KeyCode.Space then keysPressed.Space = false
	end
end)

--================ SPEED ENGINE (WASD) =================--
local function startSpeedWASD()
	if speedConnectionWASD then
		pcall(function() speedConnectionWASD:Disconnect() end)
		speedConnectionWASD = nil
	end

	speedConnectionWASD = RunService.RenderStepped:Connect(function()
		if not speedEnabled then return end
		
		local char = player.Character
		if not char then return end
		local root = char:FindFirstChild("HumanoidRootPart")
		if not root then return end

		local camera = workspace.CurrentCamera
		local moveDirection = Vector3.new(0, 0, 0)

		if UserInputService:IsKeyDown(Enum.KeyCode.W) then
			moveDirection = moveDirection + (camera.CFrame.LookVector * Vector3.new(1, 0, 1)).Unit
		end
		if UserInputService:IsKeyDown(Enum.KeyCode.S) then
			moveDirection = moveDirection - (camera.CFrame.LookVector * Vector3.new(1, 0, 1)).Unit
		end
		if UserInputService:IsKeyDown(Enum.KeyCode.A) then
			moveDirection = moveDirection - camera.CFrame.RightVector
		end
		if UserInputService:IsKeyDown(Enum.KeyCode.D) then
			moveDirection = moveDirection + camera.CFrame.RightVector
		end

		if moveDirection.Magnitude > 0 then
			moveDirection = moveDirection.Unit
			root.AssemblyLinearVelocity = Vector3.new(
				moveDirection.X * SPEED_VALUE,
				root.AssemblyLinearVelocity.Y,
				moveDirection.Z * SPEED_VALUE
			)
		end

		root.AssemblyAngularVelocity = Vector3.zero
	end)
end

local function stopSpeedWASD()
	if speedConnectionWASD then
		pcall(function() speedConnectionWASD:Disconnect() end)
		speedConnectionWASD = nil
	end
end

-- ATIVAR SPEED BOOST IMEDIATAMENTE
task.spawn(function()
    task.wait(1)
    if speedEnabled then
        startSpeedWASD()
    end
end)

player.CharacterAdded:Connect(function()
	task.wait(0.6)
	if AntiRagdollEnabled then
		startAntiRagdoll()
	end
	if speedEnabled then
		startSpeedWASD()
	end
end)

-- ========== ADMIN SPAMMER GUI SEPARADA COM SUPORTE A MOBILE ==========
local adminSpammerGui = Instance.new("ScreenGui")
adminSpammerGui.Name = "AdminSpammerGui"
adminSpammerGui.ResetOnSpawn = false
adminSpammerGui.Parent = CoreGui

local spammerFrame = Instance.new("Frame")
spammerFrame.Name = "SpammerFrame"
spammerFrame.Size = UDim2.new(0, 240, 0, 350)
spammerFrame.Position = UDim2.new(0, 20, 0.5, -175)
spammerFrame.BackgroundColor3 = Color3.fromRGB(15, 25, 45)
spammerFrame.BackgroundTransparency = 0.1
spammerFrame.BorderSizePixel = 0
spammerFrame.Active = true
spammerFrame.Parent = adminSpammerGui

Instance.new("UICorner", spammerFrame).CornerRadius = UDim.new(0, 12)

local spamStroke = Instance.new("UIStroke", spammerFrame)
spamStroke.Thickness = 2
spamStroke.Color = Color3.fromRGB(70, 130, 200)
spamStroke.Transparency = 0.3

local spamTitle = Instance.new("TextLabel")
spamTitle.Size = UDim2.new(1, 0, 0, 40)
spamTitle.Position = UDim2.new(0, 0, 0, 0)
spamTitle.BackgroundColor3 = Color3.fromRGB(25, 45, 80)
spamTitle.BackgroundTransparency = 0.2
spamTitle.Text = "⚡ SPAMMER"
spamTitle.TextColor3 = Color3.fromRGB(100, 180, 255)
spamTitle.TextSize = 16
spamTitle.Font = Enum.Font.GothamBold
spamTitle.Parent = spammerFrame
Instance.new("UICorner", spamTitle).CornerRadius = UDim.new(0, 10)

local spamCloseBtn = Instance.new("TextButton")
spamCloseBtn.Position = UDim2.new(1, -32, 0, 8)
spamCloseBtn.Size = UDim2.new(0, 24, 0, 24)
spamCloseBtn.BackgroundColor3 = Color3.fromRGB(200, 50, 50)
spamCloseBtn.Text = "✕"
spamCloseBtn.TextSize = 14
spamCloseBtn.TextColor3 = Color3.new(1, 1, 1)
spamCloseBtn.Font = Enum.Font.GothamBold
spamCloseBtn.Parent = spammerFrame
Instance.new("UICorner", spamCloseBtn).CornerRadius = UDim.new(0, 6)

spamCloseBtn.MouseButton1Click:Connect(function()
    adminSpammerGui.Enabled = false
end)

-- Lista de Players
local spamPlayerList = Instance.new("ScrollingFrame")
spamPlayerList.Position = UDim2.new(0, 12, 0, 50)
spamPlayerList.Size = UDim2.new(1, -24, 0, 110)
spamPlayerList.BackgroundColor3 = Color3.fromRGB(23, 44, 90)
spamPlayerList.BorderSizePixel = 0
spamPlayerList.ScrollBarThickness = 4
spamPlayerList.CanvasSize = UDim2.fromOffset(0, 0)
spamPlayerList.Parent = spammerFrame
Instance.new("UICorner", spamPlayerList).CornerRadius = UDim.new(0, 8)

local spamListLayout = Instance.new("UIListLayout", spamPlayerList)
spamListLayout.Padding = UDim.new(0, 2)
spamListLayout.SortOrder = Enum.SortOrder.LayoutOrder

-- Info Label
local spamInfoLabel = Instance.new("TextLabel")
spamInfoLabel.Position = UDim2.new(0, 12, 0, 170)
spamInfoLabel.Size = UDim2.new(1, -24, 0, 28)
spamInfoLabel.BackgroundColor3 = Color3.fromRGB(30, 50, 90)
spamInfoLabel.BorderSizePixel = 0
spamInfoLabel.Text = "📍 Selecione"
spamInfoLabel.TextColor3 = Color3.fromRGB(170, 200, 255)
spamInfoLabel.TextSize = 13
spamInfoLabel.Font = Enum.Font.Gotham
spamInfoLabel.Parent = spammerFrame
Instance.new("UICorner", spamInfoLabel).CornerRadius = UDim.new(0, 6)

-- Botão SPAM
local spamButtonSubmit = Instance.new("TextButton")
spamButtonSubmit.Position = UDim2.new(0.5, -65, 0, 210)
spamButtonSubmit.Size = UDim2.new(0, 130, 0, 36)
spamButtonSubmit.BackgroundColor3 = Color3.fromRGB(35, 80, 180)
spamButtonSubmit.Text = "🔥 SPAM"
spamButtonSubmit.TextSize = 15
spamButtonSubmit.TextColor3 = Color3.fromRGB(255, 255, 255)
spamButtonSubmit.Font = Enum.Font.GothamBold
spamButtonSubmit.BorderSizePixel = 0
spamButtonSubmit.AutoButtonColor = false
spamButtonSubmit.Active = false
spamButtonSubmit.Parent = spammerFrame
Instance.new("UICorner", spamButtonSubmit).CornerRadius = UDim.new(0, 8)

local spamBtnStroke = Instance.new("UIStroke", spamButtonSubmit)
spamBtnStroke.Color = Color3.fromRGB(70, 150, 220)
spamBtnStroke.Thickness = 1

-- Variáveis Spammer
local selectedPlayer = nil
local isSpammingNow = false

-- Função para enviar chat
local function sendChatMsg(message)
    pcall(function()
        if TextChatService.ChatVersion == Enum.ChatVersion.TextChatService then
            local textChannels = TextChatService:WaitForChild("TextChannels", 3)
            if textChannels then
                local generalChannel = textChannels:FindFirstChild("RBXGeneral") or textChannels:FindFirstChildWhichIsA("TextChannel")
                if generalChannel then
                    generalChannel:SendAsync(message)
                    return
                end
            end
        end
        local rs = game:GetService("ReplicatedStorage")
        local chatEvents = rs:FindFirstChild("DefaultChatSystemChatEvents")
        if chatEvents then
            local sayRequest = chatEvents:FindFirstChild("SayMessageRequest")
            if sayRequest then
                sayRequest:FireServer(message, "All")
            end
        end
    end)
end

-- Atualizar lista spammer
local function updateSpammerList()
    for _, c in ipairs(spamPlayerList:GetChildren()) do
        if c:IsA("TextButton") then
            c:Destroy()
        end
    end
    
    local otherPlayers = {}
    for _, p in ipairs(Players:GetPlayers()) do
        if p ~= player then
            table.insert(otherPlayers, p)
        end
    end
    
    -- Se só tem 1 player, selecionar automaticamente
    if #otherPlayers == 1 then
        selectedPlayer = otherPlayers[1]
        spamInfoLabel.Text = "✓ " .. selectedPlayer.Name
        spamButtonSubmit.Active = true
        spamButtonSubmit.BackgroundTransparency = 0
    end
    
    -- Criar botões
    for _, p in ipairs(otherPlayers) do
        local btn = Instance.new("TextButton")
        btn.Size = UDim2.new(1, -10, 0, 28)
        btn.BackgroundColor3 = Color3.fromRGB(31, 54, 102)
        btn.Text = "👤 " .. p.Name
        btn.TextSize = 13
        btn.Font = Enum.Font.Gotham
        btn.TextColor3 = Color3.new(1, 1, 1)
        btn.Parent = spamPlayerList
        btn.AutoButtonColor = false
        btn.BorderSizePixel = 0
        Instance.new("UICorner", btn).CornerRadius = UDim.new(0, 6)
        
        -- Se é o único player e já foi selecionado, colorir de azul
        if selectedPlayer == p then
            btn.BackgroundColor3 = Color3.fromRGB(50, 160, 255)
        end
        
        btn.MouseButton1Click:Connect(function()
            selectedPlayer = p
            spamInfoLabel.Text = "✓ " .. p.Name
            spamButtonSubmit.Active = true
            spamButtonSubmit.BackgroundTransparency = 0
            
            for _, b in ipairs(spamPlayerList:GetChildren()) do
                if b:IsA("TextButton") then
                    b.BackgroundColor3 = Color3.fromRGB(31, 54, 102)
                end
            end
            btn.BackgroundColor3 = Color3.fromRGB(50, 160, 255)
        end)
    end
    
    spamPlayerList.CanvasSize = UDim2.new(0, 0, 0, spamListLayout.AbsoluteContentSize.Y + 3)
end

Players.PlayerAdded:Connect(updateSpammerList)
Players.PlayerRemoving:Connect(updateSpammerList)
updateSpammerList()

-- Função para fazer o spam
local function performSpam()
    if not spamButtonSubmit.Active or isSpammingNow then return end
    if not selectedPlayer or not selectedPlayer.Parent then
        spamInfoLabel.Text = "❌ Inválido"
        return
    end
    
    isSpammingNow = true
    spamButtonSubmit.Active = false
    
    local cmds = {
        ";tiny " .. selectedPlayer.Name,
        ";rocket " .. selectedPlayer.Name,
        ";balloon " .. selectedPlayer.Name,
    }
    
    task.spawn(function()
        for _, cmd in ipairs(cmds) do
            if selectedPlayer and selectedPlayer.Parent then
                sendChatMsg(cmd)
            end
        end
        spamInfoLabel.Text = "✓ Concluído!"
    end)
    
    task.wait(2)
    isSpammingNow = false
    spamButtonSubmit.Active = true
    spamInfoLabel.Text = "✓ " .. selectedPlayer.Name
end

-- Botão SPAM Click
spamButtonSubmit.MouseButton1Click:Connect(function()
    performSpam()
end)

-- ✅ DRAG SPAMMER GUI COM SUPORTE A TOUCH
local spamDragging, spamDragStart, spamStartPos
spammerFrame.InputBegan:Connect(function(input)
    if input.UserInputType == Enum.UserInputType.MouseButton1 or input.UserInputType == Enum.UserInputType.Touch then
        spamDragging = true
        spamDragStart = input.Position
        spamStartPos = spammerFrame.Position
    end
end)

UserInputService.InputChanged:Connect(function(input)
    if spamDragging and (input.UserInputType == Enum.UserInputType.MouseMovement or input.UserInputType == Enum.UserInputType.Touch) then
        local delta = input.Position - spamDragStart
        spammerFrame.Position = UDim2.new(spamStartPos.X.Scale, spamStartPos.X.Offset + delta.X, spamStartPos.Y.Scale, spamStartPos.Y.Offset + delta.Y)
    end
end)

UserInputService.InputEnded:Connect(function(input)
    if input.UserInputType == Enum.UserInputType.MouseButton1 or input.UserInputType == Enum.UserInputType.Touch then
        spamDragging = false
    end
end)

-- ✅ KEYBIND F PARA SPAM (FUNCIONA EM PC)
UserInputService.InputBegan:Connect(function(input, gameProcessed)
    if gameProcessed then return end
    
    -- F para SPAM (só em PC)
    if input.KeyCode == Enum.KeyCode.F then
        if selectedPlayer and selectedPlayer.Parent then
            performSpam()
        end
    end
    
    -- H para abrir/fechar spammer (só em PC)
    if input.KeyCode == Enum.KeyCode.H then
        adminSpammerGui.Enabled = not adminSpammerGui.Enabled
    end
end)

-- ========== BOTÃO FLUTUANTE PARA MOBILE ==========
local mobileMenuBtn = Instance.new("TextButton")
mobileMenuBtn.Name = "MobileMenuBtn"
mobileMenuBtn.Size = UDim2.new(0, 50, 0, 50)
mobileMenuBtn.Position = UDim2.new(0, 10, 0, 10)
mobileMenuBtn.BackgroundColor3 = Color3.fromRGB(35, 80, 180)
mobileMenuBtn.Text = "H"
mobileMenuBtn.TextSize = 18
mobileMenuBtn.TextColor3 = Color3.new(1, 1, 1)
mobileMenuBtn.Font = Enum.Font.GothamBold
mobileMenuBtn.BorderSizePixel = 0
mobileMenuBtn.Parent = screenGui
Instance.new("UICorner", mobileMenuBtn).CornerRadius = UDim.new(1, 0)

local mobileBtnStroke = Instance.new("UIStroke", mobileMenuBtn)
mobileBtnStroke.Color = Color3.fromRGB(70, 150, 220)
mobileBtnStroke.Thickness = 2

mobileMenuBtn.MouseButton1Click:Connect(function()
    adminSpammerGui.Enabled = not adminSpammerGui.Enabled
end)

-- Drag do botão mobile
local mobileDragging, mobileDragStart, mobileStartPos
mobileMenuBtn.InputBegan:Connect(function(input)
    if input.UserInputType == Enum.UserInputType.MouseButton1 or input.UserInputType == Enum.UserInputType.Touch then
        mobileDragging = true
        mobileDragStart = input.Position
        mobileStartPos = mobileMenuBtn.Position
    end
end)

UserInputService.InputChanged:Connect(function(input)
    if mobileDragging and (input.UserInputType == Enum.UserInputType.MouseMovement or input.UserInputType == Enum.UserInputType.Touch) then
        local delta = input.Position - mobileDragStart
        mobileMenuBtn.Position = UDim2.new(mobileStartPos.X.Scale, mobileStartPos.X.Offset + delta.X, mobileStartPos.Y.Scale, mobileStartPos.Y.Offset + delta.Y)
    end
end)

UserInputService.InputEnded:Connect(function(input)
    if input.UserInputType == Enum.UserInputType.MouseButton1 or input.UserInputType == Enum.UserInputType.Touch then
        mobileDragging = false
    end
end)

print("✅ MDB HALF TP + ADMIN SPAMMER MOBILE!")
print("✅ Anti Ragdoll JÁ ATIVADO!")
print("✅ Speed Boost JÁ ATIVADO!")
print("")
print("📍 PC: Pressione H para abrir o Admin Spammer!")
print("📍 MOBILE: Clique no botão H flutuante!")
print("🔥 PC: Pressione F para SPAM RÁPIDO!")
print("🔥 MOBILE: Clique no botão SPAM!")
