# Smart Home Configuration

Professional smart home setup using [Home Assistant](https://www.home-assistant.io/) and [Kincony](https://www.kincony.com/) (ESPHome), featuring organized automations, analytics sensors, and production-ready deployment.

## 📊 Project Statistics

**Home Assistant:**
- 🤖 **12 automations** organized in 5 categories
- 🎨 **6 scenes** for presence and day/night modes
- 📊 **4 analytics sensors** for home insights
- 📝 **2 scripts** for reusable automation logic
- 🔧 **2 helpers** in version-controlled YAML

**Code Quality:**
- ✨ All automations and scenes documented with descriptions
- 📋 Organized with 80-char section headers
- 🔄 Uses entity IDs (no fragile device IDs)

## 🏠 Features

### Automation Categories

**Scene Management** (4 automations)
- Automatic home/away mode switching based on presence
- Separate scenes for main home and Kvetoslavov

**Vacuum Cleaning** (3 automations)
- Auto-start Xiaomi vacuum when leaving home
- Auto-dock when someone arrives
- Bathroom cleaning after litter robot cycle

**Pet Care** (2 automations)
- Automated bathroom cleaning coordination
- Waste drawer level notifications

**Day/Night Management** (2 automations)
- Automatic curtain control at sunrise/sunset
- Scene switching for different times of day

**Location-based Notifications** (1 automation)
- Shopping list reminders when entering stores

### Analytics Sensors

- 📍 **Home occupancy percentage** - Daily occupancy tracking
- 🤖 **Vacuum runtime** - Monitor cleaning efficiency
- 🐱 **Litter robot cycles** - Pet care automation frequency
- 🏡 **Kvetoslavov occupancy** - Secondary location tracking



## 📁 Directory Structure

```
smart-home-config/
├── homeassistant/           # Home Assistant configuration
│   ├── configuration/       # HA configuration files
│   │   ├── configuration.yaml   # Main config with includes
│   │   ├── automations.yaml     # 12 organized automations
│   │   ├── scenes.yaml          # 6 presence & time-based scenes
│   │   ├── scripts.yaml         # Reusable automation scripts
│   │   ├── sensors.yaml         # Analytics & history stats
│   │   ├── helpers.yaml         # Input helpers (YAML)
│   │   ├── custom_components/   # Custom integrations
│   │   ├── themes/              # UI themes (Mushroom, iOS)
│   │   └── docs/                # Documentation
│   └── README.md            # Detailed HA documentation
│
├── kincony/                 # Kincony KC868 (ESPHome) config
│   ├── configuration/       # ESPHome YAML configuration
│   │   └── home.yaml        # Main ESPHome config
│   ├── docs/                # Hardware documentation
│   └── README.md            # Kincony setup guide
│
└── AGENTS.md                # Development guidelines

```

## 🚀 Quick Start

### Home Assistant

**See [homeassistant/configuration/README.md](homeassistant/configuration/README.md)** for detailed setup and configuration information.

### Kincony (ESPHome)

Compile and upload:
```bash
cd kincony
esphome run configuration/home.yaml
```

**See [kincony/README.md](kincony/README.md)** for ESPHome installation and usage.

## 🔧 Technology Stack

- **Home Assistant** - Smart home automation platform
- **ESPHome** - ESP32/ESP8266 firmware for IoT devices
- **Kincony KC868** - Industrial automation hardware
- **Custom Components:**
  - Dahua cameras
  - Dreame/Xiaomi vacuum
  - Google Home integration
  - Tapo smart devices
  - SmartThinQ (LG appliances)

## 📱 Integrated Devices

- Xiaomi Robot Vacuum X20
- Litter Robot 4
- Dahua NVR & cameras
- Tapo cameras (Hall, Bedroom, Kitchen, Living room)
- Smart curtains
- Various sensors and switches via Kincony

## 📖 Documentation

- [Home Assistant Configuration](homeassistant/configuration/README.md) - Detailed HA setup
- [Kincony Setup](kincony/README.md) - ESPHome configuration
- [SSH Access](homeassistant/docs/ssh.md) - Remote access documentation
- [Development Guidelines](AGENTS.md) - Code style and standards

## 🤝 Contributing

Contributions are welcome! Please:
1. Fork the repository
2. Create a feature branch
3. Follow the code style in [AGENTS.md](AGENTS.md)
4. Submit a pull request

## 📄 License

This project is licensed under the MIT License. See the LICENSE file for details.

---

**Note:** Sensitive information (API keys, passwords) is stored in `secrets.yaml` files which are excluded from the repository.
