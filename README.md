# Pluggit PluggEasy Modbus Integration for Home Assistant

This repository provides a **Modbus configuration** for Pluggit PluggEasy (ASPV/ASPH) ventilation units and **template sensors** to display numeric registers as human-readable strings in Home Assistant.

## Contents

1. **[`modbus.yaml`](./modbus.yaml)**  
   - Defines the Modbus hub settings (port, baud rate, parity, etc.).  
   - Lists all sensors (input/holding registers) and switches (coils) to monitor and control the ventilation system.

2. **[`modbus_template.yaml`](./modbus_template.yaml)**  
   - Creates template sensors that convert numeric registers (e.g., defrost status, bypass position, actual working mode) into descriptive text.

## Usage

1. **Copy** both files (`modbus.yaml` and `modbus_template.yaml`) into your Home Assistant configuration folder (e.g., `/config`).

2. **Include** them in your main `configuration.yaml`:

   ```yaml
   modbus: !include modbus.yaml
   template: !include modbus_template.yaml
   ```

3. **Restart** Home Assistant to load the changes.

4. **Verify** that the serial device path, addresses, and offsets match your hardware. Adjust as needed if your device registers differ.

## Notes

- **Modbus Switches** let you toggle coils for manual boost, manual bypass, and more—no separate scripts needed.  
- **Template Sensors** provide friendly text descriptions for raw numeric registers (e.g., `0` → `"Closed"`, `1` → `"Open"`).  
