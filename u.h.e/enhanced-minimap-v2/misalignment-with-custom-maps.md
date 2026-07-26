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

# Misalignment with Custom Maps

{% hint style="info" %}
If you have Roxwood or any other custom map enabled, along with weather cards or other overlays, some overlays may cover parts of the map. If this happens, you can manually adjust the position of every overlay in `client/cl_overlays.lua` by editing their coordinates. This allows you to avoid conflicts and properly align all map elements.
{% endhint %}

{% stepper %}
{% step %}
#### Problem:&#x20;

<figure><img src="../../../.gitbook/assets/logo on roxwood.jpg" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
#### Solution

{% hint style="info" %}
Navigate to `client/cl_overlays.lua` and search for `Overlays.CLEAR_LOGO`. Then replace all of the following:
{% endhint %}

{% code title="cl_overlays.lua" expandable="true" %}
```lua
Overlays.CLEAR_LOGO             = { { posX = -0.9999, posY = 0.4998, scaleX = 0.8, scaleY = 0.8, centered = false, txd = "minimap_clear_logo_0_0", txn = "0_0", alpha = 200 } }
Overlays.EXTRASUNNY_LOGO        = { { posX = -0.9999, posY = 0.4998, scaleX = 0.8, scaleY = 0.8, centered = false, txd = "minimap_extrasunny_logo_0_0", txn = "0_0", alpha = 200 } }
Overlays.RAIN_LOGO              = { { posX = -0.9999, posY = 0.4998, scaleX = 0.8, scaleY = 0.8, centered = false, txd = "minimap_rain_logo_0_0", txn = "0_0", alpha = 200 } }
Overlays.THUNDER_LOGO           = { { posX = -0.9999, posY = 0.4998, scaleX = 0.8, scaleY = 0.8, centered = false, txd = "minimap_thunder_logo_0_0", txn = "0_0", alpha = 200 } }
Overlays.CLOUDS_LOGO            = { { posX = -0.9999, posY = 0.4998, scaleX = 0.8, scaleY = 0.8, centered = false, txd = "minimap_clouds_logo_0_0", txn = "0_0", alpha = 200 } }
Overlays.OVERCAST_LOGO          = { { posX = -0.9999, posY = 0.4998, scaleX = 0.8, scaleY = 0.8, centered = false, txd = "minimap_overcast_logo_0_0", txn = "0_0", alpha = 200 } }
Overlays.FOGGY_LOGO             = { { posX = -0.9999, posY = 0.4998, scaleX = 0.8, scaleY = 0.8, centered = false, txd = "minimap_foggy_logo_0_0", txn = "0_0", alpha = 200 } }
Overlays.SNOW_LOGO              = { { posX = -0.9999, posY = 0.4998, scaleX = 0.8, scaleY = 0.8, centered = false, txd = "minimap_snow_logo_0_0", txn = "0_0", alpha = 200 } }
Overlays.XMAS_LOGO              = { { posX = -0.9999, posY = 0.4998, scaleX = 0.8, scaleY = 0.8, centered = false, txd = "minimap_xmas_logo_0_0", txn = "0_0", alpha = 200 } }
Overlays.SNOWLIGHT_LOGO         = { { posX = -0.9999, posY = 0.4998, scaleX = 0.8, scaleY = 0.8, centered = false, txd = "minimap_snowlight_logo_0_0", txn = "0_0", alpha = 200 } }
Overlays.BLIZZARD_LOGO          = { { posX = -0.9999, posY = 0.4998, scaleX = 0.8, scaleY = 0.8, centered = false, txd = "minimap_blizzard_logo_0_0", txn = "0_0", alpha = 200 } }
Overlays.CLEARING_LOGO          = { { posX = -0.9999, posY = 0.4998, scaleX = 0.8, scaleY = 0.8, centered = false, txd = "minimap_clearing_logo_0_0", txn = "0_0", alpha = 200 } }
Overlays.NEUTRAL_LOGO           = { { posX = -0.9999, posY = 0.4998, scaleX = 0.8, scaleY = 0.8, centered = false, txd = "minimap_neutral_logo_0_0", txn = "0_0", alpha = 200 } }
Overlays.SMOG_LOGO              = { { posX = -0.9999, posY = 0.4998, scaleX = 0.8, scaleY = 0.8, centered = false, txd = "minimap_smog_logo_0_0", txn = "0_0", alpha = 200 } }
Overlays.HALLOWEEN_LOGO         = { { posX = -0.9999, posY = 0.4998, scaleX = 0.8, scaleY = 0.8, centered = false, txd = "minimap_halloween_logo_0_0", txn = "0_0", alpha = 200 } }
Overlays.HALLOWEEN_RAIN_LOGO    = { { posX = -0.9999, posY = 0.4998, scaleX = 0.8, scaleY = 0.8, centered = false, txd = "minimap_halloween_rain_logo_0_0", txn = "0_0", alpha = 200 } }
Overlays.HALLOWEEN_SNOW_LOGO    = { { posX = -0.9999, posY = 0.4998, scaleX = 0.8, scaleY = 0.8, centered = false, txd = "minimap_halloween_snow_logo_0_0", txn = "0_0", alpha = 200 } }
```
{% endcode %}
{% endstep %}

{% step %}
### Results

<figure><img src="../../../.gitbook/assets/common problems sover docs (1).jpg" alt=""><figcaption></figcaption></figure>
{% endstep %}
{% endstepper %}
