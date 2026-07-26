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

# Adjusting Overlay Priority

{% hint style="success" %}
Technically, this is **not a bug**. It depends on your personal preference and how you want your overlays to be layered.
{% endhint %}

{% hint style="info" %}
For example, you may want your **route/highway signs** to appear **below** the **zone names**, giving the zone names higher priority and making them easier to read.
{% endhint %}

### To change the overlay order:

{% stepper %}
{% step %}
### `Open config.lua.`
{% endstep %}

{% step %}
### `Locate the category_order = {} table.`
{% endstep %}

{% step %}
### Rearrange the categories to change their loading order.
{% endstep %}

{% step %}
### Tutorial

In this example, we want the `zone_names` category to render **on top of** `underwater_routes`.&#x20;

{% hint style="info" %}
Since categories are rendered from **top to bottom**, the category placed **lower** in the `category_order` table is drawn **last** and therefore appears **above** the others.
{% endhint %}

To achieve this, simply move `zone_names` **below** `underwater_routes` in the `category_order` table, as shown in the image below.

<div align="right" data-with-frame="true"><figure><img src="../../../.gitbook/assets/before after (1).png" alt=""><figcaption></figcaption></figure></div>
{% endstep %}

{% step %}
{% code title="config.lua" %}
```lua
  category_order = {
    "map_themes",         -- player base-map colour themes
    "cayo_themes",        -- Cayo Perico sub-tab (rendered inside map_themes section)
    "custom_maps",        -- terrain addons (very bottom)
    "day_night_themes",   -- day/night base map themes (just above terrain)
    "departments",        -- zone fills
    "extras",             -- street names, map keys, and special overlays
    "standard_routes",    -- route signs: Standard US style
    "san_andreas_routes", -- route signs: San Andreas style
    "medieval_routes",    -- route signs: Medieval style
    "nostalgic_routes",   -- route signs: Nostalgic retro style
    "underwater_routes",  -- route signs: Underwater style
    "postal_codes",       -- postal numbers (parent)
    "postal_4d",          -- 4-digit postal subcategory
    "postal_ocrp",        -- OCRP postal subcategory
    "poi_icons",          -- POI icon themes
    "western_extras",     -- western-specific extras subcategory
    "oldpaper_extras",    -- old paper-specific extras subcategory
    "day_night",          -- day/night icon (sun / moon)
    "weather_icons",      -- weather logo icon (very top)
    "weather_tiles",      -- full-map weather overlays — clouds/rain/snow
  },
```
{% endcode %}
{% endstep %}

{% step %}
### Results

<figure><img src="../../../.gitbook/assets/Nouveau projet.png" alt=""><figcaption></figcaption></figure>
{% endstep %}
{% endstepper %}
