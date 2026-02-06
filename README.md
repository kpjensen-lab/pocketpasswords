# 🔐 PocketVault

Local password manager with versioning and backup capabilities.

## Quick Start

### iPhone Installation

1. Upload `password-manager.html`, `manifest.json`, and `sw.js` to a GitHub repository
2. Enable GitHub Pages (Settings → Pages → Deploy from main branch)
3. On iPhone Safari, visit: `https://yourusername.github.io/repo-name/password-manager.html`
4. Tap Share → Add to Home Screen
5. Done! Works 100% offline after installation

### Desktop Testing

Open `password-manager.html` in any modern browser.

## Features

- **Offline-first**: All data stored locally in IndexedDB
- **Version management**: Import backups as separate versions, merge selectively
- **Tag organization**: Organize accounts with multiple tags
- **Export/Import**: JSON backups with conflict resolution
- **No cloud sync**: Data never leaves your device

## File Structure

- `password-manager.html` - Main application
- `manifest.json` - PWA manifest
- `sw.js` - Service worker for offline support

## Security Note

All password data is stored locally on your device. GitHub only hosts the app code - no passwords are ever transmitted.

## Export Format

Exports are JSON files named: `pvault-YYYY-MM-DD-HHMMSS.json`

## Updates

To update the app:
1. Upload new files to GitHub
2. Clear Safari cache on iPhone (Settings → Safari → Clear History and Website Data)
3. Reopen the app

---

**PocketVault** - Local Account Management
