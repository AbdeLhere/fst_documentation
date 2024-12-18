---
icon: square-sliders
---

```lua
Config = Config or {}

Config.Options = {

    cayoPerico = {
        enable_cayo_minimap = true, -- Set to true if you want enable cayo minimap
        using_ipl_loader = false, -- If you are using an IPL RESOURCE set this true (example: https://forum.cfx.re/t/the-cayo-perico-island-available-for-fivem/1897446?page=38)
    },

    enableBackground = true,  -- Toggle background change on/off
    opacity = 90,              -- Change background opacity

    ChangeHeaderNames = false, -- Toggle header name changes on/off

    enableColorChanges = true, -- Toggle all color changes on/off
    RedGreenBlueAlpha = {

        --- [[[[[[[[[[[[[  https://rgbacolorpicker.com  ]]]]]]]]]]]]] Note: Dont change ["ALPHA"] = 0.8

        HudLineColor = { ["RED"] = 0, ["GREEN"] = 0, ["BLUE"] = 0, ["ALPHA"] = 0.8 },
        PauseMenuStyleColor = { ["RED"] = 62, ["GREEN"] = 62, ["BLUE"] = 62, ["ALPHA"] = 0.8 },
        MapWaypointColor = { ["RED"] = 189, ["GREEN"] = 0, ["BLUE"] = 255, ["ALPHA"] = 0.8 },

    },

    Header = {
        ["TITLE"] = "Server Name Menu",
        ["SUBTITLE"] = "The beautiful city",
        ["MAP"] = "Map",
        ["GAME"] = "Exit Game",
        ["LEAVE"] = "Return to Server List",
        ["QUIT"] = "Return to Desktop",
        ["INFO"] = "Information",
        ["STATS"] = "Statistics",
        ["SETTINGS"] = "Settings",
        ["GALLERY"] = "Gallery",
        ["KEYBIND"] = "Main Keybinds",
        ["EDITOR"] = "Rockstar Editor",
        ["SERVER_NAME"] = "Server Name",
        ["SERVER_TEXT"] = "Welcome to our city",
        ["SERVER_DISCORD"] = "discord.gg"
    }
}
```
