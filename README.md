# My Smart Home Configuration

This repository contains the configuration files for my smart home setup using [Home Assistant](https://www.home-assistant.io/).

## Table of Contents

- [Overview](#overview)
- [Directory Structure](#directory-structure)
- [Installation](#installation)
- [Usage](#usage)
- [Automation Examples](#automation-examples)
- [Customization](#customization)
- [Contributing](#contributing)
- [License](#license)

## Overview

This repository includes all the YAML configuration files, scripts, and custom components used to manage and automate my smart home. The setup integrates various smart devices and services to provide a cohesive and automated home experience.

## Directory Structure

```
configuration/
├── configuration.yaml
├── secrets.yaml
├── automations.yaml
├── scripts.yaml
├── custom_components/
│ └── ...
├── themes/
│ └── ...
├── www/
│ └── ...
├── sensors/
│ └── ...
└── docs/
```

- `configuration.yaml`: Main configuration file for Home Assistant.
- `secrets.yaml`: File to store sensitive information like API keys (not included in the repository).
- `automations.yaml`: Contains automation rules.
- `scripts.yaml`: Contains custom scripts.
- `custom_components/`: Directory for custom components.
- `themes/`: Custom themes for the Home Assistant frontend.
- `www/`: Static files for the frontend.
- `sensors/`: Custom sensor configurations.
- `docs/`: Store file for documentation and tutorials.

## Installation

1. **Clone the repository**:

```bash
git clone https://github.com/yourusername/homeassistant-config.git
cd configuration
```

2. **Copy the configuration files** to your Home Assistant configuration directory, typically located at `/config`:

```bash
cp -r * /config
```

3. **Install custom components** (if any) by copying them to the appropriate directory within your Home Assistant setup.

4. **Restart Home Assistant** to apply the new configurations:

```bash
docker restart homeassistant  # If using Docker
```

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

## Contributing

Contributions are welcome! Please fork the repository and create a pull request with your changes.

## License

This project is licensed under the MIT License. See the LICENSE file for more details.
