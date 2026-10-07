---
description: >-
  Postal textures made to support all Frostbyte Minimaps, but they can also be
  used for any other minimap you are using. With this, you can choose between
  the 3 most-used postal types across FiveM: OCRP
cover: ../.gitbook/assets/postal textures thumbanel free.jpg
coverY: -4.357437759639595
---

# fst-minimap-postals

{% hint style="warning" %}
Please Read :warning:\
Everything included in this project is free to use, as long as you respect the credits and the licenses set by the original creators.\
Please do not resell, redistribute, or claim these textures as your own.\
Don't be a jerk and sell this stupid shit. It's free for everyone to use just respect the original creators and their licenses.
{% endhint %}

### Preview (on sherry map design)

{% tabs %}
{% tab title="ocrp postals" %}
<div align="left"><figure><img src="../.gitbook/assets/ocrp preview_02.png" alt="" width="188"><figcaption></figcaption></figure></div>


{% endtab %}

{% tab title="default postals" %}
<div align="left"><figure><img src="../.gitbook/assets/4digits preview_02 (1).png" alt="" width="188"><figcaption></figcaption></figure></div>


{% endtab %}

{% tab title="Oulsen postals" %}
<div align="left"><figure><img src="../.gitbook/assets/oulsen preview_02.png" alt="" width="188"><figcaption></figcaption></figure></div>


{% endtab %}
{% endtabs %}

### How to use&#x20;

{% hint style="info" %}
There are many ways to use these textures.
{% endhint %}

{% tabs %}
{% tab title="First Option" %}
Drag and drop the resource into your server files. Once that's done, the textures will be loaded into your server. Then, use [Extra Map Tiles](https://forum.cfx.re/t/release-extra-map-tiles-v2-add-extra-textured-tiles-on-the-pause-menu-map-and-minimap-new-and-revamped-version/5344181?page=4) to load the textures by following their documentation.

{% code expandable="true" %}
```lua
    -- oulsen_postales
    ['5'] = { txd = "ls_minimap_oulsen_0_0", txn = "0_0", x_offset = 0, y_offset = 0, x_scale = 1.0, y_scale = 1.0, rotation = 0.0, alpha = 100, centered = false, visible = false },
    ['6'] = { txd = "ls_minimap_oulsen_0_1", txn = "0_1", x_offset = 1, y_offset = 0, x_scale = 1.0, y_scale = 1.0, rotation = 0.0, alpha = 100, centered = false, visible = false },
    ['7'] = { txd = "ls_minimap_oulsen_1_0", txn = "1_0", x_offset = 0, y_offset = 1, x_scale = 1.0, y_scale = 1.0, rotation = 0.0, alpha = 100, centered = false, visible = false },
    ['8'] = { txd = "ls_minimap_oulsen_1_1", txn = "1_1", x_offset = 1, y_offset = 1, x_scale = 1.0, y_scale = 1.0, rotation = 0.0, alpha = 100, centered = false, visible = false },
    ['9'] = { txd = "ls_minimap_oulsen_2_0", txn = "2_0", x_offset = 0, y_offset = 2, x_scale = 1.0, y_scale = 1.0, rotation = 0.0, alpha = 100, centered = false, visible = false },
    ['10'] = { txd = "ls_minimap_oulsen_2_1", txn = "2_1", x_offset = 1, y_offset = 2, x_scale = 1.0, y_scale = 1.0, rotation = 0.0, alpha = 100, centered = false, visible = false },
  
    -- postales_4
    ['11'] = { txd = "ls_minimap_4deg_0_0", txn = "0_0", x_offset = 0, y_offset = 0, x_scale = 1.0, y_scale = 1.0, rotation = 0.0, alpha = 100, centered = false, visible = true },
    ['12'] = { txd = "ls_minimap_4deg_0_1", txn = "0_1", x_offset = 1, y_offset = 0, x_scale = 1.0, y_scale = 1.0, rotation = 0.0, alpha = 100, centered = false, visible = true },
    ['13'] = { txd = "ls_minimap_4deg_1_0", txn = "1_0", x_offset = 0, y_offset = 1, x_scale = 1.0, y_scale = 1.0, rotation = 0.0, alpha = 100, centered = false, visible = true },
    ['14'] = { txd = "ls_minimap_4deg_1_1", txn = "1_1", x_offset = 1, y_offset = 1, x_scale = 1.0, y_scale = 1.0, rotation = 0.0, alpha = 100, centered = false, visible = true },
    ['15'] = { txd = "ls_minimap_4deg_2_0", txn = "2_0", x_offset = 0, y_offset = 2, x_scale = 1.0, y_scale = 1.0, rotation = 0.0, alpha = 100, centered = false, visible = true },
    ['16'] = { txd = "ls_minimap_4deg_2_1", txn = "2_1", x_offset = 1, y_offset = 2, x_scale = 1.0, y_scale = 1.0, rotation = 0.0, alpha = 100, centered = false, visible = true },

    -- ocrp_postales
    ['17'] = { txd = "ls_minimap_ocrp_0_0", txn = "0_0", x_offset = 0, y_offset = 0, x_scale = 1.0, y_scale = 1.0, rotation = 0.0, alpha = 100, centered = false, visible = false },
    ['18'] = { txd = "ls_minimap_ocrp_0_1", txn = "0_1", x_offset = 1, y_offset = 0, x_scale = 1.0, y_scale = 1.0, rotation = 0.0, alpha = 100, centered = false, visible = false },
    ['19'] = { txd = "ls_minimap_ocrp_1_0", txn = "1_0", x_offset = 0, y_offset = 1, x_scale = 1.0, y_scale = 1.0, rotation = 0.0, alpha = 100, centered = false, visible = false },
    ['20'] = { txd = "ls_minimap_ocrp_1_1", txn = "1_1", x_offset = 1, y_offset = 1, x_scale = 1.0, y_scale = 1.0, rotation = 0.0, alpha = 100, centered = false, visible = false },
    ['21'] = { txd = "ls_minimap_ocrp_2_0", txn = "2_0", x_offset = 0, y_offset = 2, x_scale = 1.0, y_scale = 1.0, rotation = 0.0, alpha = 100, centered = false, visible = false },
    ['22'] = { txd = "ls_minimap_ocrp_2_1", txn = "2_1", x_offset = 1, y_offset = 2, x_scale = 1.0, y_scale = 1.0, rotation = 0.0, alpha = 100, centered = false, visible = false },
```
{% endcode %}


{% endtab %}

{% tab title="Second Option" %}
Export the tiles and import them into Photoshop. You can then use them directly when creating or editing your minimap.

This option is useful if you want to manually integrate the postal textures into your own minimap design.
{% endtab %}
{% endtabs %}
