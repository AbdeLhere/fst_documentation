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
