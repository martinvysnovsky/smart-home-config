# Home Assistant Configuration

## Table of Contents

- [Directory Structure](#directory-structure)
- [Installation](#installation)
- [Usage](#usage)
- [Automation Examples](#automation-examples)
- [Customization](#customization)
- [Contributing](#contributing)
- [License](#license)

## Directory Structure

```
configuration/
  ├─ configuration.yaml    # Main HA configuration with includes
  ├─ secrets.yaml          # Sensitive data (not in repo)
  ├─ helpers.yaml          # Input boolean/number/text helpers
  ├─ automations.yaml      # 12 automations in 5 categories
  ├─ scripts.yaml          # 2 scripts (vacuum, camera control)
  ├─ scenes.yaml           # 6 scenes (home/away, day/night)
  ├─ sensors.yaml          # History stats sensors
  ├─ custom_components/    # Custom integrations
  │   ├─ dahua/
  │   ├─ dreame_vacuum/
  │   ├─ google_home/
  │   ├─ smartthinq_sensors/
  │   └─ tapo_control/
  ├─ themes/               # UI themes
  │   ├─ mushroom/
  │   └─ ios-themes/
  └─ www/                  # Static web files
docs/
  └─ ssh.md                # SSH access documentation
compose.yaml               # Docker Compose configuration
```

### Configuration Files

- **`configuration.yaml`**: Main configuration file that includes all other YAML files
- **`helpers.yaml`**: Input helpers (booleans, numbers, text) defined in YAML for version control
- **`automations.yaml`**: 12 automations organized into 5 sections:
  - Scene Management (4 automations)
  - Vacuum Cleaning (3 automations)
  - Pet Care (2 automations)
  - Day/Night Management (2 automations)
  - Location-based Notifications (1 automation)
- **`scripts.yaml`**: Reusable scripts for vacuum control and camera motion detection
- **`scenes.yaml`**: 6 scenes for different home states and times of day
- **`sensors.yaml`**: Template and history statistics sensors
- **`secrets.yaml`**: Sensitive data like API keys (excluded from repository)

## Installation

1. **Clone the repository**:

```bash
git clone https://github.com/martinvysnovsky/smart-home-config.git
cd smart-home-config/homeassistant
```

2. **Copy the configuration files** to your Home Assistant configuration directory, typically located at `/config`:

```bash
cp -r configuration/* /config
```

Alternatively you can create symlinks to the configuration files. This way your configuration will always be up-to-date.

```bash
cd /homeassistant
ln -s smart-home-config/homeassistant/configuration/configuration.yaml configuration.yaml
```

NOTE: you need to clone the repository inside `/homeassistant` folder.

3. **Install custom components** (if any) by copying them to the appropriate directory within your Home Assistant setup.

4. **Restart Home Assistant** to apply the new configurations:

```bash
docker restart homeassistant  # If using Docker
```

### Running locally with Docker Compose

```bash
docker compose up -d
```

The Docker Compose configuration includes:
- **Healthcheck**: Monitors Home Assistant availability every 30s
- **Resource limits**: 2GB memory, 2 CPU cores
- **Log rotation**: Max 10MB per file, 3 files retained
- **Watchtower support**: Automated container updates

## Usage

- Edit `configuration.yaml` to configure integrations and services
- Update `automations.yaml` to add or modify automation rules
- Modify `helpers.yaml` for input booleans, numbers, and text helpers
- Create new scenes in `scenes.yaml` for different home states
- Customize the frontend using files in the `themes/` and `www/` directories

## Automation Examples

This repository includes 12 automations organized into 5 categories:

### Scene Management - Presence-based automation

Automatically switches between home and away modes based on zone presence:

```yaml
- alias: Enable Away scene when everybody leave home
  description: Activates away scene (privacy off, motion detection on) when everyone leaves
  triggers:
  - trigger: state
    entity_id: zone.home
    to: '0'
  actions:
  - action: scene.turn_on
    target:
      entity_id: scene.away
```

### Vacuum Cleaning - Automated scheduling

Starts Xiaomi vacuum when everyone leaves during daytime hours:

```yaml
- alias: Start Xiaomi when leaving home
  description: Starts Xiaomi vacuum in sweeping mode (08:00-22:00)
  triggers:
  - entity_id:
    - person.martin_vysnovsky
    - person.lidia_silanteva
    zone: zone.home
    event: leave
  conditions:
  - condition: time
    after: 08:00:00
    before: '22:00:00'
  actions:
  - action: vacuum.start
    target:
      entity_id: vacuum.xiaomi_robot_vacuum_x20
```

### Day/Night Management - Sunrise and sunset automation

Automatically opens/closes curtains based on sun position:

```yaml
- alias: Activate day mode
  description: Opens living room curtains at sunrise
  triggers:
  - trigger: sun
    event: sunrise
  actions:
  - action: scene.turn_on
    target:
      entity_id: scene.day_mode
```

## Customization

Feel free to customize the configuration files to suit your needs. Add new automations, scripts, and custom components as needed.
