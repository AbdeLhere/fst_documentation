---
cover: ../../.gitbook/assets/enhanced v2 miinilao thumb (1).jpg
coverY: -550.8341708542714
coverHeight: 263
layout:
  width: default
  cover:
    visible: true
    size: full
    mask: none
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
    visible: false
  tags:
    visible: true
  actions:
    visible: true
  anchors:
    visible: true
---

# FST Enhanced Minimap V2

{% embed url="https://youtu.be/TbQgkFTVGUk" %}

{% hint style="warning" %}
**Please read carefully to understand the difference between the Basic and Ultimate versions of FST Enhanced Minimap V2.**\
\
The **Basic version** includes the built-in system and standard overlays.\
The **Ultimate version** includes everything in the Basic version, plus all paid listed here: [**FrostByte Minimaps**](../fst-minimaps.md)
{% endhint %}

{% stepper %}
{% step %}
### **Required step before starting.**

* Remove any old minimap scripts from your server resources.
* Download and ensure **`ox_lib`** starts before this script in your `server.cfg`.
* Drag and drop the script into your `resources` folder. **Do not rename the folder.**
{% endstep %}

{% step %}
### Optional minimap assets

{% hint style="danger" %}
If you want to use the built-in themes, you need an empty Los Santos minimap. [fst\_empty\_los\_santos\_minimap](https://github.com/AbdeLhere/fst_empty_los_santos_minimap) installed
{% endhint %}

* If you already have a minimap design and only want to use overlays, zones, icons, or other features, **delete** [fst\_empty\_los\_santos\_minimap](https://github.com/AbdeLhere/fst_empty_los_santos_minimap).
* Install [fst\_atlas\_minimaps\_assets](https://github.com/AbdeLhere/fst_atlas_minimaps_assets) if you want to use the default Atlas or Satellite minimap overlays.
* If you have the bundle or want to use external [FrostByte minimaps](../fst-minimaps.md), install their required assets. Example: `fst_colored_minimaps_assets`
{% endstep %}

{% step %}
### install postals and street names

* First, install the required dependencies:\
  [fst\_minimap\_postals\_assets](https://github.com/AbdeLhere/fst_minimap_postals_assets) for postals.\
  [fst\_minimap\_streetnames\_assets](https://github.com/AbdeLhere/fst_minimap_streetnames_assets) for street names.
*   Then enable them in `config.lua`:<br>

    <pre class="language-lua" data-title="config.lua" data-expandable="true"><code class="lang-lua">local frostbyteMaps = {
      western = false,                      -- true if fst_western_minimap_assets is installed
      oldpaper = false,                     -- true if fst_oldpaper_minimap_assets is installed
      burnout = false,                      -- true if fst_burnout_minimap_assets is installed
      colored_minimaps = false,             -- true if fst_colored_minimaps_assets is installed
      vintage_minimaps = false,             -- true if fst_vintage_minimaps_assets is installed
      minimap_postals = false,              -- true if fst_minimap_postals_assets is installed
      minimap_streetnames = false,          -- true if fst_minimap_streetnames_assets is installed

      atlas_and_satellite_minimaps = false, -- true if fst_atlas_minimaps_assets is installed
    }
    </code></pre>
{% endstep %}

{% step %}
### **Configure Core Settings**

* Review admin permissions in the config if you want to restrict map configuration access to admins only.

{% content-ref url="admin-system.md" %}
[admin-system.md](admin-system.md)
{% endcontent-ref %}

*   Some categories have a `requiresMap` field.<br>

    <pre class="language-lua" data-title="config.lua" data-overflow="wrap"><code class="lang-lua">cayo_themes = { enabled = true, requiresMap = 'cayo_perico', label = "Cayo Perico", description = "Cayo Perico colour theme extensions matching the base map themes", icon = "fas fa-umbrella-beach", allowMultiple = false, conflictsWithMaps = { "cayo_perico" }, },
    </code></pre>

    \
    This means the category only loads if the required map is enabled. For example, `cayo_themes` requires the `cayo_perico` map.

    To use it, enable Cayo Perico under the `customMaps` section if your server uses Cayo Perico.
{% endstep %}

{% step %}
### Troubleshooting&#x20;

*   **Minimap is pulsing or flashing?**

    Try these settings:<br>

    <pre class="language-lua" data-title="config.lua"><code class="lang-lua">  enable_map_zoom_levels = false,
      removeBlur = false, -- Remove the blur/vignette effect on the minimap edges
      radarZoom = { enabled = false, level = 1300 },
    </code></pre>
*   **Some overlays are not drawing or weird textures appear?**

    The script is probably trying to load a texture that you don't have installed.\
    Set:

    ```lua
    debug = true,
    ```

    This will help you track the exact issue.
*   **Having texture loss, missing roads, or parts of the map disappearing in-game?**\
    Read this:\
    \
    One of the first things to try is **reducing the amount of map textures you are using**.

    <mark style="color:$success;">The reason our minimap assets are separated into different resources is so you only install the assets you actually need.</mark> <mark style="color:$warning;">Using too many large textures at the same time can cause streaming issues.</mark>

    Make sure you **do not see errors like these in your server console**:

    ```
    Warning: Asset .../minimap.ytd uses 64.0 MiB of physical memory.
    Oversized assets can and WILL lead to streaming issues.
    ```

    You may also see warnings for assets using <mark style="color:$warning;">**32.0 MiB of physical memory**</mark>, or similar.

    For example, the **Satellite minimap is an 8K map**, which is very large for FiveM. If you are experiencing texture loss or missing roads, **do not use the 8K Satellite map** on your server.

    Increasing the texture budget in your FiveM settings does **not** guarantee that the problem is fixed for all players.

    The minimap textures are located in the `stream` folder, so using fewer and smaller textures can greatly reduce streaming problems.

    This is also why FrostByte minimap assets are separated into different resources: **only install and use the assets you actually need.**

    If you need more help understanding texture streaming or these warnings, open a ticket in our Discord and we can help you further.
{% endstep %}
{% endstepper %}
