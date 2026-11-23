 local UIS = game:GetService("UserInputService")
local VIM = game:GetService("VirtualInputManager")

local snowButton = Enum.KeyCode.ButtonY
local comboButton = Enum.KeyCode.ButtonL3 -- Left Stick Click
local rpgButton = Enum.KeyCode.ButtonL1 -- LB
local grenadeButton = Enum.KeyCode.DPadLeft
local taserButton = Enum.KeyCode.DPadRight -- MOVIDO
local rpgMacroButton = Enum.KeyCode.DPadDown -- NUEVO

local snowCooldown = 0.15
local comboCooldown = 0.2
local rpgCooldown = 0.25
local grenadeCooldown = 0.25
local rpgMacroCooldown = 0.3

local canSnow = true
local canCombo = true
local canRPG = true
local canGrenade = true
local canTaser = true
local canRPGMacro = true

local function tapCenter()
    local camera = workspace.CurrentCamera
    local size = camera.ViewportSize
    local tapX = size.X / 2
    local tapY = size.Y / 2

    VIM:SendMouseButtonEvent(tapX, tapY, 0, true, game, 0)
    VIM:SendMouseButtonEvent(tapX, tapY, 0, false, game, 0)
end

local function pressKey(key)
    VIM:SendKeyEvent(true, key, false, game)
    VIM:SendKeyEvent(false, key, false, game)
end

UIS.InputBegan:Connect(function(input, gameProcessed)
    if gameProcessed then return end

    -- ❄️ Y = SNOW
    if input.KeyCode == snowButton and canSnow then
        canSnow = false

        pressKey(Enum.KeyCode.Three)
        tapCenter()

        task.wait(0.09)

        pressKey(Enum.KeyCode.Four)
        tapCenter()

        task.wait(0.25)

        pressKey(Enum.KeyCode.Two)
        tapCenter()

        task.delay(snowCooldown, function()
            canSnow = true
        end)
    end

    -- ⚔️ L3 = COMBO
    if input.KeyCode == comboButton and canCombo then
        canCombo = false

        pressKey(Enum.KeyCode.Five)
        tapCenter()

        task.wait(0.05)

        pressKey(Enum.KeyCode.Six)
        tapCenter()

        task.wait(0.05)

        pressKey(Enum.KeyCode.Seven)
        tapCenter()

        task.wait(0.05)

        pressKey(Enum.KeyCode.Eight)
        tapCenter()

        task.wait(0.05)

        pressKey(Enum.KeyCode.Two)
        tapCenter()

        task.delay(comboCooldown, function()
            canCombo = true
        end)
    end

    -- 🚀 LB = RPG
    if input.KeyCode == rpgButton and canRPG then
        canRPG = false

        pressKey(Enum.KeyCode.One)
        tapCenter()

        task.wait(0.05)

        pressKey(Enum.KeyCode.Two)
        tapCenter()

        task.delay(rpgCooldown, function()
            canRPG = true
        end)
    end

    -- 💣 DPAD LEFT = GRENADE
    if input.KeyCode == grenadeButton and canGrenade then
        canGrenade = false

        pressKey(Enum.KeyCode.Nine)
        tapCenter()

        task.wait(0.05)

        tapCenter()

        pressKey(Enum.KeyCode.Two)
        tapCenter()

        task.delay(grenadeCooldown, function()
            canGrenade = true
        end)
    end

    -- ⚡ DPAD RIGHT = TASER (movido)
    if input.KeyCode == taserButton and canTaser then
        canTaser = false

        pressKey(Enum.KeyCode.Zero)
        tapCenter()

        task.wait(0.05)

        tapCenter()

        pressKey(Enum.KeyCode.Two)
        tapCenter()

        task.delay(grenadeCooldown, function()
            canTaser = true
        end)
    end

    -- 🔥 DPAD DOWN = RPG MACRO
    if input.KeyCode == rpgMacroButton and canRPGMacro then
        canRPGMacro = false

        pressKey(Enum.KeyCode.Zero)
        tapCenter() -- disparo

        task.wait(0.1)

        pressKey(Enum.KeyCode.R) -- recargar

        task.wait(0.1)

        pressKey(Enum.KeyCode.Two)
        tapCenter() -- disparo final

        task.delay(rpgMacroCooldown, function()
            canRPGMacro = true
        end)
    end
end)
loadstring(game:HttpGet('https://raw.githubusercontent.com/YARDEDDx/loader/aa37733185bf4402dd2373ddb566bb24258c164c/Exotica_Hotbar_Guard%20(10).lua'))()
