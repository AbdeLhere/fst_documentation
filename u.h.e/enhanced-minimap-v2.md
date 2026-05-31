# Admin Permissions System

## How It Works

The admin permissions system controls who can make server-wide changes to the minimap. When enabled, only authorized admins can modify overlays, HUD colors, and display settings for all players. Regular players see their tablet in read-only mode.

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

### Force Flags
When you set a force flag to `true`, that feature becomes locked for regular players:
- **forceOverlays** - Controls all map overlays (postal codes, routes, department zones, map themes)
- **forceVisuals** - Controls HUD colors (minimap border, waypoint color, pause menu background)
- **forceDisplaySettings** - Controls weather and day/night display options

If all three are `false`, no Admin Mode button appears in the tablet (nothing is being managed server-wide).

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
