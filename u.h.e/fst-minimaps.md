---
cover: ../.gitbook/assets/bundle map thumbanel.jpg
coverY: -492.44444444444446
layout:
  width: default
  cover:
    visible: true
    size: full
    mask: none
  title:
    visible: true
  description:
    visible: false
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: true
  metadata:
    visible: true
  tags:
    visible: true
  actions:
    visible: true
  anchors:
    visible: true
---

# FST Minimaps

## **Available Minimaps and Features**

<table data-view="cards"><thead><tr><th></th><th></th><th></th><th data-type="rating" data-max="5"></th><th data-hidden data-card-cover data-type="image">Cover image</th></tr></thead><tbody><tr><td>FrostB Minimap</td><td><strong>POI Icons</strong><br><strong>Routes Lines/Icons</strong><br><strong>Zone Names</strong><br><strong>Cayo Perico</strong><br><strong>Postals</strong></td><td><a href="https://abdelemporium.tebex.io/package/7672849">Purchase Link</a></td><td>3</td><td><a href="../.gitbook/assets/frostb_minimap_thumb.jpg">frostb_minimap_thumb.jpg</a></td></tr><tr><td>Bundle Minimap</td><td><strong>9 Different Themes</strong><br><strong>Modern Zone Names</strong><br><strong>Routes Lines/Icons</strong><br><strong>Cayo Perico</strong><br><strong>Enhanced Minimap V2</strong><br><strong>Postals</strong></td><td><a href="https://abdelemporium.tebex.io/package/7730160">Purchase Link</a></td><td>5</td><td><a href="../.gitbook/assets/bundle map thumbanel.jpg">bundle map thumbanel.jpg</a></td></tr><tr><td>OLD Paper Minimap</td><td><strong>POI Icons</strong><br><strong>Routes Lines/Icons</strong><br><strong>Cayo Perico</strong><br><strong>Enhanced Minimap V2</strong><br><strong>Map Key</strong><br><strong>Postals</strong></td><td><a href="https://abdelemporium.tebex.io/package/7519660">Purchase Link</a></td><td>5</td><td><a href="../.gitbook/assets/sdsde.png">sdsde.png</a></td></tr><tr><td>Burnout Minimap</td><td><strong>Routes Lines/Icons</strong><br><strong>Cayo Perico</strong><br><strong>Enhanced Minimap V2</strong><br><strong>Postals</strong></td><td><a href="https://abdelemporium.tebex.io/package/7655078">Purchase Link</a></td><td>3</td><td><a href="../.gitbook/assets/imagsddsdsde.png">imagsddsdsde.png</a></td></tr><tr><td>Western Minimap</td><td><strong>POI Icons</strong><br><strong>Zone Names</strong><br><strong>Routes Lines/Icons</strong><br><strong>Cayo Perico</strong><br><strong>Enhanced Minimap V2</strong><br><strong>Map Key</strong><br><strong>Postals</strong></td><td><a href="https://abdelemporium.tebex.io/package/fst-western-minimap">Purchase Link</a></td><td>5</td><td><a href="../.gitbook/assets/western_minimap_thumb.jpg">western_minimap_thumb.jpg</a></td></tr></tbody></table>

<table><thead><tr><th width="203.45458984375">Minimap Name</th><th data-type="checkbox">Enhanced Minimap V2</th><th data-type="checkbox">Cayo Perico</th><th width="154.9090576171875" data-type="checkbox">Configurable</th><th>Creator<select><option value="Fqa4L8hfpMf6" label="Pengu" color="blue"></option><option value="xr0WO41u6jcI" label="Cyberhead" color="blue"></option></select></th><th>Free/Paid<select><option value="R74sKabmYCnk" label="Free" color="blue"></option><option value="SyUxlOu9ywQw" label="Paid" color="blue"></option></select></th></tr></thead><tbody><tr><td>OLD Paper Minimap</td><td>true</td><td>true</td><td>true</td><td><span data-option="xr0WO41u6jcI">Cyberhead</span></td><td><span data-option="SyUxlOu9ywQw">Paid</span></td></tr><tr><td>Western Minimap</td><td>true</td><td>true</td><td>true</td><td><span data-option="xr0WO41u6jcI">Cyberhead</span></td><td><span data-option="SyUxlOu9ywQw">Paid</span></td></tr><tr><td>Burnout Minimap</td><td>true</td><td>true</td><td>true</td><td><span data-option="Fqa4L8hfpMf6">Pengu</span></td><td><span data-option="SyUxlOu9ywQw">Paid</span></td></tr><tr><td>Bundle Minimap</td><td>true</td><td>true</td><td>true</td><td><span data-option="Fqa4L8hfpMf6">Pengu</span></td><td><span data-option="SyUxlOu9ywQw">Paid</span></td></tr><tr><td>FrostB Minimap</td><td>false</td><td>true</td><td>true</td><td><span data-option="Fqa4L8hfpMf6">Pengu</span></td><td><span data-option="R74sKabmYCnk">Free</span></td></tr></tbody></table>

### Installation

{% stepper %}
{% step %}
### Place resource

Place the resource inside your server resources folder.\
Make sure the folder name is correct\
Add the resource to your `server.cfg` if needed
{% endstep %}

{% step %}
### Hud Colors

{% hint style="info" %}
(Optional) Install and start `ox_lib` before this resource if you want to use the `/mapcolors` command.
{% endhint %}
{% endstep %}

{% step %}
### Adjust your needs

Adjust `config.lua` to your liking and restart the resource.
{% endstep %}

{% step %}
### Postals

{% code expandable="true" %}
```lua
  postales_4 = { enabled = false, opacity = 100 },
  ocrp_postales = { enabled = false, opacity = 100 },
  oulsen_postales = { enabled = true, opacity = 100 },
```
{% endcode %}

{% hint style="warning" %}
Enable only one postal set. Textures are supplied by [**fst\_minimap\_postals** ](https://github.com/AbdeLhere/fst_minimap_postals)\
so make sure to install the dependency first before enabling postals

<table data-view="cards"><thead><tr><th></th><th data-hidden data-card-cover data-type="image">Cover image</th></tr></thead><tbody><tr><td>Postals Textures<br><a href="https://github.com/AbdeLhere/fst_minimap_postals">Download</a></td><td><a href="../.gitbook/assets/postal textures thumbanel free.jpg">postal textures thumbanel free.jpg</a></td></tr></tbody></table>
{% endhint %}
{% endstep %}

{% step %}
### Config Example

{% code expandable="true" %}
```lua
Config = {}
Config.debug = true
Config.enable_map_zoom_levels = true
Config.using_the_enhanced_minimap = false

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
    enabled = false,       -- Enable automatic radar zoom
    on_vehicle = 1000,     -- Zoom level when in vehicle (default: 1000)
    on_foot = 1100,        -- Zoom level when on foot (default: 1100)
    check_interval = 1000, -- How often to check zoom in ms (default: 1000)
  },
  disable_blur = true,     -- Disable the blur effect when loading minimap (recommended: true)
}

Config.PauseMenu = {
  enable_color_picker = true, -- Allow players to change colors with a command
  command = "mapcolors",      -- Command to open color picker (/mapcolors)

  -- Default colors (RGB format: 0-255) - Burnout theme
  colors = {
    line = { enabled = false, red = 255, green = 114, blue = 24, alpha = 255 },     -- Burnt Orange (western leather)
    background = { enabled = false, red = 94, green = 28, blue = 8, alpha = 200 },  -- Dark Brown (saddle leather)
    pause_bg = { enabled = false, red = 94, green = 28, blue = 8, alpha = 200 },    -- Light Brown (desert sand)
    waypoint = { enabled = false, red = 255, green = 114, blue = 24, alpha = 255 }, -- Goldenrod (western gold)
  },
}

Config.overlays = {
  -- Enable only one postal set. Textures are supplied by fst_minimap_postals_op ⚠️
  postales_4 = { enabled = false, opacity = 100 },
  ocrp_postales = { enabled = false, opacity = 100 },
  oulsen_postales = { enabled = true, opacity = 100 },
  -------------------
  modernZoneNames = { enabled = true, opacity = 100 },
  --- MAP THEMES ---
  -------------------
  -- Opacity/alpha value (0-100, default: 100)
  Amethyst = { enabled = false, opacity = 100 },
  AmethystCayo = { enabled = false, opacity = 100 },

  Emerald = { enabled = false, opacity = 100 },
  EmeraldCayo = { enabled = false, opacity = 100 },

  Graphite = { enabled = false, opacity = 100 },
  GraphiteCayo = { enabled = false, opacity = 100 },

  Midnight = { enabled = false, opacity = 100 },
  MidnightCayo = { enabled = false, opacity = 100 },

  Ruby = { enabled = true, opacity = 100 },
  RubyCayo = { enabled = true, opacity = 100 },

  Sakura = { enabled = false, opacity = 100 },
  SakuraCayo = { enabled = false, opacity = 100 },

  Sapphire = { enabled = false, opacity = 100 },
  SapphireCayo = { enabled = false, opacity = 100 },

  Sherryup = { enabled = false, opacity = 100 },
  SherryupCayo = { enabled = false, opacity = 100 },

  Sunset = { enabled = false, opacity = 100 },
  SunsetCayo = { enabled = false, opacity = 100 },
}


Config.load_order = {
  "Amethyst",
  "AmethystCayo",
  "Emerald",
  "EmeraldCayo",
  "Graphite",
  "GraphiteCayo",
  "Midnight",
  "MidnightCayo",
  "Ruby",
  "RubyCayo",
  "Sakura",
  "SakuraCayo",
  "Sapphire",
  "SapphireCayo",
  "Sherryup",
  "SherryupCayo",
  "Sunset",
  "SunsetCayo",
  "postales_4",
  "ocrp_postales",
  "oulsen_postales", -- Postal numbers draw above map themes and extensions
  "modernZoneNames"
}

```
{% endcode %}
{% endstep %}

{% step %}
### Custom Installation

{% tabs %}
{% tab title="Bundle Minimap" %}
{% hint style="warning" %}
For **Cayo Perico** installation, an asset called `fst_bundle_minimap_cayo` is included. You first need to install it, as it contains all Cayo Perico minimaps. This helps avoid having a large number of unnecessary textures on your server if your not using Cayo Perico.
{% endhint %}
{% endtab %}
{% endtabs %}


{% endstep %}
{% endstepper %}

### Using with Enhanced Minimap

{% hint style="warning" %}
If you own **fst\_enhanced\_minimap\_v2** and want to use one of this minimaps with it, follow this guide
{% endhint %}

{% stepper %}
{% step %}
### Set compatibility

<pre class="language-lua"><code class="lang-lua"><strong>Config.using_the_enhanced_minimap = true
</strong></code></pre>
{% endstep %}

{% step %}
### Ensure both resources

```cfg
ensure fst_enhanced_minimap_v2
ensure fst_oldpaper_minimap
```
{% endstep %}

{% step %}
### Restart your server.

{% hint style="info" %}
The Old Paper Minimap will only provide its textures and overlays while Enhanced Minimap handles all UI, radar, tablet, and player features.
{% endhint %}
{% endstep %}
{% endstepper %}

{% hint style="warning" %}
If you are not using Enhanced Minimap:\
`Config.using_the_enhanced_minimap = false`\
The Old Paper Minimap will run independently with all features enabled.
{% endhint %}
