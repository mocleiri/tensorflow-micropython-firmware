# Tensorflow Micropyhon Example's Prebuilt Firmware

This repository holds pre-built firmware for the Tensorflow Micropython
Examples Project.

It is separate because each image is several MB large and its not
needed in the main repository.

This is a pre-1.0.0 firmware.  I was able to get the micro_speech example to work
using this version.

## ESP32 Microlite No SPI RAM 4MB Flash

We use a custom partition scheme with 1MB allocated to the file system and the rest 
reserved for the application code in the firmware.

This is mostly composed of the kitchen sink of tensorflow ops.

In the future I expect the filesystem to back to stock as we intend to allow the ops
to be loaded as required as native modules.

[esp32-microlite-nospiram-4m-pre-1.0.0.bin](firmware/esp32-microlite-nospiram-4m-pre-1.0.0.bin)

## ESP32 Microlite with SPI RAM and 16 MB Flash
We use a custom parition scheme with 13 MB allocated to the file system
and the rest reserved for the application code in the firmware.

This is mostly composed of the kitchen sink of tensorflow ops.

In the future I expect the filesystem to back to stock as we intend to allow the ops
to be loaded as required as native modules. 

[esp32-microlite-spiram-16m-pre-1.0.0.bin](firmware/esp32-microlite-spiram-16m-pre-1.0.0.bin)

## Version Information
| Project | Git Commit | Branch | Repository |
|  --- | --- | --- | --- |
| Tensorflow Microlite Examples | b52d60d911d219a113d825d2f9ef3fa91335f830 | master | https://github.com/mocleiri/tensorflow-micropython-examples |
| Tensorflow | 85c8b2a817f95a3e979ecd1ed95bff1dc1335cff | r2.4 |  https://github.com/tensorflow/tensorflow.git |
| Micropython | e95a8d65cdf5526d50f61cd7e27cefa97129e8b1 | microlite | https://github.com/mocleiri/micropython |
| ULAB | 6e0b9bb7d976f97685628e1f08af694a5d540b6a | mtf-latest | https://github.com/mocleiri/micropython-ulab.git |

## Flash Firmware

In windows after you plug in your board you need to use device manager to determine
which COM port the board is showing up under.

Once identified you can erase the flash and also flash the new firmware using these commands:
```
esptool.py --port COM5 erase_flash
esptool.py --chip esp32 --port COM5 write_flash -z 0x1000 ./firware.bin
```
