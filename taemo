local ScreenGui = Instance.new("ScreenGui")
local Frame = Instance.new("Frame")

ScreenGui.Parent = game.CoreGui
ScreenGui.ZIndexBehavior = Enum.ZIndexBehavior.Sibling

Frame.Parent = ScreenGui
Frame.BackgroundColor3 = Color3.new(0.098, 0.459, 1)
Frame.BackgroundTransparency = 0.8
Frame.BorderColor3 = Color3.new(0.09, 0.137, 0.776)
Frame.BorderSizePixel = 2
Frame.Position = UDim2.new(0, 0, 0, 0)
Frame.Size = UDim2.new(0, 0, 0, 0)

local Mouse = game.Players.LocalPlayer:GetMouse()
local Run = game:GetService("RunService")
local Player = game.Players.LocalPlayer
local userinputservice = game:GetService("UserInputService")
local camera = game.Workspace.CurrentCamera

local selected = {}
_G.sssaaaaaaaaaa = true

local run = userinputservice.InputBegan:Connect(function(input)
    if not _G.sssaaaaaaaaaa then return end
    if input.UserInputType == Enum.UserInputType.MouseButton1 then
        Frame.Visible = true
        Frame.Position = UDim2.new(0, Mouse.X, 0, Mouse.Y)
        while userinputservice:IsMouseButtonPressed(Enum.UserInputType.MouseButton1) do
            Run.RenderStepped:wait()
            if _G.strictdeselectmode == true then
            for i,v in pairs(game.Workspace.PlayerModels:GetChildren()) do
                if v:FindFirstChild("OriginSquare") then
                    if v.Main:FindFirstChild("Selection") then
                        v.Main.Selection:Destroy()
                    end
                end
                end
            end
            
            Frame.Size = UDim2.new(0, Mouse.X, 0, Mouse.Y) - Frame.Position
            
            for i, v in pairs(game:GetService("Workspace").Properties:GetChildren()) do
                if v:FindFirstChild("OriginSquare") then
                    local screenpos, visible = camera:WorldToScreenPoint(v.OriginSquare.CFrame.p)
                    if visible then
                        if is_in_frame(screenpos, Frame) then
                            if v.OriginSquare:FindFirstChild("Selection") then continue end

                            local bob = Instance.new("SelectionBox", v.OriginSquare)
                            bob.Name = "Selection"
                            bob.Adornee = bob.Parent
                            --a.AlwaysOnTop = true
                            bob.SurfaceTransparency = 0.5
                            bob.LineThickness = 0.09
                            bob.SurfaceColor3 = Color3.fromRGB(0, 0, 0)
                            bob.Color3 = Color3.fromRGB(0, 240, 44)
                        end
                    end
                end
            end
        end
        Frame.Size = UDim2.new(0, 1, 0, 1)
        Frame.Visible = false
    end
end)

function lassoTpcheck()
    function is_in_frame(screenpos, frame)
        local xPos = frame.AbsolutePosition.X
        local yPos = frame.AbsolutePosition.Y

        local xSize = frame.AbsoluteSize.X
        local ySize = frame.AbsoluteSize.Y

        local check1 = screenpos.X >= xPos and screenpos.X <= xPos + xSize
        local check2 = screenpos.X <= xPos and screenpos.X >= xPos + xSize

        local check3 = screenpos.Y >= yPos and screenpos.Y <= yPos + ySize
        local check4 = screenpos.Y <= yPos and screenpos.Y >= yPos + ySize

        local finale = (check1 and check3) or (check2 and check3) or (check1 and check4) or (check2 and check4)

        return finale
    end
end
lassoTpcheck()
