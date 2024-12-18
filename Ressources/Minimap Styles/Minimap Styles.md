---
icon: clipboard-question
cover: ../../.gitbook/assets/0A8704FA-8499-4DE1-9192-14D4A6E56769.jpg
coverY: 0
layout:
  cover:
    visible: true
    size: full
  title:
    visible: false
  description:
    visible: false
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: true
---

# Overview

### **Installation / Information 📖**

#### Step 1: Remove Old Minimap Script

* Start by removing any old minimap script from your resources folder.

#### Step 2: Cleanup

* Open **Visual Studio Code**.
* Press `CTRL + K + O` to open a folder.
* Select your server folder and press `Open`.
* Press `CTRL + SHIFT + F` to search for the following lines:
  * `SetMapZoomDataLevel`
  * `SetRadarZoom`
  * `SetRadarAsInteriorThisFrame` " remove this one only if you have specific problems with the map "
* Remove these lines if found, **but do not remove them from the new script!**

#### Step 3: Ensuring the New Script

* Drag and drop the new resource into your resources folder.
* Open your `server.cfg` file and add the following line after your framework, replacing `"script-name"` with your actual script name (e.g., `abl-minimap-X8-OP`):

```lua
ensure "script-name"
```

* Restart your server.

#### Step 4: Configuration

* You can adjust the background opacity in `Config.Options.opacity` (Max: 200, Min: 0).
* Pause Menu colors can be edited in `Config.Options.RedGreenBlueAlpha`. You can use the [RGBA Color Picker](https://rgbacolorpicker.com/) to choose your preferred colors.
* **Note:** If you change colors, please avoid modifying `["ALPHA"] = 0.8`.
* To customize titles, refer to `Config.Options.Header`.

Here's a sample configuration snippet:

```lua
Config = Config or {}

Config.Options = {
    enableBackground = true,   -- Toggle background change on/off
    opacity = 90,               -- Change background opacity
    ChangeHeaderNames = true,  -- Toggle header name changes on/off
    enableColorChanges = true, -- Toggle all color changes on/off
    RedGreenBlueAlpha = {

        --- [[[[[[[[[[[[[  https://rgbacolorpicker.com  ]]]]]]]]]]]]]
        --- [[[[[[[[[[[[[  https://rgbacolorpicker.com  ]]]]]]]]]]]]]
        --- [[[[[[[[[[[[[  https://rgbacolorpicker.com  ]]]]]]]]]]]]]
        --- [[[[[[[[[[[[[  https://rgbacolorpicker.com  ]]]]]]]]]]]]]
        --- [[[[[[[[[[[[[  https://rgbacolorpicker.com  ]]]]]]]]]]]]]

        HudLineColor = {
            ["RED"] = 0,
            ["GREEN"] = 0,
            ["BLUE"] = 0,
            
           ---- Dont change ALPHA ❌
            ["ALPHA"] = 0.8,
        },
        PauseMenuStyleColor = {
            ["RED"] = 62,
            ["GREEN"] = 62,
            ["BLUE"] = 62,
            
           ---- Dont change ALPHA ❌
            ["ALPHA"] = 0.8,
        },
        MapWaypointColor = {
            ["RED"] = 189,
            ["GREEN"] = 0,
            ["BLUE"] = 255,

           ---- Dont change ALPHA ❌
            ["ALPHA"] = 0.8,
        },
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
        ["SERVER_DISCORD"] = "discordlink.gg"
    }
}

```

### **Useful Links 😊**

* [Join Our Discord](https://discord.gg/jgM5jW3rrN)
* [Visit Our Tebex Store](https://abdelemporium.tebex.io/)
* [Donations](https://paypal.me/ablframework?country.x=FR\&locale.x=fr_FR)
