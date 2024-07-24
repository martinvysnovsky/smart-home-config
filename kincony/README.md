# Kincony Configuration

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
  ├─ secrets.yaml
  └─ ...
docs/
  └─ ...
```

- `configuration/`: Store configuration files.
  - `secrets.yaml`: File to store sensitive information like API keys (not included in the repository).
- `docs/`: Store file for documentation and tutorials for Home Assistant.

## Installation

1. **Clone the repository**:

```bash
git clone https://github.com/martinvysnovsky/smart-home-config.git
cd smart-home-config/kincony
```

2. **Install ESPHome CLI** to your computer

[ESPHome CLI Installation](https://esphome.io/guides/installing_esphome)

## Usage

### Compile and upload

```bash
esphome run configuration/home.yaml
```

### View logs

```bash
esphome logs configuration/home.yaml
```

## Customization

Feel free to customize the configuration files to suit your needs.
