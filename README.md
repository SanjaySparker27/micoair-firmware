# MicoAir H743 v2 Firmware

ArduPilot firmware for MicoAir H743 v2 flight controller.

## Files

| File | Description | Size |
|------|-------------|------|
| `MicoAir743v2_arducopter.apj` | ArduPilot firmware for Mission Planner/QGroundControl | 1.2 MB |
| `MicoAir743v2_arducopter.bin` | Raw binary firmware file | 1.4 MB |
| `MicoAir743v2_bl.hex` | Bootloader (Intel HEX format) | 55 KB |
| `MicoAir743v2_bl.bin` | Bootloader (binary format) | 20 KB |

## Flashing Instructions

### Option 1: Using Mission Planner (Recommended)
1. Connect your flight controller via USB
2. Open Mission Planner → Initial Setup → Install Firmware
3. Select "Load custom firmware" and choose `MicoAir743v2_arducopter.apj`
4. Follow the prompts to flash

### Option 2: Using DFU Mode
If the bootloader is corrupted or for initial flashing:

1. Enter DFU mode by holding BOOT button while powering on
2. Use STM32CubeProgrammer or dfu-util:
   ```bash
   dfu-util -a 0 -D MicoAir743v2_bl.bin -s 0x08000000
   ```

### Option 3: Using Betaflight Configurator
1. Put board in DFU mode
2. Select firmware file
3. Flash with "Full chip erase"

## Hardware Specifications

- **MCU**: STM32H743xx (Cortex-M7 @ 480MHz)
- **Flash**: 2 MB
- **RAM**: 1 MB
- **IMU**: BMI088 + BMI270 (dual IMU)
- **Barometer**: DPS310
- **Compass**: QMC5883L
- **OSD**: AT7456E
- **PWM Outputs**: 11 channels (DShot capable)

## Default UART Mapping

| UART | Function | Default Protocol |
|------|----------|------------------|
| USART1 | TELEM1 | MAVLink1 |
| USART2 | DJIO3 | MAVLink2 |
| USART3 | GPS | GPS |
| UART4 | TELEM2 | MAVLink1 |
| UART5 | RC_INPUT | RCIN |
| USART6 | Spare | - |
| UART7 | ESC Telemetry | ESC Telemetry |
| UART8 | BlueTooth | MAVLink1 |

## Default PWM Outputs

| PWM | Function | Notes |
|-----|----------|-------|
| PWM1 | Motor 1 | TIM1_CH4, BIDIR |
| PWM2 | Motor 2 | TIM1_CH3 |
| PWM3 | Motor 3 | TIM1_CH2, BIDIR |
| PWM4 | Motor 4 | TIM1_CH1 |
| PWM5 | Motor 5 | TIM3_CH4, BIDIR |
| PWM6 | Motor 6 | TIM3_CH3 |
| PWM7 | Motor 7 | TIM4_CH1, BIDIR |
| PWM8 | Motor 8 | TIM4_CH2 |
| PWM9 | Motor 9 | TIM4_CH3 |
| PWM10 | Motor 10 | TIM4_CH4 |
| PWM11 | Motor 11 | TIM12_CH2 |

## Build Information

- **ArduPilot Version**: Copter 4.6.0-dev
- **Build Date**: April 9, 2025
- **Board ID**: 1167 (AP_HW_MicoAir743v2)

## Links

- [ArduPilot Documentation](https://ardupilot.org/copter/)
- [MicoAir Official Website](http://micoair.com/)
- [ArduPilot GitHub](https://github.com/ArduPilot/ardupilot)

## License

This firmware is built from ArduPilot source code and is licensed under GPLv3.
