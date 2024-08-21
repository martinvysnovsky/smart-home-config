# RS485 Temperature Sensor

[Video](https://www.youtube.com/watch?v=-ZJnaKNHLR0)
[Online Modbus Decoder](https://npulse.net/en/online-modbus)

WARNING: it uses register address 10 to set device id

You can use script located in `/kincony/tools/set-rs485-device-address.yaml` to set up address.

## Set address

Workflow:

1. Add following action to switch:

```yaml
on_press:
  then:
    - lambda: |-
        esphome::modbus_controller::ModbusController *controller = id(device);
        esphome::modbus_controller::ModbusCommandItem set_address_command = esphome::modbus_controller::ModbusCommandItem::create_write_single_command(controller, 257, ${new_address});
        controller->queue_command(set_address_command);
        ESP_LOGI("ModbusLambda", "Device address set");
```

1. wait a little
1. remove sensor and use new address

### Command components

- `0x1` - device address
- `0x6` - command to set address
- `0x1`, `0x1` - register address in device (257)
- `0x0`, `0x14` - payload - new address we want to set = 20

Note: you do not need to include CRC bytes (last two bytes). They will be automatically calculated by Modbus controller

## Debugging

Use:

```yaml
logger:
  level: VERBOSE
```
