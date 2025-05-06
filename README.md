# Roblox-Modular-Gun-System
A Modular Open Source Gun System, Easily Add Guns And Change Data.  To Add Guns, Duplicate The Assault Rifle, Change Sounds, Change Model, And Welds.  When Referencing The Model When Spawing, Refer To The New Model And Model Name, And Change Data.  

--[[


Made By @PanchoPantera2k, Alt Account: AbcForMonkeyMan

These modules manage guns in a modular,
object-oriented way, allowing guns to be created, 
retrieved, parented, and destroyed.

# HOW TO CREATE GUN


## Reference Variables Needed Such As:


-- Service Variables
local ServerScriptService = game:GetService("ServerScriptService")
local ServerStorage = game:GetService("ServerStorage")

-- Object Variables
local ServerModules = ServerScriptService:WaitForChild("ModuleScripts")
local Tools = ServerStorage:WaitForChild("Tools")

-- Module Variables
local GunModule = require(ServerModules:WaitForChild("GunModule"))
local RetrievalSystem = require(ServerModules:WaitForChild("GunRetrievalSystem"))

local AssaultRifle = Tools:WaitForChild("AssaultRifle")

-- Define The Data Of The Gun

local Data = {
			Name = "Assault Rifle",
			MaxAmmo = 25,
			Ammo = 25,
			Damage = 15,
			Range = 100,
			FireRate = .15,
			ReloadTime = 2,
			HeadShotMultiplier = 1.5,
			Spread = .05,
			Model = AssaultRifle
		}

-- Create A Gun Using The GunModule.New(Data, Player) Function

local Gun = GunModule.New(Data, player)

-- Parent The Gun Using Gun:Parent(Player.Backpack)

Gun:Parent(player.Backpack)


## MAIN FUNCTIONS IN MODULES


### GUN MODULE FUNCTIONS

local Gun = GunModule.New() -- Creates A New Gun Object, NOT Tool

Gun:Parent(NewParent) -- Creates A Gun Tool IF One Doesn't Exist Yet And Parents To NewParent, ELSE Parents To NewParent

Gun:Shoot(MousePosition) -- Shoots A Bullet Using A Raycast Towards The MousePosition

Gun:Reload() -- Reloads The Gun To Full Ammo After A Pre-Defined Time In Gun Data

Gun:Remove() -- Properly Destroys And Removes Gun

### RETRIEVAL SYSTEM FUNCTIONS

:AddGun(Player, Gun) -- Adds A Gun To The Players Gun Retrieval System

:GetGunFromModel(Model) -- Gets The Gun Associated With The Model (Tool, Not Actually The Model)

:GetGunsFromPlayer(Player) — Gets All Guns Owned By A Player

:RemoveGun(Player, Gun) — Removes A Specific Gun From The Players Gun Retrieval System

:RemoveGunFromModel(Model) — Removes A Specific Gun Using The Gun Model Associate W/The Gun

:RemoveGunsFromPlayer(Player) — Removes All Guns Associate With A Player.


## NOTES

-- Remove Gun Once Player Leaves Using:

game.Players.PlayerRemoving:Connect(function(player: Player) 
	RetrievalSystem:RemoveGunsFromPlayer(player)
end)

Make sure players have a Character loaded before giving them guns.

Make sure new guns have the RemoteEvents, Sounds, and BulletOrigin folders and parts respectively. 

--]]
