---
description: What is CFX Auth?
layout:
  width: default
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
  metadata:
    visible: true
---

# CFX Escrow System

### What is CFX Auth?

CFX Auth, also called the FiveM escrow system, is used to protect premium resources. It encrypts important files so only the person who purchased the script can use it. This keeps FrostByte Studios scripts (for example, `fst-enhanced-minimap`) secure and prevents unauthorized editing or sharing.

***

### Common Issues and Fixes

#### Failed to Verify Protected Resource

**Error:**

```
Failed to verify protected resource (fst-enhanced-minimap)
```

**Cause:** Some encrypted files were corrupted or skipped during upload.\
**Fix:**

* Re-upload all files, including the `.fxap` files.
* Use **WinSCP** for file transfers, as FileZilla can sometimes skip encrypted files.

***

#### Missing Required Entitlement

**Error:**

```
You lack the required entitlement to use fst-enhanced-minimap
```

**Cause:** The server license key is not linked to the account that purchased the script.\
**Fix:**

* Check your license key in [Keymaster](https://keymaster.fivem.net/).
* Make sure the key is from the same account that purchased the script.
* Restart the server after updating the license key.

***

#### Syntax Errors

**Error:**

```
Syntax error </1>
```

**Cause:** Running an outdated FiveM artifact, or editing encrypted files.\
**Fix:**

* Update your server to artifact version **4960 or newer**.
* Do not edit encrypted `.fxap` files. Use the provided configuration files instead.
* Restart the server after making changes.

***

### Recommendations

* Keep your server updated with the latest artifacts.
* Use reliable tools like WinSCP for uploading files.
* Only edit configuration files, not encrypted code.
* Restart your server after installing or updating any script.
