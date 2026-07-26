# Admin System

```mermaid

graph TD

A[InGamePermissionsSystem] --> B{Choose a mode}

B --> C[Mode 1<br/>Everyone controls their own minimap]
B --> D[Mode 2<br/>Admins control the minimap]
B --> E[Mode 3<br/>Locked for everyone<br/>Config only]

C --> C1["enabled = false"]
C --> C2["forceOverlays = false"]
C --> C3["forceVisuals = false"]
C --> C4["forceDisplaySettings = false"]

D --> D1["enabled = true"]
D --> D2["forceOverlays = true"]
D --> D3["forceVisuals = true"]
D --> D4["forceDisplaySettings = true"]
D --> D5["Only admins can change settings"]

E --> E1["enabled = false"]
E --> E2["forceOverlays = true"]
E --> E3["forceVisuals = true"]
E --> E4["forceDisplaySettings = true"]
E --> E5["Players cannot change anything"]
E --> E6["Configure default values in config.lua"]

D5 --> F[Configure Admin Permissions]
F --> F1[ACE Permissions]
F --> F2[Framework Groups]
F --> F3[Specific Identifiers]

E6 --> G[Set default overlay states]
G --> G1["Example: wanted_names forced = true"]
G --> G2["Repeat for every overlay you want enabled or disabled"]

```

{% tabs %}
{% tab title="Mode 1" %}
```lua
  InGamePermissionsSystem = {
    enabled = false,
    forceOverlays = false,
    forceVisuals = false,
    forceDisplaySettings = false,
    ace = { 'group.admin', 'fst_minimap.admin' },
    identifiers = { 'discord:907923629226983425', 'license:f21b66842de05a850df9224665256b1293ddfdc0' },
    framework = { esx = { 'superadmin', 'admin' }, qbcore = { 'god', 'admin' }, qbox = { 'god', 'admin' } },
  },
```
{% endtab %}

{% tab title="Mode 2" %}
```lua
  InGamePermissionsSystem = {
    enabled = true,
    forceOverlays = true,
    forceVisuals = true,
    forceDisplaySettings = false,
    ace = { 'group.admin', 'fst_minimap.admin' },
    identifiers = { 'discord:907923629226983425', 'license:f21b66842de05a850df9224665256b1293ddfdc0' },
    framework = { esx = { 'superadmin', 'admin' }, qbcore = { 'god', 'admin' }, qbox = { 'god', 'admin' } },
  },
```
{% endtab %}

{% tab title="Mode 3" %}
```lua
  InGamePermissionsSystem = {
    enabled = false,
    forceOverlays = true,
    forceVisuals = true,
    forceDisplaySettings = true,
    ace = { 'group.admin', 'fst_minimap.admin' },
    identifiers = { 'discord:907923629226983425', 'license:f21b66842de05a850df9224665256b1293ddfdc0' },
    framework = { esx = { 'superadmin', 'admin' }, qbcore = { 'god', 'admin' }, qbox = { 'god', 'admin' } },
  },
```
{% endtab %}
{% endtabs %}
