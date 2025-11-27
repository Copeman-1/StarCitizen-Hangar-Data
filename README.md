# StarCitizen-Hangar-Data

Central data repository for [Star Citizen Hangar Manager](https://github.com/Copeman-1/StarCitizen-Hangar-Viewer) extension.

This repo hosts ship databases, loaner matrices, and ship images that are fetched by the extension at runtime, allowing updates without requiring users to reinstall the extension.

## 📁 Structure

```
StarCitizen-Hangar-Data/
├── ships/
│   ├── database.json       # Complete ship catalog (190+ ships)
│   └── images/             # Ship background images
│       ├── aegis-avenger-titan.jpg
│       └── ...
├── loaners/
│   └── matrix.json         # Loaner ship mappings (70+ ships)
├── version.json            # Version tracking for cache busting
└── README.md
```

## 📊 Data Files

### ships/database.json
Complete catalog of Star Citizen ships and vehicles with:
- Ship name and manufacturer
- Price (USD)
- Type (Ship or Ground Vehicle)
- Status (Flight Ready or In Concept)

**Format:**
```json
{
  "version": "2.0.2",
  "lastUpdated": "2025-11-27",
  "ships": [
    {
      "name": "Aegis Avenger Titan",
      "manufacturer": "Aegis",
      "price": 50,
      "type": "Ship",
      "status": "Flight Ready"
    }
  ]
}
```

### loaners/matrix.json
Loaner ship mappings based on [RSI's official loaner matrix](https://support.robertsspaceindustries.com/hc/en-us/articles/360003093114-Loaner-Ship-Matrix).

**Format:**
```json
{
  "version": "2.0.2",
  "lastUpdated": "2025-11-27",
  "matrix": {
    "Ironclad": ["Caterpillar"],
    "Polaris": ["F7C-M Super Hornet"]
  }
}
```

### version.json
Version tracking for client-side caching.

## 🖼️ Ship Images

### Adding Images

1. Create a pull request with your ship images
2. Name files: `manufacturer-ship-name.jpg` or `.png`
   - Lowercase
   - Replace spaces with dashes
   - Remove special characters
3. Place in `ships/images/` folder

**Examples:**
- "Aegis Avenger Titan" → `aegis-avenger-titan.jpg`
- "RSI Aurora MR" → `rsi-aurora-mr.png`
- "Anvil C8X Pisces Expedition" → `anvil-c8x-pisces-expedition.jpg`

### Image Guidelines
- **Resolution**: Minimum 800x450 (16:9 aspect ratio recommended)
- **Format**: JPG or PNG
- **Size**: Under 500KB per image (optimize for web)
- **Content**: Official ship artwork or high-quality screenshots

## 🔄 Updating Data

### Ship Database
To add or update ships:
1. Edit `ships/database.json`
2. Update `version` field
3. Update `lastUpdated` field
4. Increment ship `count` in `version.json`

### Loaner Matrix
To update loaners:
1. Edit `loaners/matrix.json`
2. Follow format: `"Original Ship": ["Loaner Ship 1", "Loaner Ship 2"]`
3. Update `version` and `lastUpdated`
4. Update loaner `count` in `version.json`

### Version Bumping
Always update `version.json` when making changes:
```json
{
  "dataVersion": "2.0.3",
  "lastUpdated": "2025-11-28T00:00:00Z"
}
```

## 🤝 Contributing

Contributions are welcome! Please:
1. Fork the repo
2. Create a feature branch
3. Make your changes
4. Submit a pull request

### What to Contribute
- ✅ New ship images
- ✅ Ship database updates (new ships, price changes)
- ✅ Loaner matrix updates (when RSI updates)
- ✅ Image quality improvements

## 📜 License

This repository contains data and images related to Star Citizen®.

Star Citizen® and Roberts Space Industries® are registered trademarks of Cloud Imperium Rights LLC and Cloud Imperium Rights Ltd.

Images are property of Cloud Imperium Games and are used for reference purposes only.

## 🔗 Links

- **Extension Repo**: [StarCitizen-Hangar-Viewer](https://github.com/Copeman-1/StarCitizen-Hangar-Viewer)
- **RSI Loaner Matrix**: [Official Source](https://support.robertsspaceindustries.com/hc/en-us/articles/360003093114-Loaner-Ship-Matrix)
- **Star Citizen**: [robertsspaceindustries.com](https://robertsspaceindustries.com)

## 📝 Notes

- Data is fetched from GitHub's CDN (raw.githubusercontent.com)
- Extension caches data locally to minimize API calls
- Version checking ensures users get latest data
- No authentication required for public access
