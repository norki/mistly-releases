# Mistly - Guild Wars 2 Companion

A powerful desktop application for Guild Wars 2 that provides inventory management, bank organization, and Trading Post integration through the official API.

![Mistly Desktop App](https://img.shields.io/badge/Platform-Windows%20%7C%20Mac%20%7C%20Linux-blue)
![Auto Update](https://img.shields.io/badge/Auto%20Update-Enabled-green)
![License](https://img.shields.io/badge/License-MIT-yellow)

## 🎮 Features

### 🎒 Inventory Manager
- View all items across character inventories
- Real-time Trading Post prices
- Color-coded rarity display
- Calculate total inventory value
- Export to CSV/JSON
- Sort by value to find most valuable items

### 🏦 Bank & Storage Manager
- View account bank contents
- Browse material storage by category
- Combined storage view (bank + materials)
- Search across all storage locations
- Track item locations easily
- Export storage data

### 📈 Smart Inventory Analysis
- **Intelligent Recommendations**: Get personalized advice on whether to salvage, sell, or keep each item
- **Economic Optimization**: Maximize profits with data-driven decisions based on current Trading Post prices
- **Salvage Kit Selection**: Automatically recommends the most cost-effective salvage kit for each item
- **Batch Processing**: Analyze single characters or your entire account at once
- **Material Value Tracking**: See the true value of salvaging vs selling
- **Export Action Lists**: Save recommendations for easy in-game processing

### 🔍 Smart Search (Coming Soon)
- Search for items across all characters and storage
- Find items by name or description
- Instant location tracking

### 📊 Additional Features
- **Modern Desktop Interface**: Native desktop app with dark theme
- **Auto-Updates**: Stay up to date automatically
- **Caching System**: Reduces API calls and improves performance
- **Rate Limiting**: Respects GW2 API limits automatically
- **Progress Indicators**: Shows progress for long operations
- **Export Options**: CSV and JSON export for all data

## 🚀 Download & Installation

### Download the Desktop App

Download the latest version for your platform from the [Releases](https://github.com/norki/mistly-releases/releases) page:

- **Windows**: Download the `.exe` installer
- **macOS**: Download the `.dmg` file
- **Linux**: Download the `.AppImage` file

**Note**: The app includes auto-update functionality that will notify you when new versions are available.

### Requirements

- GW2 API key with permissions: `account`, `characters`, `inventories`, `wallet`, `unlocks`
- Get your API key from: https://account.arena.net/applications

### Installation Steps

1. Download the appropriate installer for your operating system
2. Run the installer:
   - **Windows**: Double-click the `.exe` file
   - **macOS**: Double-click the `.dmg` and drag to Applications
   - **Linux**: Make the `.AppImage` executable and run it
3. Launch Mistly
4. On first launch, you'll see a welcome screen:
   - Enter your GW2 API key in the setup modal
   - Click the link to get an API key if you don't have one
   - The app validates your key before saving
5. Start managing your GW2 inventory!

## 🛠️ Configuration

### API Key Setup

When you first launch Mistly, a setup modal will appear:
- Enter your GW2 API key in the text field
- Click "Save API Key" to validate and save it
- If the key is invalid, you'll see an error message
- You can change your API key later in Settings

Your API key is stored locally in your user data directory and is never transmitted anywhere except to the official GW2 API.

### Environment Variables

The app stores configuration in:
- **Windows**: `%APPDATA%\Mistly`
- **macOS**: `~/Library/Application Support/Mistly`
- **Linux**: `~/.config/Mistly`

The app stores your configuration in a `config.json` file containing:
- Your GW2 API key (encrypted)
- Future settings will be added here

Note: The environment variables shown below are for development use only:
```env
GW2_SHOW_PROGRESS=true        # Show progress indicators
GW2_USE_COLORS=true          # Enable colored output (terminal mode)
GW2_EXPORT_FORMAT=csv        # Default export format (csv/json)
```

### Cache Management

The app uses intelligent caching following GW2 API best practices:
- Static data (items, skins): 24-hour cache
- Semi-dynamic data (characters, bank): 1-hour cache
- Dynamic data (prices): 5-minute cache

Clear cache through Settings in the app.

## 📁 Project Structure

```
mistly/
├── electron/           # Electron desktop app
│   ├── src/           # Main and renderer processes
│   ├── assets/        # App icons and resources
│   └── index.html     # Main app window
├── core/              # Core Python functionality
│   ├── gw2_api.py    # GW2 API client
│   ├── cache.py      # Caching system
│   ├── config.py     # Configuration management
│   └── utils.py      # Utility functions
├── tools/            # Feature modules
│   ├── inventory.py  # Inventory manager
│   ├── bank.py       # Bank manager
│   └── ...          # Other tools
├── api_server.py     # Flask API server
├── package.json      # Node.js configuration
└── requirements.txt  # Python dependencies
```

## 🔧 Architecture

Mistly uses a hybrid architecture:
- **Frontend**: Electron (Chromium + Node.js) for the desktop UI
- **Backend**: Python Flask API server for GW2 API integration
- **Communication**: REST API over localhost
- **Security**: API keys stored locally, never transmitted

## 🐛 Troubleshooting

### App Won't Start / Shows "Error" Status
- Check if port 5000 is available (the internal API server uses this port)
- Ensure your antivirus isn't blocking the app
- Try running as administrator (Windows)
- If you see "Backend Error" or the app is stuck loading:
  - The Python backend may have failed to start
  - Check Windows Defender or antivirus logs
  - Try reinstalling the latest version

### Invalid API Key
- Ensure your API key has the required permissions: `account`, `characters`, `inventories`, `wallet`, `unlocks`
- The API may occasionally return "Invalid key" errors - the app will retry automatically
- You can update your API key in the Settings menu

### Auto-Update Issues
- Check your internet connection
- Ensure the app has write permissions to its installation directory
- Manually download the latest version if needed
- Updates are checked on app startup

### Recent Updates (v1.0.15)
- **New**: API key setup modal on first launch
- **New**: Persistent API key storage between sessions
- **Fixed**: Windows startup issues with embedded Python
- **Fixed**: Backend connection problems
- **Improved**: Better error messages and user guidance

### Minimum Version Requirement
Please ensure you're running at least v1.0.15 for the best experience. Earlier versions had various startup issues that have been resolved.

## 🤝 Contributing

Contributions are welcome! Please:
1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

Please follow the existing code style and include appropriate error handling. See [CLAUDE.md](CLAUDE.md) for detailed development guidelines.

## 📝 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🙏 Acknowledgments

- Guild Wars 2 and ArenaNet for the amazing API
- The GW2 community for inspiration and feedback
- All contributors who help make Mistly better

## 📞 Support

- **Issues**: [GitHub Issues](https://github.com/norki/mistly/issues)
- **Discussions**: [GitHub Discussions](https://github.com/norki/mistly-releases/discussions)

---

Made with ❤️ for the Guild Wars 2 community