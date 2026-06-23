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





READY TO RUN SCRIPT WITH CHANGING URL ONLY TO UPDATE

#!/bin/bash

# Claude DMG direct GitHub release link
URL="https://github.com/mahdijbara/mac-updates/releases/download/v1.14271.0/Claude.dmg"

TMP_FILE="/tmp/Claude.dmg"
MOUNT_POINT="/Volumes/Claude"

echo "Starting Claude installation..."

# Download DMG
echo "Downloading..."
curl -L "$URL" -o "$TMP_FILE"

if [ ! -f "$TMP_FILE" ]; then
  echo "Download failed"
  exit 1
fi

# Mount DMG
echo "Mounting DMG..."
hdiutil attach "$TMP_FILE" -nobrowse -quiet

# Wait a moment for mount
sleep 5

# Find app inside DMG and copy to Applications
echo "Installing application..."
cp -R "$MOUNT_POINT"/*.app /Applications/

# Unmount DMG
echo "Cleaning up..."
hdiutil detach "$MOUNT_POINT" -quiet

# Remove temp file
rm -f "$TMP_FILE"

echo "Claude installation complete"
exit 0
