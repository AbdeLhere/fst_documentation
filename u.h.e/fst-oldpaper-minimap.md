---
cover: ../.gitbook/assets/old_paper_map_thumb.png
coverY: -492.44444444444446
---

# fst-oldpaper-minimap

Handcrafted. Timeless. Drawn by Hand.

FST Old Paper Minimap is a fully standalone and customizable FiveM minimap inspired by old navigation charts and sketchbooks. The map combines the original GTA layout with a hand-made paper aesthetic created by artist Doha E., giving the world a unique illustrated appearance while keeping roads and navigation clear.

### Features

{% embed url="https://youtu.be/5CNZmaIwmqE" %}

### About

This map focuses on atmosphere and artistic presentation rather than modern styling. The illustrated paper textures, hand-made icons / details, and soft colors create a unique navigation experience while preserving the original GTA V layout.

Everything can be configured directly inside `config.lua`, allowing you to customize the map to fit your server.

### Requirements

{% hint style="warning" %}
Optional: `ox_lib` (only required if the `/mapcolors` command is enabled)
{% endhint %}

### Installation

1. Place the resource inside your server resources folder.
2. Make sure the folder name is exactly:

```cfg
fst_oldpaper_minimap
```

3. Add the resource to your `server.cfg`:

```cfg
ensure fst_oldpaper_minimap
```

4. (Optional) Install and start `ox_lib` before this resource if you want to use the `/mapcolors` command.
5. Adjust `config.lua` to your liking and restart the resource.

### Using with Enhanced Minimap

If you own **fst\_enhanced\_minimap** and want to use the Old Paper overlays with it:

#### Setup

1. Set compatibility mode in `config.lua`:

```lua
Config.using_the_enhanced_minimap = true
```

2. Ensure both resources:

```cfg
ensure fst_enhanced_minimap
ensure fst_oldpaper_minimap
```

3. Restart your server.

The Old Paper Minimap will only provide its textures and overlays while Enhanced Minimap handles all UI, radar, tablet, and player features.

{% hint style="info" %}
If you are not using Enhanced Minimap:
{% endhint %}

```lua
Config.using_the_enhanced_minimap = false
```

The Old Paper Minimap will run independently with all features enabled.

### Config

```lua
Config = {}
Config.debug = false                 -- Set to false to disable debug messages
Config.enable_map_zoom_levels = true -- Enable different map zoom levels

--========================================================================================--
--  ENHANCED MINIMAP COMPATIBILITY
--  Set to true if you're using fst_enhanced_minimap alongside this resource
--
--  When enabled:
--  - All Western Minimap features are DISABLED (zoom, radar, blur, pause menu, commands, tile system)
--  - Only the overlay textures in the stream folder are provided
--  - Enhanced Minimap detects and loads Western textures automatically
--  - Use Enhanced Minimap's tablet to toggle Western overlays on/off
--
--  When disabled (false):
--  - Western Minimap runs standalone with all features enabled
--========================================================================================--
Config.using_the_enhanced_minimap = true

Config.ZoomLevels = {
  { index = 0, zoomScale = 0.96,  zoomSpeed = 0.9, scrollSpeed = 0.08, tilesX = 0.0, tilesY = 0.0 },
  { index = 1, zoomScale = 1.6,   zoomSpeed = 0.9, scrollSpeed = 0.08, tilesX = 0.0, tilesY = 0.0 },
  { index = 2, zoomScale = 8.6,   zoomSpeed = 0.9, scrollSpeed = 0.08, tilesX = 0.0, tilesY = 0.0 },
  { index = 3, zoomScale = 12.3,  zoomSpeed = 0.9, scrollSpeed = 0.08, tilesX = 0.0, tilesY = 0.0 },
  { index = 4, zoomScale = 24.3,  zoomSpeed = 0.9, scrollSpeed = 0.08, tilesX = 0.0, tilesY = 0.0 },
  { index = 5, zoomScale = 55.0,  zoomSpeed = 0.0, scrollSpeed = 0.1,  tilesX = 2.0, tilesY = 1.0 },
  { index = 6, zoomScale = 450.0, zoomSpeed = 0.0, scrollSpeed = 0.1,  tilesX = 1.0, tilesY = 1.0 },
  { index = 7, zoomScale = 4.5,   zoomSpeed = 0.0, scrollSpeed = 0.0,  tilesX = 0.0, tilesY = 0.0 },
  { index = 8, zoomScale = 11.0,  zoomSpeed = 0.0, scrollSpeed = 0.0,  tilesX = 2.0, tilesY = 3.0 },
}

Config.Radar = {
  zoom = {
    enabled = true,        -- Enable automatic radar zoom
    on_vehicle = 1000,     -- Zoom level when in vehicle (default: 1000)
    on_foot = 1100,        -- Zoom level when on foot (default: 1100)
    check_interval = 1000, -- How often to check zoom in ms (default: 1000)
  },
  disable_blur = true,     -- Disable the blur effect when loading minimap (recommended: true)
}

Config.PauseMenu = {
  enable_color_picker = true, -- Allow players to change colors with a command
  command = "mapcolors",      -- Command to open color picker (/mapcolors)

  -- Default colors (RGB format: 0-255) - Western Theme
  colors = {
    line = { enabled = true, red = 204, green = 119, blue = 34, alpha = 255 },      -- Burnt Orange (western leather)
    background = { enabled = true, red = 101, green = 67, blue = 33, alpha = 115 }, -- Dark Brown (saddle leather)
    pause_bg = { enabled = true, red = 139, green = 90, blue = 43, alpha = 70 },    -- Light Brown (desert sand)
    waypoint = { enabled = true, red = 218, green = 165, blue = 32, alpha = 255 },  -- Goldenrod (western gold)
  },
}

Config.overlays = {
  -------------------
  --- MAP THEMES ---
  -------------------
  mainmaptheme = {
    enabled = true, -- Main desert/western map theme (includes all base and sea variants)
    opacity = 100,  -- Opacity/alpha value (0-100, default: 100)
  },
  -------------------
  --- MAP EXTENSIONS ---
  -------------------
  cayo_perico = {
    enabled = false, -- Cayo Perico map
    opacity = 100,   -- Opacity/alpha value (0-100, default: 100)
  },
  cayo_bridge = {
    enabled = false, -- Cayo Bridge
    opacity = 100,   -- Opacity/alpha value (0-100, default: 100)
  },
  cayo_bridge1 = {
    enabled = false, -- Cayo Bridge V1
    opacity = 100,   -- Opacity/alpha value (0-100, default: 100)
  },
  cayo_bridge2 = {
    enabled = false, -- Cayo Bridge V2
    opacity = 100,   -- Opacity/alpha value (0-100, default: 100)
  },
  -------------------
  --- OVERLAYS  ---
  -------------------
  postales_4 = {
    enabled = false, -- 4-digit postal codes
    opacity = 50,    -- Opacity/alpha value (0-100, default: 100)
  },
  ocrp_postales = {
    enabled = true, -- OCRP postal codes
    opacity = 50,   -- Opacity/alpha value (0-100, default: 100)
  },
  utr_routes = {
    enabled = false, -- Urban/rural route markers
    opacity = 100,   -- Opacity/alpha value (0-100, default: 100)
  },
  zone_names = {
    enabled = false, -- Zone/district names
    opacity = 100,   -- Opacity/alpha value (0-100, default: 100)
  },
  poi_icons = {
    enabled = false, -- Points of interest icons
    opacity = 100,   -- Opacity/alpha value (0-100, default: 100)
  },
  map_key = {
    enabled = false, -- Map key/legend
    opacity = 100,   -- Opacity/alpha value (0-100, default: 100)
  },
}

Config.load_order = {
  "mainmaptheme",  -- Main map theme - loads first (base layer)
  "postales_4",    --
  "ocrp_postales", --
  "utr_routes",    --
  "poi_icons",     --
  "map_key",       --
  "roxwood",       --
  "cayo_perico",   --
  "cayo_bridge",   --
  "cayo_bridge1",  --
  "cayo_bridge2",  --
  "zone_names",    -- Loads last (top layer)
}

```
