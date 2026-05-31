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

### Force Flags
When you set a force flag to `true`:
1. That feature becomes **locked for regular players** (read-only)
2. Authorized admins get an **"Admin Mode" button** in their tablet
3. Admins use the Admin Mode menu to control that feature **server-wide** (changes apply to everyone)

- **forceOverlays** - Controls all map overlays (postal codes, routes, department zones, map themes)
- **forceVisuals** - Controls HUD colors (minimap border, waypoint color, pause menu background)
- **forceDisplaySettings** - Controls weather and day/night display options

**Important:** If all three force flags are `false`, no Admin Mode button will appear (nothing is being managed server-wide).

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
