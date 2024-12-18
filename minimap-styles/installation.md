
#### Step 1: Remove Old Minimap Script

* Start by removing any old minimap script from your resources folder.

#### Step 2: Cleanup

* Open **Visual Studio Code**.
* Press `CTRL + K + O` to open a folder.
* Select your server folder and press `Open`.
* Press `CTRL + SHIFT + F` to search for the following lines:
  * `SetMapZoomDataLevel`
  * `SetRadarZoom`
  * `SetRadarAsInteriorThisFrame` " remove this one only if you have specific problems with the map "
* Remove these lines if found, **but do not remove them from the new script!**

#### Step 3: Ensuring the New Script

* Drag and drop the new resource into your resources folder.
* Open your `server.cfg` file and add the following line after your framework, replacing `"script-name"` with your actual script name (e.g., `abl-minimap-X8-OP`):

```lua
ensure "script-name"
```

* Restart your server.

#### Step 4: Configuration

* You can adjust the background opacity in `Config.Options.opacity` (Max: 200, Min: 0).
* Pause Menu colors can be edited in `Config.Options.RedGreenBlueAlpha`. You can use the [RGBA Color Picker](https://rgbacolorpicker.com/) to choose your preferred colors.
* **Note:** If you change colors, please avoid modifying `["ALPHA"] = 0.8`.
* To customize titles, refer to `Config.Options.Header`.
