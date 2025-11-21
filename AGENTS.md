# Smart Home Configuration - Agent Guidelines

## Overview
This repository contains Home Assistant and Kincony (ESPHome) configuration for a smart home system. Primary languages: YAML, Python, C++.

## Build/Test Commands
- **Home Assistant**: `docker compose up -d` (from homeassistant/)
- **Kincony compile**: `esphome run configuration/home.yaml` (from kincony/)
- **Kincony logs**: `esphome logs configuration/home.yaml`
- **Restart HA**: `docker restart homeassistant`

## Code Style

### YAML (Home Assistant & ESPHome)
- Use 2-space indentation, never tabs
- Section headers with `#` followed by 80-char comment line for major sections
- Use snake_case for IDs and entity names
- Secrets via `!secret` directive, never hardcode sensitive data
- Include comments for complex automations/lambdas

### Python (ESPHome Custom Components)
- Follow ESPHome component patterns (codegen, config_validation)
- Import structure: esphome modules first, then standard library
- Use cv.Optional/cv.Required for config schema validation
- PascalCase for classes, snake_case for variables/functions

### C++ (ESPHome Components)
- Follow ESPHome namespace pattern (esphome::component_name)
- Use ESP_LOGD/ESP_LOGE for logging
- CamelCase for class names, snake_case for methods
- Include proper CRC validation for hardware communication
