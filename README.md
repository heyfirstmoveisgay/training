-- 🎯 Triggerbot ultra rapide sur contact immédiat

local Players = game:GetService("Players")
local LocalPlayer = Players.LocalPlayer

-- Fonction pour tirer immédiatement
local function FireWeapon()
    -- Action immédiate ici
    print("Triggerbot: TIR INSTANTANÉ !! 🔥")
    -- Exemple : si tu as un RemoteEvent pour tirer :
    -- game.ReplicatedStorage.ShootEvent:FireServer()
end

-- Dès qu'on touche un autre joueur
local function OnTouch(otherPart)
    local character = otherPart:FindFirstAncestorOfClass("Model")
    local player = Players:GetPlayerFromCharacter(character)
    if player and player ~= LocalPlayer then
        FireWeapon()
    end
end

-- Se connecter au corps du joueur
LocalPlayer.CharacterAdded:Connect(function(character)
    local rootPart = character:WaitForChild("HumanoidRootPart")
    rootPart.Touched:Connect(OnTouch)
end)

-- Si le personnage est déjà chargé
if LocalPlayer.Character then
    local rootPart = LocalPlayer.Character:WaitForChild("HumanoidRootPart")
    rootPart.Touched:Connect(OnTouch)
end

print("✅ Triggerbot ultra instantané prêt ! 🚀")
