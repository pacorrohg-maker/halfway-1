# halfway-1
local Players = game:GetService("Players")
local TweenService = game:GetService("TweenService")
local RunService = game:GetService("RunService")
local UserInputService = game:GetService("UserInputService")
local ProximityPromptService = game:GetService("ProximityPromptService")
local CoreGui = game:GetService("CoreGui")
local ReplicatedStorage = game:GetService("ReplicatedStorage")

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

if CoreGui:FindFirstChild("UwuHubSemiTP") then
    CoreGui["UwuHubSemiTP"]:Destroy()
end

local screenGui = Instance.new("ScreenGui")
screenGui.Name = "UwuHubSemiTP"
screenGui.ResetOnSpawn = false
screenGui.ZIndexBehavior = Enum.ZIndexBehavior.Global
screenGui.Parent = CoreGui

local function createESPBox(position, labelText)
    local espFolder = Instance.new("Folder")
    espFolder.Name = "ESPBox_" .. labelText
    espFolder.Parent = workspace
    local box = Instance.new("Part")
    box.Size = Vector3.new(5, 0.5, 5)
    box.Position = position
    box.Anchored = true
    box.CanCollide = false
    box.Transparency = 0.5
    box.Material = Enum.Material.Neon
    box.Color = Color3.fromRGB(255, 100, 100)
    box.Parent = espFolder
    local selectionBox = Instance.new("SelectionBox")
    selectionBox.Adornee = box
    selectionBox.LineThickness = 0.05
    selectionBox.Color3 = Color3.fromRGB(255, 100, 100)
    selectionBox.Parent = box
    local billboard = Instance.new("BillboardGui")
    billboard.Adornee = box
    billboard.Size = UDim2.new(0, 150, 0, 40)
    billboard.StudsOffset = Vector3.new(0, 2, 0)
    billboard.AlwaysOnTop = true
    billboard.Parent = box
    local textLabel = Instance.new("TextLabel")
    textLabel.Size = UDim2.new(1, 0, 1, 0)
    textLabel.BackgroundTransparency = 1
    textLabel.Text = labelText
    textLabel.TextColor3 = Color3.fromRGB(255, 200, 200)
    textLabel.TextSize = 16
    textLabel.Font = Enum.Font.GothamBold
    textLabel.TextStrokeTransparency = 0.4
    textLabel.TextStrokeColor3 = Color3.fromRGB(120, 0, 0)
    textLabel.Parent = billboard
    return espFolder
end

createESPBox(pos1, "Teleport Here")
createESPBox(pos2, "Teleport Here")
createESPBox(standing1, "Standing 1")
createESPBox(standing2, "Standing 2")
createESPBox(Vector3.new(-349.325867, -7.00000238, 95.0031433), "Auto tp Right")
createESPBox(Vector3.new(-349.560211, -7.00000238, 27.0543289), "Auto tp Left")

local C = {
