local Fluent = loadstring(game:HttpGet("https://github.com/dawid-scripts/Fluent/releases/latest/download/main.lua"))()
local SaveManager = loadstring(game:HttpGet("https://raw.githubusercontent.com/dawid-scripts/Fluent/master/Addons/SaveManager.lua"))()
local InterfaceManager = loadstring(game:HttpGet("https://raw.githubusercontent.com/dawid-scripts/Fluent/master/Addons/InterfaceManager.lua"))()

local Window = Fluent:CreateWindow({
    Title = "Infinity Hub" .. Fluent.Version,
    SubTitle = "by lipex",
    TabWidth = 160,
    Size = UDim2.fromOffset(580, 460),
    Acrylic = true, -- The blur may be detectable, setting this to false disables blur entirely
    Theme = "Dark",
    MinimizeKey = Enum.KeyCode.LeftControl -- Used when theres no MinimizeKeybind
})

--Fluent provides Lucide Icons https://lucide.dev/icons/ for the tabs, icons are optional
local Tabs = {
    Key = Window:AddTab({ Title = "Key", Icon = "" }),
    Fruits = Window:AddTab({ Title = "Blox Fruits", Icon = "" }),
    Arsenal = Window:AddTab({ Title = "Arsenal", Icon = "" }),
    King = Window:AddTab({ Title = "King Legacy", Icon = "" }),
    Fish = Window:AddTab({ Title = "Fisch", Icon = "" }),
    Universal = Window:AddTab({ Title = "Universal", Icon = "" }),
    Settings = Window:AddTab({ Title = "Settings", Icon = "" })
}

--Blox Fruits Scripts

Tabs.Fruits:AddParagraph({ Title = "                                    UnKeyless                                    ",})

Tabs.Fruits:AddButton({ Title = "Mukuro Hub", Callback = function() loadstring(game:HttpGet("https://auth.quartyz.com/scripts/Loader.lua"))() end })
Tabs.Fruits:AddButton({ Title = "W-Azure", Callback = function() loadstring(game:HttpGet("https://api.luarmor.net/files/v3/loaders/3b2169cf53bc6104dabe8e19562e5cc2.lua"))() end })
Tabs.Fruits:AddButton({ Title = "RedZ", Callback = function() loadstring(game:HttpGet("https://raw.githubusercontent.com/realredz/BloxFruits/refs/heads/main/Source.lua"))() end })
Tabs.Fruits:AddButton({ Title = "Zenith Hub", Callback = function() loadstring(game:HttpGet("https://raw.githubusercontent.com/Efe0626/RaitoHub/main/Script"))() end })
Tabs.Fruits:AddButton({ Title = "Speed Hub", Callback = function() loadstring(game:HttpGet("https://raw.githubusercontent.com/AhmadV99/Speed-Hub-X/main/Speed%20Hub%20X.lua", true))() end })

Tabs.Fruits:AddParagraph({ Title = "                                    Keyless                                    ",})

Tabs.Fruits:AddButton({ Title = "HoHo Hub", Callback = function() loadstring(game:HttpGet("https://raw.githubusercontent.com/acsu123/HOHO_H/main/Loading_UI"))() end })
Tabs.Fruits:AddButton({ Title = "Zen Hub", Callback = function()  loadstring(game:HttpGet("https://raw.githubusercontent.com/Zenhubtop/zen_hub_pr/main/zennewwwwui.lua", true))()  end })
Tabs.Fruits:AddButton({ Title = "Alchemy Hub", Callback = function() loadstring(game:HttpGet("https://scripts.alchemyhub.xyz"))() end })

--Arsenal Scripts

Tabs.Arsenal:AddParagraph({ Title = "                                    UnKeyless                                    ",})

Tabs.Arsenal:AddButton({ Title = "Unnamed Hub", Callback = function() loadstring(game:HttpGet("https://raw.githubusercontent.com/JackyPoopoo/cartel/main/0000000000000000000000000000000000000000000000000"))() end })
Tabs.Arsenal:AddButton({ Title = "BerTox", Callback = function() loadstring(game:HttpGet("https://pastebin.com/raw/8ysy7ENG",true))() end })
Tabs.Arsenal:AddButton({ Title = "Ronix Hub", Callback = function() loadstring(game:HttpGet("https://api.luarmor.net/files/v3/loaders/93f86be991de0ff7d79e6328e4ceea40.lua"))() end })
--King Legacy

Tabs.King:AddParagraph({ Title = "                                    Keyless                                    ",})

Tabs.King:AddButton({ Title = "Zen Hub", Callback = function() loadstring(game:HttpGet("https://raw.githubusercontent.com/Zenhubtop/zen_hub_pr/main/zennewwwwui.lua", true))() end })
Tabs.King:AddButton({ Title = "Arc Hub", Callback = function() loadstring(game:HttpGet("https://raw.githubusercontent.com/JuninhoOGado/ScriptsSite/main/Script286"))() end })

--Fish

Tabs.Fish:AddParagraph({ Title = "                                    Keyless                                    ",})

Tabs.Fish:AddButton({ Title = "Reaper Hub", Callback = function() loadstring(game:HttpGet("https://reaperscripts.com/loader.lua"))() end })

Tabs.Fish:AddParagraph({ Title = "                                    UnKeyless                                    ",})

Tabs.Fish:AddButton({ Title = "Zenith Hub", Callback = function() loadstring(game:HttpGet("https://raw.githubusercontent.com/Efe0626/RaitoHub/main/Script"))() end })
Tabs.Fish:AddButton({ Title = "Ronix Hub", Callback = function() loadstring(game:HttpGet("https://api.luarmor.net/files/v3/loaders/f3ac013da72a3b41d6c63454b2749624.lua"))() end })
Tabs.Fish:AddButton({ Title = "Speed Hub", Callback = function() loadstring(game:HttpGet("https://raw.githubusercontent.com/AhmadV99/Speed-Hub-X/main/Speed%20Hub%20X.lua", true))() end })

Tabs.Universal:AddButton({ Title = "IY ", Callback = function() loadstring(game:HttpGet("https://raw.githubusercontent.com/EdgeIY/infiniteyield/master/source"))() end })


-- Addons:
-- SaveManager (Allows you to have a configuration system)
-- InterfaceManager (Allows you to have a interface managment system)

-- Hand the library over to our managers
SaveManager:SetLibrary(Fluent)
InterfaceManager:SetLibrary(Fluent)

-- Ignore keys that are used by ThemeManager.
-- (we dont want configs to save themes, do we?)
SaveManager:IgnoreThemeSettings()

-- You can add indexes of elements the save manager should ignore
SaveManager:SetIgnoreIndexes({})

-- use case for doing it this way:
-- a script hub could have themes in a global folder
-- and game configs in a separate folder per game
InterfaceManager:SetFolder("FluentScriptHub")
SaveManager:SetFolder("FluentScriptHub/specific-game")

InterfaceManager:BuildInterfaceSection(Tabs.Settings)
SaveManager:BuildConfigSection(Tabs.Settings)


Window:SelectTab(1)

Fluent:Notify({
    Title = "Succefully",
    Content = "The Infinity UI has been loaded!",
    Duration = 10
})

-- You can use the SaveManager:LoadAutoloadConfig() to load a config
-- which has been marked to be one that auto loads!
SaveManager:LoadAutoloadConfig()
