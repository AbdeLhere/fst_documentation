---
icon: square-info
layout:
  width: default
  title:
    visible: false
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
---

# Admin System

The script includes an advanced in-game permission system with **three different modes**, allowing you to decide how much control players have over their minimap.

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
{% tab title="Mode" icon="1" %}
{% hint style="info" %}
Everyone controls thier own minimap
{% endhint %}

```lua
  InGamePermissionsSystem = {
    enabled = false,
    forceOverlays = false,
    forceVisuals = false,
    forceDisplaySettings = false,
    ace = { 'group.admin', 'fst_minimap.admin' },
    identifiers = { 'discord:907923629226983425', 'license:xxxx' },
    framework = { esx = { 'superadmin', 'admin' }, qbcore = { 'god', 'admin' }, qbox = { 'god', 'admin' } },
  },
```
{% endtab %}

{% tab title="Mode" icon="2" %}
{% hint style="info" %}
Amins control the minimap including (Overlays, Visuals and Display Settings)
{% endhint %}

```lua
  InGamePermissionsSystem = {
    enabled = true,
    forceOverlays = true,
    forceVisuals = true,
    forceDisplaySettings = true,
    ace = { 'group.admin', 'fst_minimap.admin' },
    identifiers = { 'discord:907923629226983425', 'license:xxxx' },
    framework = { esx = { 'superadmin', 'admin' }, qbcore = { 'god', 'admin' }, qbox = { 'god', 'admin' } },
  },
```
{% endtab %}

{% tab title="Mode" icon="3" %}
{% hint style="info" %}
Locked for everyone, Config only
{% endhint %}

```lua
  InGamePermissionsSystem = {
    enabled = false,
    forceOverlays = true,
    forceVisuals = true,
    forceDisplaySettings = true,
    ace = { 'group.admin', 'fst_minimap.admin' },
    identifiers = { 'discord:907923629226983425', 'license:xxxx' },
    framework = { esx = { 'superadmin', 'admin' }, qbcore = { 'god', 'admin' }, qbox = { 'god', 'admin' } },
  },
```
{% endtab %}
{% endtabs %}

{% hint style="info" %}
### Admin Permissions

You can define who has access to the admin controls using **ACE permissions**, **specific player identifiers**, or your framework's admin groups.<br>

```lua
ace = {
    'group.admin',
    'fst_minimap.admin'
},

identifiers = {
    'discord:xxxx',
    'license:xxxx'
},

framework = {
    esx = { 'superadmin', 'admin' },
    qbcore = { 'god', 'admin' },
    qbox = { 'god', 'admin' }
},
```
{% endhint %}



