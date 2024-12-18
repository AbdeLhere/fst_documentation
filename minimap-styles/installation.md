---
icon: hashtag
cover: ../.gitbook/assets/0A8704FA-8499-4DE1-9192-14D4A6E56769.jpg
coverY: 0
layout:
  cover:
    visible: true
    size: full
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
---

# Installation

## <mark style="color:yellow;">**Step 1: Remove Old Minimap Script**</mark>

* Remove any old minimap script from your resources.

## <mark style="color:yellow;">**Step 2: Cleanup**</mark>&#x20;

* Open **Visual Studio Code**.
* Press `CTRL + K + O` to open a folder.
* Select your server folder and press `Open`.
* Press `CTRL + SHIFT + F` to search for the following lines:
  * `SetMapZoomDataLevel`
  * `SetRadarZoom`
  * `SetRadarAsInteriorThisFrame` " remove this one only if you have specific problems with the map "

{% hint style="warning" %}
Remove these lines if found, **but do not remove them from the new script!**
{% endhint %}

## <mark style="color:yellow;">**Step 3: Ensuring the New Script**</mark>

* Drag and drop the new resource into your resources folder.
* Open your `server.cfg` file and add the following line after your framework, replacing `"script-name"` with your actual script name (e.g., `abl-minimap-X8-OP`):

<pre class="language-systemd"><code class="lang-systemd"><strong>ensure ox_lib ## my lib
</strong><strong>ensure qb-core ## my framework
</strong>
<strong>ensure "script-name"
</strong></code></pre>

* Restart your server.

## <mark style="color:yellow;">**Step 4: Configuration**</mark>

* You can adjust the background opacity in `Config.Options.opacity` (Max: 200, Min: 0).
* Pause Menu colors can be edited in `Config.Options.RedGreenBlueAlpha`. You can use the [RGBA Color Picker](https://rgbacolorpicker.com/) to choose your preferred colors.
* **Note:** If you change colors, please avoid modifying `["ALPHA"] = 0.8`.
* To customize titles, refer to `Config.Options.Header`.
