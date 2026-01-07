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
  ├─ configuration.yaml
  ├─ secrets.yaml
  ├─ automations.yaml
  ├─ scripts.yaml
  ├─ custom_components/
  │   └─ ...
  ├─ themes/
  │   └─ ...
  ├─ www/
  │   └─ ...
  └─ sensors/
      └─ ...
docs/
  └─ ...
```

- `configuration/`:
  - `configuration.yaml`: Main configuration file for Home Assistant.
  - `secrets.yaml`: File to store sensitive information like API keys (not included in the repository).
  - `automations.yaml`: Contains automation rules.
  - `scripts.yaml`: Contains custom scripts.
  - `custom_components/`: Directory for custom components.
  - `themes/`: Custom themes for the Home Assistant frontend.
  - `www/`: Static files for the frontend.
  - `sensors/`: Custom sensor configurations.
- `docs/`: Store file for documentation and tutorials for Home Assistant.

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

4. **Restart Home Assistant** to apply the new configurations.

## Usage

- Edit `configuration.yaml` to configure integrations and services.
- Update `automations.yaml` to add or modify automation rules.
- Customize the frontend using files in the `themes/` and `www/` directories.

## Automation Examples

Here are a few examples of automation rules included in this repository:

### Turn on lights at sunset

```yaml
- alias: "Turn on living room lights at sunset"
  trigger:
    platform: sun
    event: sunset
  action:
    service: light.turn_on
    entity_id: light.living_room
```

## Customization

Feel free to customize the configuration files to suit your needs. Add new automations, scripts, and custom components as needed.
