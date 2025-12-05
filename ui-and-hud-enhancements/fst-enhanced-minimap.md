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
    -- 'esx' | 'qb' | 'qbx' | 'standalone'
    type = 'standalone',
  },

  Fallbacks = {
    playername = 'hey its me',    -- Used for standalone mode
    jobname = 'Frostbyte Studios' -- Used for standalone mode
  },

  Settings = {
    -- 'tablet' | 'oxlib' - Choose UI type
    ui_type = 'oxlib',
    
    notifications = {
      -- 'ox' uses ox_lib; or set to 'custom' and implement below
      type = 'ox',
      customFunction = function(message, type, duration, title)
        print('[CUSTOM NOTIFY] ' .. message)
      end,
    },
  },

  Options = {
    postalCodes = { enabled = true },    -- Requires mnr_postals
    command     = { enabled = true, command_name = 'minimapm' },
    keybind     = { enabled = true, default = "F6" },
    anim        = { enabled = true },    -- Tablet animation
    HUDHandle   = {
      enabled = true,
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

  -- Overlay conflicts (prevent similar overlays being active together)
  OverlayConflicts = {
    interstates = "interstates2",
    interstates2 = "interstates",
    rural = "rural2",
    rural2 = "rural",
    urban = "urban2",
    urban2 = "urban"
  },

  -- Map overlays grouped by category
  MapCategories = {
    street_names = {
      label = "Zone Names",
      allowMultiple = false, -- Only one style active at a time
      styles = {
        names = {
          label = "Standard Names",
          tiles = {
            { xOffset = 0, yOffset = 0, txd = "minimap_names_tile_0_0", txn = "0_0", alpha = 100 },
            -- ... more tiles
          }
        },
        npcyan = { label = "Cyan Modern Names" },
        npblue = { label = "Blue Modern Names" },
        -- ... more color variants
      }
    },

    postal_codes = {
      label = "Postal Codes",
      allowMultiple = false,
      styles = {
        whitepostales = { label = "White Postal Codes" },
        blackpostales = { label = "Black Postal Codes" }
      }
    },

    standard_routes = {
      label = "Standard Routes",
      allowMultiple = true, -- Multiple styles can be active
      styles = {
        interstates = { label = "Interstate Signs" },
        rural = { label = "Rural Routes" },
        urban = { label = "Urban Routes" }
      }
    },

    san_andreas_routes = {
      label = "San Andreas Routes",
      allowMultiple = true,
      styles = {
        interstates2 = { label = "SA Interstate Signs" },
        rural2 = { label = "SA Rural Routes" },
        urban2 = { label = "SA Urban Routes" }
      }
    }
  },

  -- Emergency departments overlays (job-gated if permissions enabled)
  DepartmentZones = {
    enabled = true,
    permissions = {
      enabled = false, -- Enable job-based access control
      allowedJobs = { 'police', 'sheriff', 'trooper' },
    },
    departments = {
      lspd = {
        enabled = true,
        label = 'Los Santos Police Department',
        shortLabel = 'LSPD',
        tiles = {
          { xOffset = 0, yOffset = -1, txd = "minimap_lspd_1_0", txn = "1_0", alpha = 100 },
          -- ... more tiles
        }
      },
      bcso = { enabled = true, label = 'Blaine County Sheriff' },
      lssd = { enabled = true, label = 'Los Santos Sheriff Department' },
      -- ... more departments (mcso, rhpd, dppd, saspa, usaf, nose)
    },
  },

  -- HUD color customization
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
    roxwood = { enabled = true, description = "Roxwood County" },
    cayoBridge1 = { enabled = true, description = "Cayo Bridge V1" },
  },
}
```
{% endcode %}



---

### **Forced Settings System**

You can enable server-side control of the minimap using the **Forced Settings System**. This prevents players from toggling overlays or department zones and ensures only selected overlays/departments are loaded.

#### **How it works**

Set `Options.forcePlayerSettings = true` in your `config.lua`:

* Players **cannot** toggle overlays or departments.
* Only overlays or departments with `forced = true` will be loaded.
* Player preferences are ignored and **not saved**.
* UI controls are **locked/disabled** for players.

#### **How to use**

1. Open your `config.lua` and set:

```lua
Options = {
    forcePlayerSettings = true,
    -- other options...
}
```

2. Find the overlay styles in `MapCategories` and set `forced = true` for the ones you want active:

```lua
street_names = {
    styles = {
        names  = { forced = true },   -- This overlay will show
        npcyan = { forced = false }   -- This overlay won't show
    }
}
```

3. Find the departments in `DepartmentZones` and set `forced = true` for the ones you want active:

```lua
departments = {
    lspd = { forced = true },  -- This department will show
    bcso = { forced = false }  -- This department won't show
}
```

4. Restart the resource. Players will now only see the overlays and departments you selected.

#### **Example**

```lua
-- MapCategories example
street_names = {
    styles = {
        names  = { forced = true },
        npcyan = { forced = false }
    }
}

-- DepartmentZones example
departments = {
    lspd = { forced = true },
    bcso = { forced = false }
}
```

{% hint style="warning" %}
Once enabled, players **cannot** change overlays or departments manually. Make sure your forced selections are correct before restarting the resource.
{% endhint %}

### FAQ

#### <mark style="color:yellow;">I have a custom map like Roxwood. Is it supported?</mark>

Yes. Custom maps are fully supported. The config already includes premade entries for maps like **Roxwood**, **Cayo Perico**, and **Cayo Bridge (v1/v2)**.\
You can also add your own map by editing the `SpecialTiles` section in the config.

Need help? Contact me and I’ll assist you with adding it.

***

#### <mark style="color:yellow;">Why is my minimap pulsing or flickering?</mark>

This usually happens when two scripts are trying to control minimap zoom levels at the same time.\
To fix this issue, set the following in your config:

```lua
using_affected_hud = true
```

***

#### <mark style="color:yellow;">How can I change the theme of the map?</mark>

You can download themes that support special maps like Roxwood from this repository:\
[https://github.com/AbdeLhere/fst\_minimap\_themes](https://github.com/AbdeLhere/fst_minimap_themes)

Replace the contents of the `stream/base` folder with your desired theme.\
If you already have your own minimap, it's recommended to use one without zone names or postal overlays, then replace the textures in `stream/base`.

***

#### <mark style="color:yellow;">Do you accept custom maps?</mark>

Yes. Custom maps are accepted.\
Open a ticket on the Discord server: [https://discord.gg/DQDsp5ehvJ](https://discord.gg/DQDsp5ehvJ)\
Or contact me directly on Discord: `abdel4999`

***

#### <mark style="color:yellow;">Can I edit the department zones?</mark>

Yes. Department zones are overlays (textures) like any other.\
You will need tools like **Photoshop** and **OpenIV** to edit them.\
If you're not comfortable doing it yourself, you can request custom work.

***

#### <mark style="color:yellow;">Can I disable overlays or departments?</mark>

Yes. You can enable or disable any overlay or department at any time in the `config.lua`.\
Just set `enabled = false` for anything you don't want active.

***

#### <mark style="color:yellow;">I don’t like the tablet UI. Can I use something else?</mark>

Yes. You can use the ox\_lib UI instead by setting the following in your config:

```lua
ui_type = 'oxlib'
```

Options: `'tablet'` or `'oxlib'`

***

#### <mark style="color:yellow;">Are you adding more overlays in the future?</mark>

Yes. More overlays are planned.\
Suggestions are welcome, feel free to contact me or open a ticket.

### Exports

```lua
exports.fst_enhanced_minimap:openTablet()
```

```lua
exports.fst_enhanced_minimap:closeTablet()
```

### Creating new overlays

you can absolutely make more zones and even put them in a new category if you want to separate them from the department zones. the script is fully driven by the config, so as long as you follow the same structure, it will recognize your new zones.

each category, like `street_names`, `postal_codes`, or `standard_routes`, is just a container for one or more styles or zones. you can create your own, for example a “city zones” category.

inside a category, each style or zone has a few key things:

* **label** – the name displayed in-game
* **description** – a short explanation
* **tiles** – the minimap overlays that make up the zone. each tile points to a `txd`/`txn` name from a **ytd file** that you will need to create
* optional: **icon**, **color**, **allowMultiple**

**example**:

```lua
city_zones = {
  label = "city zones",
  description = "custom city overlays like parks and city limits",
  icon = "fa-solid fa-city",
  color = "#3b82f6",
  allowMultiple = true,
  styles = {
    parks = {
      label = "city parks",
      description = "all park areas",
      tiles = {
        { xOffset = 0, yOffset = 0,  txd = "minimap_parks_0_0", txn = "0_0", alpha = 100 },
        { xOffset = 1, yOffset = 0,  txd = "minimap_parks_0_1", txn = "0_1", alpha = 100 },
        { xOffset = 0, yOffset = -1, txd = "minimap_parks_1_0", txn = "1_0", alpha = 100 },
        { xOffset = 1, yOffset = -1, txd = "minimap_parks_1_1", txn = "1_1", alpha = 100 }
      }
    },
    city_limits = {
      label = "city limits",
      description = "outline of city boundaries",
      tiles = {
        { xOffset = 0, yOffset = 0,  txd = "minimap_citylimits_0_0", txn = "0_0", alpha = 100 },
        { xOffset = 1, yOffset = 0,  txd = "minimap_citylimits_0_1", txn = "0_1", alpha = 100 }
      }
    }
  }
}

```

{% hint style="warning" %}
important, you will need to create the ytd files for each zone, like `minimap_parks_0_0.ytd` or `minimap_citylimits_0_0.ytd`. the config just tells the script which tiles to load, the visuals come from your ytd files.
{% endhint %}

for the tile positions, you could technically use real world coordinates like `x = 4859.6, y = -5099.9` for a tile, but the easier way is to use **xOffset** and **yOffset**.

in the same way the default tile grid works, this resource places tiles based on offsets. the position of a tile is calculated from an origin point. the designers of gta 5 chose the origin to be the top-left corner of the map. this means that the top-left tile of the default map is at offset `x = 0` and `y = 0`.

the sign of the offset determines the direction in which to place a tile, while the number determines how far (in number of tiles) to place it in that direction. one unit equals one tile, which is 4500 in-game units.

<figure><img src="../.gitbook/assets/fst (2).png" alt=""><figcaption></figcaption></figure>

{% hint style="success" %}
so basically, follow the config structure, create your ytd files, use offsets for positioning, and the script will load your new zones. you can make as many as you want.
{% endhint %}
