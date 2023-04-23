# Aqara Presence Sensor FP2
Aqara Presence Sensor FP2 is using ESP32 (single core mode) with 16MBit SPI Flash and PSRAM, the radar is IWR6843AOP from Ti.



| UART | Test Point |
|:-----:|:-----:|
|   TX  |  TP8 |
|   RX  |  TP9 |
| GPIO0 | TP28 |
|  GND  |      |

To dump the flash content, you can use esptool.py to read. For example,
```
esptool.py --baud 230400 --port COM2 read_flash 0x0 0x1000000 fw-backup-16M.bin
```

To flash firmwares, you can also use esptool.py to program. For example,
```
esptool.py --port COM2 write_flash -z 0x1000 bootloader.bin 0x8000 partitions.bin 0x11000 otadata.bin 0x13000 phy_init.bin 0x20000 aqara_fw1.bin 0x220000 aqara_fw1.bin
```