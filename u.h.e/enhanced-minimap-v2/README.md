# Admin Permissions System

## How It Works

The admin permissions system controls who can make server-wide changes to the minimap. 

**When enabled with force flags:**
- Authorized admins see an **"Admin Mode" button** in the tablet to control server-wide settings
- Their changes apply to ALL players on the server
- Regular players see their tablet in read-only mode (they can view but not change locked features)

**When disabled:**
- No Admin Mode button appears
- Everyone controls their own minimap settings independently
- Changes only affect the individual player

## Configuration

```lua
InGamePermissionsSystem = {
  enabled = true,  -- Enable/disable the entire admin system
  
  -- Lock specific features (true = only admins can change):
  forceOverlays = false,        -- Map overlays, postal codes, routes, zones
  forceVisuals = false,         -- HUD colors, minimap border, waypoint
  forceDisplaySettings = false, -- Weather tiles/icons, day/night system
  
  -- Grant admin access via ACE permissions:
  ace = { 'group.admin', 'fst_minimap.admin' },
  
  -- Grant admin access via player identifiers:
  identifiers = { 'discord:123456789', 'license:abc123...' },
  
  -- Grant admin access via framework ranks:
  framework = { 
    esx = { 'superadmin', 'admin' }, 
    qbcore = { 'god', 'admin' }, 
    qbox = { 'god', 'admin' } 
  },
}
```

### enabled
- `true` = Admin system is active. Only authorized players can make changes that affect everyone.
- `false` = No restrictions. Everyone controls their own minimap settings independently.

**Important:** If `enabled = true` but **all force flags are `false`**, the system loads only the default settings from config.lua. No Admin Mode button appears and there's no server-wide control - players get the defaults you set in the config.

### Force Flags
When you set a force flag to `true`:
1. That feature becomes **locked for regular players** (read-only)
2. Authorized admins get an **"Admin Mode" button** in their tablet
3. Admins use the Admin Mode menu to control that feature **server-wide** (changes apply to everyone)

When force flags are `false`:
- Players can customize those features freely (not locked)
- Changes only affect their own view

**Force flag options:**
- **forceOverlays** - Controls all map overlays (postal codes, routes, department zones, map themes)
- **forceVisuals** - Controls HUD colors (minimap border, waypoint color, pause menu background)
- **forceDisplaySettings** - Controls weather and day/night display options

**Note:** If `enabled = true` but all force flags are `false`, everyone uses the default config settings with no admin control.

### Granting Admin Access

You can use any combination of these three methods:

**1. ACE Permissions** (server.cfg)
```cfg
add_ace group.admin fst_minimap.admin allow
```

**2. Player Identifiers** (config.lua)
```lua
identifiers = {
  'discord:907923629226983425',  -- Get from Discord (right-click user → Copy User ID)
  'steam:110000123456789',       -- Steam hex ID
  'license:abc123...',           -- Rockstar license
  'fivem:123456',                -- FiveM ID
}
```

To find a player's identifiers, run this in your server console:
```
fst_whoami <serverID>
```

**3. Framework Ranks** (config.lua)
```lua
framework = {
  esx = { 'superadmin', 'admin' },
  qbcore = { 'god', 'admin' },
  qbox = { 'god', 'admin' },
}
```

## Examples

**Everyone controls their own minimap:**
```lua
InGamePermissionsSystem = {
  enabled = false,
}
```

**Only admins can change everything:**
```lua
InGamePermissionsSystem = {
  enabled = true,
  forceOverlays = true,
  forceVisuals = true,
  forceDisplaySettings = true,
  ace = { 'group.admin' },
}
```

**Admins control overlays, players customize colors:**
```lua
InGamePermissionsSystem = {
  enabled = true,
  forceOverlays = true,
  forceVisuals = false,
  forceDisplaySettings = false,
  identifiers = { 'discord:123456789' },
}
```

# Player Settings & Controls

## Player Display Preferences

Controls what features players can access from the tablet and whether their choices are saved.

```lua
playerSettings = {
  allowOverlayControl   = true, -- Let players toggle overlays (postal codes, routes, zones)
  allowWeatherControl   = true, -- Let players toggle weather tiles/icons
  allowDayNightControl  = true, -- Let players toggle day/night icon and map theme
  allowTileAlphaControl = true, -- Let players adjust overlay opacity sliders
  allowMapThemeControl  = true, -- Let players choose base map color themes
  allowLinkedOverlays   = true, -- Let players toggle linked-overlay auto-sync
  allowDatasetControl   = true, -- Let players switch postal code types
  allowPauseMenuControl = true, -- Let players change pause menu background
  savePlayerPrefs       = true, -- Save player preferences (KVP storage)
}
```

**Each setting:**
- `true` = Feature is available in the tablet for players to use
- `false` = Feature is hidden/disabled for players

**savePlayerPrefs:**
- `true` = Player choices are saved and restored on reconnect
- `false` = All player settings reset every time they join the server

**Note:** When `InGamePermissionsSystem.forceOverlays = true`, overlays are locked even if `allowOverlayControl = true`. The force flag takes priority.

---

## Postal Code System

```lua
postalCodes = {
  enabled = true,   -- Enable/disable the entire postal code system
  dataset = 'ocrp', -- Which postal code set to use
}
```

**enabled:**
- `true` = Postal code system works (players can toggle postal overlays in the tablet)
- `false` = Postal code system is completely disabled (no postal options appear in-game)

**dataset options:**
- `'fourdigits'` = Standard 4-digit postal codes (~1687 codes)
- `'ocrp'` = OCRP postal codes
- `'oulsen'` = Oulsen postal codes

---

## Opening the Tablet

### Command

```lua
command = {
  enabled = true,
  command_name = 'minimapm',
}
```

- `enabled = true` → Players can type `/minimapm` (or your custom name) to open the tablet
- `enabled = false` → Command is disabled (only keybind works)
- `command_name` → Change the command (e.g., `'map'` makes it `/map`)

### Keybind

```lua
keybind = {
  enabled = true,
  default = "F6",
}
```

- `enabled = true` → Players can press the key to open the tablet
- `enabled = false` → Keybind is disabled (only command works)
- `default` → Default key (players can change it in FiveM settings)

---

## Tablet Animation

```lua
tablet_anim = true,
```

- `true` = Player pulls out a tablet with animation
- `false` = No animation, tablet opens instantly

---

## Custom HUD Integration

Use this if you have a custom HUD resource that needs to hide when the tablet opens.

```lua
HUDHandle = {
  enabled = false,
  onTabletOpen = function()
    -- Add code to hide your HUD here
    -- Example: exports['my_hud']:Hide()
  end,
  onTabletClose = function()
    -- Add code to show your HUD here
    -- Example: exports['my_hud']:Show()
  end
}
```

**enabled:**
- `true` = Your custom functions run when tablet opens/closes
- `false` = No custom HUD handling (default GTA HUD behavior)

---

## Sound Settings

```lua
sounds = {
  volume = 0.5,     -- Sound volume (0.0 = silent, 1.0 = full volume)
  map_sound = true, -- Play sounds when opening/closing the tablet
}
```

**volume:**
- Range: `0.0` to `1.0`
- `0.5` = 50% volume (recommended)

**map_sound:**
- `true` = Sounds enabled
- `false` = Sounds disabled (silent)

# Day / Night System

Automatically switches map icons and themes based on the in-game time.

```lua
dayNightSystem = {
  enabled    = true, -- Enable/disable the entire day/night system
  dayStart   = 6,    -- Hour when day begins (0-23)
  nightStart = 21,   -- Hour when night begins (0-23)
  
  day = { 
    tile = "DAY_ICON",      -- Icon overlay to show during day
    label = "Day",          -- Display label
    mapTheme = nil          -- Optional: map theme overlay for daytime
  },
  
  night = { 
    tile = "NIGHT_ICON",    -- Icon overlay to show at night
    label = "Night",        -- Display label
    mapTheme = "NIGHT_MAP"  -- Optional: map theme overlay for nighttime
  },
  
  -- Per custom-map day/night theme overrides
  customMapThemes = {
    cayo_perico = { day = nil, night = "NIGHT_CAYO" },
    -- roxwood = { day = nil, night = nil },
  },
}
```

## How It Works

- At `dayStart` hour (default 6 AM), the system switches to day mode
- At `nightStart` hour (default 9 PM), the system switches to night mode
- The configured icon and map theme (if set) automatically load based on time

## enabled

- `true` = Day/night system is active (icon and theme switch with time)
- `false` = System is completely disabled (no day/night options appear in-game)

## Time Settings

**dayStart:**
- Hour (0-23) when daytime begins
- Default: `6` (6:00 AM)
- Example: `5` = starts at 5:00 AM

**nightStart:**
- Hour (0-23) when nighttime begins
- Default: `21` (9:00 PM)
- Example: `19` = starts at 7:00 PM

## Day / Night Configuration

Each phase (day/night) has three properties:

**tile:**
- Icon overlay key that appears on the minimap
- Must match an overlay key in `cl_overlays.lua`
- Example: `"DAY_ICON"` shows a sun icon

**label:**
- Display name shown in the tablet UI
- Can be any text you want

**mapTheme:**
- Optional full-map color theme that loads with this phase
- Set to an overlay key (like `"NIGHT_MAP"`) or `nil` to disable
- When set, the entire map changes color during this phase

## Custom Map Themes

Override day/night themes for specific custom maps (Cayo Perico, Roxwood, etc.)

```lua
customMapThemes = {
  cayo_perico = { day = nil, night = "NIGHT_CAYO" },
}
```

- **Key** must match a `customMaps` entry name (e.g., `cayo_perico`)
- **day/night** values must match overlay keys in `cl_overlays.lua` or `nil`
- `nil` = no theme override for that phase on this custom map

**Example:**
- When night begins and player is on Cayo Perico island, `"NIGHT_CAYO"` theme loads
- When day begins, no special theme loads (`day = nil`)

## Examples

**Disable day/night system entirely:**
```lua
dayNightSystem = {
  enabled = false,
}
```

**Day starts at 5 AM, night at 8 PM:**
```lua
dayNightSystem = {
  enabled = true,
  dayStart = 5,
  nightStart = 20,
}
```

**No map themes, icons only:**
```lua
dayNightSystem = {
  enabled = true,
  dayStart = 6,
  nightStart = 21,
  day = { tile = "DAY_ICON", label = "Day", mapTheme = nil },
  night = { tile = "NIGHT_ICON", label = "Night", mapTheme = nil },
}
```


# Weather System

Automatically displays weather overlays and icons based on the current in-game weather.

```lua
weatherSystem = {
  enabled = {
    tiles = true, -- Show full-map weather overlays (clouds/rain/snow)
    icons = true, -- Show weather logo icons on the minimap
  },
  
  weathers = {
    CLEAR      = { enabled = true, tile = "CLEAR", icon = "CLEAR_LOGO", label = "Clear" },
    RAIN       = { enabled = true, tile = "RAIN", icon = "RAIN_LOGO", label = "Rain" },
    THUNDER    = { enabled = true, tile = "THUNDER", icon = "THUNDER_LOGO", label = "Thunderstorm" },
    SNOW       = { enabled = true, tile = "SNOW", icon = "SNOW_LOGO", label = "Snow" },
    -- ... more weather types
  }
}
```

## How It Works

- The script detects the current in-game weather (CLEAR, RAIN, THUNDER, SNOW, etc.)
- It loads the matching tile overlay and/or icon from the `weathers` table
- Both tiles and icons update automatically when weather changes

## enabled

**tiles:**
- `true` = Full-map weather overlays appear (clouds, rain, snow covering the map)
- `false` = No weather tile overlays

**icons:**
- `true` = Weather logo icons appear on the minimap
- `false` = No weather icons

**Important:** If **both** `tiles` and `icons` are `false`, the entire weather system is disabled in-game (no weather options appear).

## Weather Definitions

Each weather type has four properties:

**enabled:**
- `true` = This weather type is active (shows tile/icon when detected)
- `false` = This weather type is disabled (no overlay when detected)

**tile:**
- Overlay key for the full-map weather overlay
- Must match an overlay key in `cl_overlays.lua`
- Example: `"RAIN"` shows rain clouds across the map

**icon:**
- Overlay key for the weather logo icon
- Must match an overlay key in `cl_overlays.lua`
- Example: `"RAIN_LOGO"` shows a rain icon on the minimap

**label:**
- Display name shown in the tablet UI
- Can be any text you want

## Available Weather Types

The script supports these GTA weather types:

- **CLEAR** - Clear skies
- **EXTRASUNNY** - Extra sunny day
- **RAIN** - Rainy weather
- **DRIZZLE** - Light drizzle (uses RAIN tile/icon)
- **THUNDER** - Thunderstorm with lightning
- **CLOUDS** - Cloudy skies
- **OVERCAST** - Overcast gray skies
- **FOGGY** - Foggy conditions
- **SNOWLIGHT** - Light snow
- **BLIZZARD** - Heavy blizzard
- **SNOW** - Snow
- **XMAS** - Christmas snow
- **CLEARING** - Clearing skies
- **NEUTRAL** - Neutral weather
- **SMOG** - Smoggy conditions
- **HALLOWEEN** - Halloween themed weather
- **HALLOWEEN_RAIN** - Halloween rain
- **HALLOWEEN_SNOW** - Halloween snow

## Examples

**Disable weather system entirely:**
```lua
weatherSystem = {
  enabled = {
    tiles = false,
    icons = false,
  },
}
```

**Icons only, no tile overlays:**
```lua
weatherSystem = {
  enabled = {
    tiles = false,
    icons = true,
  },
}
```

**Tiles only, no icons:**
```lua
weatherSystem = {
  enabled = {
    tiles = true,
    icons = false,
  },
}
```

**Disable specific weather types:**
```lua
weatherSystem = {
  enabled = {
    tiles = true,
    icons = true,
  },
  weathers = {
    CLEAR = { enabled = true, tile = "CLEAR", icon = "CLEAR_LOGO", label = "Clear" },
    RAIN = { enabled = false }, -- Rain won't show any overlay
    SNOW = { enabled = true, tile = "SNOW", icon = "SNOW_LOGO", label = "Snow" },
  }
}
```

---

# Overlay Conflict Groups

Prevents multiple overlays from occupying the same map space at the same time.

```lua
OverlayConflictGroups = {
  { "interstates", "interstates2", "interstates_medieval", "interstates_nostalgic", "interstates_underwater" },
  { "rural", "rural2", "rural_medieval", "rural_nostalgic", "rural_underwater" },
  { "urban", "urban2", "urban_medieval", "urban_nostalgic", "urban_underwater" },
  { "p4d_dark", "p4d_light", "pocrp_dark", "pocrp_light" },
}
```

## How It Works

- Each array is a **conflict group**
- When one overlay in a group is enabled, all others in that group are automatically disabled
- This prevents visual overlap (e.g., you can't have both Standard and Medieval interstate signs active)

## Why This Exists

Some overlays cover the same map tiles but with different styles:
- **Route signs** - Same highways, different themes (Standard, San Andreas, Medieval, Nostalgic, Underwater)
- **Postal codes** - Same locations, different backgrounds (dark vs light, 4-digit vs OCRP)

Without conflict groups, enabling multiple overlays would stack them on top of each other, making the map unreadable.

## Default Conflict Groups

**Highway Signs:**
```lua
{ "interstates", "interstates2", "interstates_medieval", "interstates_nostalgic", "interstates_underwater" }
```
Only one interstate style can be active at a time.

**Rural Route Signs:**
```lua
{ "rural", "rural2", "rural_medieval", "rural_nostalgic", "rural_underwater" }
```
Only one rural route style can be active at a time.

**Urban Route Signs:**
```lua
{ "urban", "urban2", "urban_medieval", "urban_nostalgic", "urban_underwater" }
```
Only one urban route style can be active at a time.

**Postal Codes:**
```lua
{ "p4d_dark", "p4d_light", "pocrp_dark", "pocrp_light" }
```
Only one postal overlay can be active (across all types and styles).

## Adding Custom Conflict Groups

If you add custom overlays that occupy the same map space, add them to a conflict group:

```lua
OverlayConflictGroups = {
  -- ... existing groups
  { "my_custom_overlay1", "my_custom_overlay2", "my_custom_overlay3" },
}
```

**Rules:**
- Each group is a Lua array (table) of overlay keys
- Overlay keys must match entries in the `overlays` table
- Groups work across different categories
- No need to list every pair — just group all conflicting overlays together

# Categories & Overlays System

The minimap uses a **category-based overlay system**. Categories organize overlays into logical groups in the tablet UI, and overlays are the actual map tiles that get rendered.

## How It Works

- **Categories** = Sections in the tablet UI (e.g., "Department Zones", "Postal Codes", "Map Themes")
- **Overlays** = Individual map tiles inside those sections (e.g., "LSPD", "Dark Postals", "Blue Ocean Theme")
- Each overlay belongs to one category via the `categorie` field
- Categories can have subcategories (nested tabs in the UI)

## Category Configuration

Each category supports these properties:

```lua
category_name = {
  enabled = true,              -- false = hide entire category from UI
  label = "Display Name",      -- What shows in the tablet
  description = "Details",     -- Subtitle/description text
  icon = "fa-solid fa-icon",   -- FontAwesome icon
  allowMultiple = false,       -- true = players can enable multiple overlays in this category
  
  -- Optional properties:
  subCategorie = true,         -- Renders as a sub-tab inside parentCategory
  parentCategory = 'parent',   -- Which category to nest inside
  requiresMap = 'cayo_perico', -- Category hidden when this customMaps entry is disabled
  conflictsWithMaps = { "cayo_perico" }, -- Disable when these custom maps are active
  
  permissions = {              -- Restrict to specific jobs (bypassed in standalone mode)
    enabled = true,
    allowedJobs = { 'police', 'sheriff' }
  }
}
```

### enabled
- `true` = Category appears in the tablet
- `false` = Category completely hidden (all overlays inside it are disabled)

### allowMultiple
- `true` = Players can enable multiple overlays in this category at once
- `false` = Only one overlay can be active at a time (radio button behavior)

### Job Permissions

Restrict a category to specific jobs (ESX, QBCore, QBox):

```lua
permissions = {
  enabled = true,
  allowedJobs = { 'police', 'sheriff', 'trooper' }
}
```

- **Standalone mode**: Permissions are bypassed (everyone has access)
- **Framework mode**: Only players with those jobs see the category

### Subcategories

Nest categories inside other categories for organization:

```lua
postal_4d = {
  enabled = true,
  label = "4-Digit",
  subCategorie = true,
  parentCategory = 'postal_codes', -- Renders inside postal_codes tab
}
```

## Overlay Configuration

Each overlay supports these properties:

```lua
overlay_name = {
  categorie = 'category_name', -- Which category this overlay belongs to (required)
  label = "Display Name",      -- What shows in the tablet
  description = "Details",     -- Subtitle/description text
  enabled = true,              -- false = overlay won't load or appear
  forced = false,              -- true = always active on connect, can't be toggled off
  
  -- Optional properties:
  linkedOverlay = "other_overlay", -- Auto-enable/disable another overlay with this one
  icon = "nui://path/icon.png",    -- Custom icon (used for department zones)
  shortLabel = "ABBR",             -- Short abbreviation (used for department zones)
}
```

### enabled
- `true` = Overlay is available (players can toggle it)
- `false` = Overlay completely disabled (won't load or appear for anyone)

### forced
- `true` = Overlay is always active when player joins, cannot be toggled off
- `false` = Overlay is optional (player controls)

### linkedOverlay

Automatically sync two overlays together:

```lua
black_hole = {
  categorie = 'map_themes',
  linkedOverlay = "black_hole_cayo", -- When main theme enables, Cayo theme also enables
}
```

- When `black_hole` is enabled, `black_hole_cayo` also enables
- When `black_hole` is disabled, `black_hole_cayo` also disables
- Useful for matching themes across base map and custom maps

---

## Available Categories

### Department Zones
```lua
departments = {
  enabled = true,
  label = "Department Zones",
  allowMultiple = true,
  permissions = {
    enabled = true,
    allowedJobs = { 'police', 'sheriff', 'trooper' }
  }
}
```
Law enforcement territory overlays (LSPD, LSSD, BSCO, etc.). Restricted to police jobs by default.

### Zone Names
```lua
zone_names = {
  enabled = true,
  label = "Zone Names",
  allowMultiple = false,
}
```
Location name overlays (Vinewood, Del Perro, Sandy Shores, etc.). Different themed styles available.

### Street Names
```lua
street_names = {
  enabled = true,
  label = "Street Names",
  allowMultiple = false,
}
```
Street name text overlay.

### Postal Codes (Parent Category)
```lua
postal_codes = {
  enabled = true,
  label = "Postal Codes",
  allowMultiple = false,
}
```
Parent category for postal code subcategories.

**Subcategories:**
- **postal_4d** - 4-digit postal codes (dark/light variants)
- **postal_ocrp** - OCRP postal codes (dark/light variants)

### Numbered Highways (Parent Category)
```lua
routes = {
  enabled = true,
  label = "Numbered Highways",
  allowMultiple = true,
}
```
Parent category for route sign subcategories (interstates, rural, urban).

**Subcategories:**
- **standard_routes** - Classic US-style route signs
- **san_andreas_routes** - San Andreas themed route signs
- **medieval_routes** - Medieval themed route signs
- **nostalgic_routes** - Retro game themed route signs
- **underwater_routes** - Underwater themed route signs

### POI Icons
```lua
poi_icons = {
  enabled = true,
  label = "POI Icons",
  allowMultiple = false,
}
```
Point-of-interest icon themes (Medieval, Nostalgic, Underwater).

### Map Themes
```lua
map_themes = {
  enabled = true,
  label = "Map Themes",
  allowMultiple = false,
}
```
Base-map color themes (Black Hole, Blue Ocean, Sakura, etc.).

### Cayo Perico Themes (Subcategory)
```lua
cayo_themes = {
  enabled = true,
  requiresMap = 'cayo_perico',
  subCategorie = true,
  parentCategory = 'map_themes',
  conflictsWithMaps = { "cayo_perico" },
}
```
Cayo Perico color theme extensions. Hidden when `customMaps.cayo_perico.enabled = false`.

---

## Available Overlays

### Zone Names Overlays
- **names** - Standard zone names
- **wanted_names** - Wanted/red theme styling
- **cyber_red_names** - Cyber red theme styling
- **crime_scene_names** - Crime scene theme styling
- **epicnews** - EpicNews styled theme
- **pure_blue** - Pure blue styled theme

### Street Names Overlay
- **street_names_overlay** - Standard street names

### Postal Code Overlays

**4-Digit:**
- **p4d_dark** - Dark (black) background
- **p4d_light** - Light (white) background

**OCRP:**
- **pocrp_dark** - Dark (black) background
- **pocrp_light** - Light (white) background

### Route Sign Overlays

Each route category has three overlays: **Interstates**, **Rural Routes**, **Urban Routes**

**Standard Routes:**
- **interstates** - US-style interstate highway signs
- **rural** - US-style rural route signs
- **urban** - US-style urban state route signs

**San Andreas Routes:**
- **interstates2**, **rural2**, **urban2**

**Medieval Routes:**
- **interstates_medieval**, **rural_medieval**, **urban_medieval**

**Nostalgic Routes:**
- **interstates_nostalgic**, **rural_nostalgic**, **urban_nostalgic**

**Underwater Routes:**
- **interstates_underwater**, **rural_underwater**, **urban_underwater**

### Map Theme Overlays
- **black_hole** - Deep dark void map theme
- **blue_ocean** - Cool ocean-blue map theme
- **dusty_brown** - Warm dusty desert theme
- **fresh_blood** - Deep crimson map theme
- **mandarin** - Warm amber/orange map theme
- **pink_petal** - Soft pink blossom map theme
- **purple_heart** - Deep violet map theme
- **sakura** - Soft cherry blossom theme
- **sour_lime** - Bright fresh lime map theme

**Cayo Perico Extensions** (one for each main theme):
- **black_hole_cayo**, **blue_ocean_cayo**, **dusty_brown_cayo**, etc.

### POI Icon Overlays
- **poi_medival** - Medieval themed icons
- **poi_nostalgic** - Retro game themed icons
- **poi_underwater** - Underwater themed icons

### Department Zone Overlays
- **bsco** - Blaine County Sheriff
- **dppd** - Del Perro Police Department
- **lspd** - Los Santos Police Department
- **lssd** - Los Santos Sheriff Department
- **mcso** - Majestic County Sheriff Office
- **nose** - National Office of Security Enforcement
- **rhpd** - Rockford Hills Police Department
- **saspa** - San Andreas State Prison Authority
- **usaf** - United States Air Force Security Forces

---

## Examples

**Disable an entire category:**
```lua
categories = {
  poi_icons = {
    enabled = false, -- POI icons won't appear in the tablet
  }
}
```

**Disable a specific overlay:**
```lua
overlays = {
  wanted_names = {
    enabled = false, -- Wanted zone names won't load
  }
}
```

**Force an overlay to always be active:**
```lua
overlays = {
  names = {
    forced = true, -- Standard zone names always active, can't be toggled off
  }
}
```

**Remove job restrictions from department zones:**
```lua
categories = {
  departments = {
    permissions = {
      enabled = false, -- Everyone can access department zones
    }
  }
}
```

**Add a new job to department zone permissions:**
```lua
categories = {
  departments = {
    permissions = {
      enabled = true,
      allowedJobs = { 'police', 'sheriff', 'trooper', 'ems', 'fire' }
    }
  }
}
```
