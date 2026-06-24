---
cover: ../.gitbook/assets/old_paper_map_thumb.png
coverY: -492.44444444444446
---

# fst-oldpaper-minimap

Handcrafted. Timeless. Drawn by Hand.

FST Old Paper Minimap is a fully standalone and customizable FiveM minimap inspired by old navigation charts and sketchbooks. The map combines the original GTA layout with a hand-made paper aesthetic created by artist Doha E., giving the world a unique illustrated appearance while keeping roads and navigation clear.

### Features

{% embed url="https://youtu.be/GZM661pj64s" %}

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
