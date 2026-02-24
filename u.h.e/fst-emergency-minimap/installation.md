---
cover: ../../.gitbook/assets/thumbnail (2) (1).png
coverY: 0
---

# Installation

## Emergency Minimap Setup Guide

### 1. Remove Old Minimap

Before installing the new Emergency Minimap, remove any old minimap scripts from your server resources.

#### Cleanup (Optional but Recommended)

1. Open **Visual Studio Code**.
2. Press **CTRL + K + O** and select your server folder.
3. Press **CTRL + SHIFT + F** to search for the following lines in your code:
   * `SetMapZoomDataLevel`
   * `SetRadarZoom`
4. Remove these lines if they exist. **Do not remove them from the new minimap script.**

***

### 2. Install the New Minimap

1. Drag and drop the new resource into your **resources folder**.
2. Open your `server.cfg` file and add the following lines **after your framework** (replace with your actual script name):

```
ensure ox_lib       -- your library
ensure qb-core      -- your framework
ensure "abl-emap-t1"  -- your minimap script
```

3. Restart your server.

***

### 3. Styles

If you want to use different map styles (like Cayo Bridge or Roxwood County), follow the instructions below.

***

### 4. Changing the Default Map

The default map is `abl-emap-t1`. You can switch to a different map by replacing the contents of the `abl-emergencymap/stream/ytd` folder with files from a new map.

#### Example: Switching to Los Santos + Cayo Perico (Without Zone Names)

1. **Locate the default map:**
   * Go to `abl-emergencymap/stream/ytd` in your current installation.
2. **Select the new map files:**
   * Navigate to `abl-emergencymap/INSTALLATION/Other Styles/abl-emap-t2/ytd`.
3. **Replace the files:**
   * Copy all files from the new folder into `abl-emap-t1/stream/ytd` and **replace existing files** when prompted.

***

### 5. Map Variants

| Script         | Description                                                                           |
| -------------- | ------------------------------------------------------------------------------------- |
| `abl-emap-t1`  | Los Santos + Cayo Perico (+ Zone Names)                                               |
| `abl-emap-t2`  | Los Santos + Cayo Perico (Without Zone Names)                                         |
| `abl-emap-t3`  | Los Santos + Cayo Perico + Roxwood County V1 (+ Zone Names)                           |
| `abl-emap-t4`  | Los Santos + Cayo Perico + Roxwood County V1 + Cayo Bridge V2 (+ Zone Names)          |
| `abl-emap-t5`  | Los Santos + Cayo Perico + Roxwood County V1 + Cayo Bridge V1 (+ Zone Names)          |
| `abl-emap-t6`  | Los Santos + Cayo Perico + Cayo Bridge V1 (+ Zone Names)                              |
| `abl-emap-t7`  | Los Santos + Cayo Perico + Cayo Bridge V2 (+ Zone Names)                              |
| `abl-emap-t8`  | Los Santos + Cayo Perico + Roxwood County Last Update (+ Zone Names)                  |
| `abl-emap-t9`  | Los Santos + Cayo Perico + Roxwood County Last Update + Cayo Bridge V2 (+ Zone Names) |
| `abl-emap-t10` | Los Santos + Cayo Perico + Roxwood County Last Update + Cayo Bridge V1 (+ Zone Names) |
