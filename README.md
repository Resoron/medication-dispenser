# Medicine Delivery System PCB (v1.0)

Custom controller board for an automatic medication dispenser — ENGE 1414, Group B10.

## Board overview
- **MCU:** ESP32-S3-WROOM-1-N8 (Wi-Fi/BLE, native USB for flashing)
- **Power:** USB-C (5 V) → NCP1117LP 3.3 V LDO; motors run directly from 5 V
- **Motors:** 4× 28BYJ-48 steppers driven by 2× ULN2803A (JST-XH 5-pin connectors J2–J5)
- **Display:** 16×2 LCD with PCF8574 I2C backpack, BSS138 3.3 V ↔ 5 V level shifter (JST-XH 4-pin, J6)
- **Inputs:** 3 external buttons (JST-XH 2-pin), on-board RESET and BOOT
- **Protection:** USBLC6-2SC6 ESD on USB D+/D−, 470 µF bulk cap on the motor rail

## GPIO map
| Function | GPIO |
|---|---|
| Motor 1 / 2 (ULN2803 #1) | IO4–7 / IO15–18 |
| Motor 3 / 4 (ULN2803 #2) | IO35–38 / IO39–42 |
| LCD I2C SDA / SCL | IO8 / IO9 |
| Buttons | IO1, IO2, IO14 |
| Status LED | IO21 |
| USB D− / D+ | IO19 / IO20 |
| Boot / Reset | IO0 / EN |
| Free (future homing sensors) | IO10–13, IO47, IO48 |

## Repository layout
```
hardware/     KiCad project (open Medication_System_Final.kicad_pro)
production/   Gerbers + drill files as ordered (gerbers.zip) and BOM.csv
```

## History
- `servo-c6` tag: earlier 2-servo design on an ESP32-C6
- `master`: final stepper design on the ESP32-S3 (the version that was ordered)
