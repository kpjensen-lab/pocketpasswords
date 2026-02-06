# 🔐 KeyVault Password Manager

A secure, offline-first Progressive Web App (PWA) for managing passwords with versioning and backup capabilities.

## Features

✅ **Offline-First**: Works completely offline using IndexedDB
✅ **Version Management**: Import backups as separate versions and merge selectively
✅ **Tag-Based Organization**: Organize accounts with multiple tags
✅ **Active/Inactive States**: Mark accounts as active or inactive
✅ **Custom Fields**: Add unlimited custom fields to any account
✅ **App Deep Links**: Quick access to apps via deep linking
✅ **Export/Import**: JSON backup and restore functionality
✅ **Responsive Design**: Works beautifully on iPhone and desktop
✅ **Secure**: Data stays on your device, no cloud sync

## Installation

### On iPhone (Safari)

1. Open `password-manager.html` in Safari
2. Tap the Share button (square with arrow)
3. Scroll down and tap "Add to Home Screen"
4. Name it "KeyVault" and tap "Add"
5. The app will now appear on your home screen

### On Desktop

1. Open `password-manager.html` in Chrome/Edge
2. Click the install icon in the address bar (or ⋮ menu → "Install KeyVault")
3. Confirm installation
4. Access from your applications menu or desktop

### On Android

1. Open `password-manager.html` in Chrome
2. Tap the menu (⋮)
3. Tap "Add to Home screen"
4. Confirm

## Usage Guide

### Data Structure

The app uses a simple key-value structure:
- **Version**: Primary (active) or v1, v2, etc. (imported backups)
- **Account Title**: Unique identifier for each account
- **Attributes**: username, email, password, url, app, active_flag, tags, custom fields
- **Values**: The actual data

### Standard Fields

Every account has these default fields:
- **Account Title** (required, unique)
- **Username** (required)
- **Email** (optional)
- **Password** (required, hidden by default)
- **URL** (optional)
- **App Link** (optional, with common app presets)
- **Active Flag** (required, defaults to true)

### Workflow

1. **Version Selection**
   - Start by selecting a version (Primary or imported backup)
   - Upload backups to create new versions (v1, v2, etc.)

2. **Tag Navigation**
   - View all accounts or filter by tags
   - Tag buttons show account count in brackets
   - Sorted by count (ALL is always first)

3. **Account Management**
   - Active accounts appear first (alphabetically)
   - Inactive accounts appear below (alphabetically, greyed out)
   - Click any account to view details

4. **Account Details**
   - View all fields with copy buttons
   - Toggle password visibility
   - Open apps via deep links
   - Manage tags
   - Add custom fields
   - Edit or delete account

### Version Management & Merging

**Primary Version**: Your active working database

**Uploaded Versions**: Backups that can be reviewed and selectively merged

**Push to Primary**:
- Push individual accounts or all accounts
- Choose conflict resolution:
  - **Keep Versioned Values**: Overwrites Primary with backup data
  - **Keep Primary Values**: Keeps current Primary data
- Non-conflicting values from both versions are merged

**Example Merge Scenario**:
```
Primary:
- Facebook / URL / facebook.com
- Facebook / Username / george

Backup v1:
- Facebook / Username / phil
- Facebook / Password / secret123

Merge with "Keep Versioned Values":
Result:
- Facebook / URL / facebook.com (kept from Primary)
- Facebook / Username / phil (overwrote Primary)
- Facebook / Password / secret123 (added from backup)
```

### App Deep Links

Common apps are pre-configured:
- Instagram, Facebook, Twitter/X, LinkedIn
- TikTok, Snapchat, YouTube
- Gmail, WhatsApp, Telegram
- Spotify, Netflix, Amazon
- Reddit, Pinterest

You can also add custom deep links for any app.

### Export/Import

**Export**: Only exports the Primary version as JSON

**Import**: Creates a new version (v1, v2, etc.) with timestamp

This allows you to:
- Keep multiple backup versions
- Review backups before merging
- Selectively merge specific accounts
- Safely test changes

## Data Format

Export format (JSON):
```json
{
  "version": "Primary",
  "timestamp": 1234567890,
  "records": [
    {
      "accountTitle": "Facebook",
      "attribute": "username",
      "value": "john_doe"
    },
    {
      "accountTitle": "Facebook",
      "attribute": "password",
      "value": "secret123"
    }
  ]
}
```

## Security Notes

⚠️ **Important Security Information**:

1. **Local Storage Only**: All data is stored in your browser's IndexedDB
2. **No Cloud Sync**: Data never leaves your device
3. **Device Security**: Relies on your device's lock screen/password
4. **Export Security**: Exported JSON files are unencrypted - store them securely
5. **Browser Data**: Clearing browser data will delete all passwords
6. **Backup Regularly**: Export your Primary version regularly

## Technical Details

- **Storage**: IndexedDB
- **Framework**: Vanilla JavaScript
- **Styling**: Custom CSS with gradient mesh design
- **Fonts**: Google Fonts (Outfit, JetBrains Mono)
- **Offline**: Service Worker caching
- **Compatibility**: Modern browsers (Chrome, Safari, Firefox, Edge)

## File Structure

```
password-manager.html  - Main application
manifest.json          - PWA manifest
sw.js                  - Service worker
README.md             - This file
```

## Tips

💡 Use tags to organize accounts by category (Social Media, Banking, Work, etc.)

💡 Mark old accounts as "Inactive" instead of deleting them

💡 Export Primary version before making major changes

💡 Test merges with a backup version before applying to Primary

💡 Use descriptive custom field names for easy identification

💡 Copy-paste functionality works on all fields for easy access

## Browser Compatibility

- ✅ Chrome/Edge 80+
- ✅ Safari 13.1+
- ✅ Firefox 78+
- ✅ iOS Safari 13.4+
- ✅ Chrome Android 80+

## Troubleshooting

**App won't install on iPhone**:
- Make sure you're using Safari (not Chrome)
- iOS 13.4+ is required

**Data disappeared**:
- Check if browser data was cleared
- Restore from your last export

**Import not working**:
- Ensure JSON file is valid
- Check file has correct format (see Data Format above)

**App link doesn't work**:
- Some apps may not support deep linking
- Try the URL field instead

## Privacy

This app:
- ❌ Does NOT send data to any server
- ❌ Does NOT track your usage
- ❌ Does NOT require an internet connection
- ✅ Stores everything locally on your device
- ✅ Works completely offline
- ✅ Gives you full control of your data

---

**Created with Claude** | Secure Password Management | Offline-First PWA
