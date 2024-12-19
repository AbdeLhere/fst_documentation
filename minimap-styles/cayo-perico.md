---
icon: map
cover: ../.gitbook/assets/0A8704FA-8499-4DE1-9192-14D4A6E56769.jpg
coverY: 0
layout:
  cover:
    visible: true
    size: full
  title:
    visible: true
  description:
    visible: false
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: true
---

# Cayo Perico

{% hint style="warning" %}
**To enable Cayo Perico Minimap set `enable_cayo_minimap = true`.**
{% endhint %}

## <mark style="color:green;">Installation</mark>

1. Choose your style:&#x20;
   * <mark style="color:yellow;">**Example**</mark> : I have **abl-minimap-part1-OP**. So to install the **grey Cayo Perico minimap with green zone names**, follow these steps
2. Download your style:
   * Download the **Cayo-Maps** `Folder` from <mark style="color:yellow;">**GitHub**</mark>.
3. Drag and drop your style:
   * Move the file `Cayo-Maps/Grey with text/grey-green/int3232302352.gfx` to the folder `abl-minimap-part1-OP/stream/gfx`.
4. Finish
   * Restart the script (it’s recommended to restart the server) to complete the setup.

## <mark style="color:green;">Configuration</mark>

{% hint style="info" %}
`enable_cayo_minimap`  will just enable the cayo minimap not the map IPL\
\
<mark style="color:yellow;">**Example :**</mark>

***

\
![](<../.gitbook/assets/image (2) (1).png>)\


***
{% endhint %}

{% hint style="success" %}
If you dont have the Cayo Perico IPL you can download it from [<mark style="color:yellow;">**HERE**</mark>](https://forum.cfx.re/t/the-cayo-perico-island-available-for-fivem/1897446)
{% endhint %}

{% hint style="warning" %}
After installing [<mark style="color:yellow;">ipls\_resource</mark>](https://forum.cfx.re/t/the-cayo-perico-island-available-for-fivem/1897446) set `using_ipl_loader = true`
{% endhint %}

***

```lua
  cayoPerico = {
        enable_cayo_minimap = true, -- Set to true if you want enable cayo minimap
        using_ipl_loader = false, -- If you are using an IPL RESOURCE set this true (example: https://forum.cfx.re/t/the-cayo-perico-island-available-for-fivem/1897446?page=38)
    },
```

***
