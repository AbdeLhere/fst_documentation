---
layout:
  width: default
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
---

# fst-enhanced-minimap

The **FST Enhanced Minimap** is not just a minimap, it's a fully customizable and interactive map management system designed to enhance the player experience on your FiveM server. With a sleek tablet UI, players can manage their minimap overlays, customize their pause menu, and interact with advanced features like postal systems, special maps, and emergency zones. This script is perfect for roleplay servers looking to add a professional and immersive touch to their gameplay.

### **Features**

* <mark style="color:$success;">**Tablet UI**</mark> A modern, interactive tablet interface to manage your minimap.
* <mark style="color:$success;">**Overlay Management**</mark>:
  * Enable/disable overlays like:
    * <mark style="color:$success;">Zone Names (9+ styles)</mark>
    * <mark style="color:$success;">Rural Routes (+2 styles)</mark>
    * <mark style="color:$success;">Urban Routes (+2 styles)</mark>
    * <mark style="color:$success;">Interstate Highways (+2 styles)</mark>
  * More overlays coming soon!
* <mark style="color:$success;">**Emergency Zones**</mark>:
  * Whitelisted jobs (e.g., BCSO, DPPD, LSPD, LSSD, MCSO, NOOSE, RHPD, SASPA, USAF) can enable zones on the minimap.
  * Configurable to allow anyone to toggle zones.
* <mark style="color:$success;">**Pause Menu Customization**</mark>:
  * Change background colors, waypoint colors, and text highlights in real-time.
* <mark style="color:$success;">**Postal System**</mark>: needs `mnr_postals` [my edited version](https://github.com/AbdeLhere/mnr_postals)
  * Search by postal code.
  * View your current postal.
  * Click anywhere on the map to find its postal.
* <mark style="color:$success;">**Special Maps**</mark>:
  * Enable maps like Roxwood, Cayo Perico, and Cayo Bridge (v1 or v2).
* <mark style="color:$success;">**Theme Customization**</mark>:
  * Change themes for Los Santos and special maps.
  * Download themes from the [fst\_minimap\_themes GitHub repository](https://github.com/AbdeLhere/fst_minimap_themes).
* <mark style="color:$success;">**Sound Effects**</mark>: Custom sound effects when opening the map.
* <mark style="color:$success;">**Framework Compatibility**</mark>: Works with QBX, QB-Core, and ESX frameworks.

***

### **Installation**

Follow these steps to install the FST Enhanced Minimap on your FiveM server.

#### Step 1: Download and Extract

1. Download the script and place it in your server's `resources` folder.
2. Ensure the folder is named `fst_enhanced_minimap`.

#### Step 2: Install Dependencies

Ensure the following dependencies are installed:

* [ox\_lib](https://github.com/CommunityOx/ox_lib)
* [mnr\_postals](https://github.com/AbdeLhere/mnr_postals)

#### Step 3: Ensure

Add the following line to your `server.cfg` if needed:

```plaintext
ensure ox_lib 
ensure mnr_postals 
ensure fst_enhanced_minimap
```

#### Step 4: Optional - Install Themes

1. Download themes from the fst\_minimap\_themes GitHub repository.
2. Replace the contents of `stream/base` with the desired theme folder.

***

### Config

{% code title="config.lua" fullWidth="false" %}
```lua
return {
  debug = false,

  Framework = {
    -- 'esx' | 'qb' | 'qbx'
    type = 'qbx',
  },

  Settings = {
    notifications = {
      -- 'ox' uses ox_lib; or set to 'custom' and implement below
      type = 'ox',
      customFunction = function(message, type, duration, title)
        -- Your custom notify here
      end,
    },
  },

  Options = {
    postalCodes = { enabled = true },    -- Requires mnr_postals
    command     = { enabled = true, command_name = 'minimapm' },
    anim        = { enabled = true },    -- Tablet animation
    HUDHandle   = {
      enabled = false,
      onTabletOpen  = function() end,    -- Hide your HUD here
      onTabletClose = function() end,    -- Show your HUD here
    },
    sounds = {
      volume = 0.5,
      map_sound = true,
    },
    enable_map_zoom_levels = true,
    using_affected_hud     = false,
  },

  -- Default alpha (0-255) for all tiles
  DefaultAlpha = 100,

  -- Overlays grouped by category; one style active per category
  MapCategories = {
    street_names = {
      label = "Zone Names",
      styles = {
        names = {
          label = "Standard",
          tiles = {
            { xOffset = 0, yOffset = 0, txd = "minimap_names_tile_0_0", txn = "0_0", alpha = 100 },
          }
        },
      }
    },

    postal_codes = {
      label = "Postal Codes",
      styles = {
        whitepostales = {
          label = "White Postal Codes",
          tiles = {
            { xOffset = 0, yOffset = 0, txd = "minimap_whitepostales_tile_0_0", txn = "0_0", alpha = 100 },
          }
        },
      }
    },
  },

  -- Emergency departments overlays (job-gated if permissions.enabled = true)
  DepartmentZones = {
    enabled = true,
    permissions = {
      enabled = true,
      allowedJobs = { 'police', 'sheriff' }, -- sample
    },
    departments = {
      lspd = {
        enabled = true,
        label = 'Los Santos Police Department',
        shortLabel = 'LSPD',
        tiles = {
          { xOffset = 0, yOffset = -1, txd = "minimap_lspd_1_0", txn = "1_0", alpha = 100 },
        }
      },
    },
  },

  -- Pause menu color customization
  HudCustomization = {
    enabled = true,
    colors = {
      line       = { red = 255, green = 77,  blue = 77,  alpha = 255 },
      background = { red = 254, green = 88,  blue = 88,  alpha = 115 },
      pause_bg   = { red = 255, green = 77,  blue = 77,  alpha = 70  },
      waypoint   = { red = 255, green = 77,  blue = 77,  alpha = 255 },
    },
    limits = { rgb_min = 0, rgb_max = 255, alpha_min = 50, alpha_max = 255 },
  },

  -- Optional extra maps/overlays
  SpecialTiles = {
    cayo = {
      enabled = true,
      description = "Cayo Perico",
      tiles = {
        { x = 4859.6, y = -5099.9, txd = "cayoPerico", txn = "cayo_tex", alpha = 100, centered = true },
      }
    },
  },
}
```
{% endcode %}

### Exports

```lua
exports.fst_enhanced_minimap:openTablet()
```

```lua
exports.fst_enhanced_minimap:closeTablet()
```

