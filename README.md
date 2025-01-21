local Lib = loadstring(game:HttpGet("https://raw.githubusercontent.com/7yhx/kwargs_Ui_Library/main/source.lua"))()


local UI = Lib:Create(
    Theme = "Dark", -- or any other theme
    Size = UDim2.new(0, 555, 0, 400) -- default
)
 
 local Main = UI:Tab(
    Name = "Inicio"
)
 
 local Divider = Main:Divider(
    Name = "Inicio shit"
)
 
 local QuitDivider = Main:Divider(
    Name = "Sair"
)

 local Speed = Divider:Toggle(
    Name = "Modo Flash",
    Description = "Fique com alta velocidade no Game !",
    Callback = function(State)
        local player = game.Players.LocalPlayer
        local character = player.Character or player.CharacterAdded:Wait()
        local humanoid = character:FindFirstChildOfClass("Humanoid")
        
        if humanoid then
            humanoid.WalkSpeed = 200
            print("Velocidade aumentada para 200!")
        else
            warn("Humanoid nao encontrado!")
        end
    end
)

 Divider:SearchDropdown(
    Name = "Teleports",
    Options = {"Pleasant Park", "Loot Lake", "Tomato Town", "Wailing Woods", "Anarchy Acres", "Retail Row"},
    ClearText = false, -- default
    Callback = function(Value)
        print(Value)
    end
)
 
 local Quit = QuitDivider:Button(
    Name = "Fechar Hub",
    Callback = function()
        UI:Quit{
            Message = "Hub Off...", -- closing message
            Length = 1 -- seconds the closing message shows for
        }
    end
)
