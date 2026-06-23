# mac-updates
📦 mac-updates

Central repository for hosting macOS application installers (.dmg / .pkg) used for automated deployment and updates via MDM tools such as NinjaOne.

🎯 Purpose

This repository is used to:

Host macOS application installers that exceed MDM upload limits (e.g. 200MB+)
Provide stable HTTPS download links for automation scripts
Support silent or manual installation workflows
Enable version-controlled software distribution for macOS devices
⚙️ Why this exists

Some MDM solutions (such as NinjaOne) have limitations including:

File upload size restrictions (e.g. 200MB limit)
Lack of direct vendor download URLs for certain applications
No reliable built-in software repository for large macOS apps

This repository solves that by acting as a lightweight software distribution source of truth.
