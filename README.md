# argon-particle-flipper
building flipperzero firmware for the particle Argon

# Building Flipper-Zero Firmware for Particle Argon

Flipper-Zero is a multi-tool device designed for hardware debugging, protocol sniffing, and signal analysis. It is an open-source hardware and firmware project, which means that you can modify and customize it to fit your needs. In this project, we will build Flipper-Zero firmware for Particle Argon using .ino files and necessary libraries.

## Requirements

Before we start building the firmware, we need to make sure that we have all the necessary tools and software installed.

- [Particle CLI](https://docs.particle.io/tutorials/developer-tools/cli/)
- [Arduino IDE](https://www.arduino.cc/en/software)
- [Flipper-Zero firmware repository](https://github.com/flipperdevices/flipper-zero-firmware)

## Setting up the Environment

First, let's clone the Flipper-Zero firmware repository. Open a terminal and run the following command:

```
git clone https://github.com/flipperdevices/flipper-zero-firmware.git
```

Next, we need to install the necessary libraries. Open Arduino IDE and go to **Sketch > Include Library > Manage Libraries**. Search for and install the following libraries:

- Adafruit GFX Library
- Adafruit SSD1306
- Adafruit BusIO

Now, we need to install the Particle firmware build toolchain. Open a terminal and run the following command:

```
particle update
```

## Building the Firmware

To build the Flipper-Zero firmware for Particle Argon, we need to modify the source code slightly. Open the `flipper-zero-firmware/flipper-zero.ino` file in Arduino IDE. Add the following lines at the beginning of the file:

```
#include "Particle.h"
#include "flipper.h"
```

Next, we need to replace the `setup()` and `loop()` functions with the following code:

```
void setup() {
  flipper_setup();
}

void loop() {
  flipper_loop();
}
```

Save the file and close Arduino IDE. Open a terminal and navigate to the `flipper-zero-firmware` directory. Run the following command to build the firmware:

```
particle compile argon . --saveTo firmware.bin
```

This will compile the firmware and save the binary file as `firmware.bin`. We can now flash this firmware to our Particle Argon device.

## Flashing the Firmware

To flash the firmware to our Particle Argon device, we need to put it in DFU mode. To do this, hold down the MODE button and tap the RESET button. The device should start flashing yellow, indicating that it is in DFU mode.

Next, run the following command to flash the firmware:

```
particle flash --usb firmware.bin
```

This will flash the firmware to the device. Once the flashing process is complete, the device will reset and start running the new firmware.

## Conclusion

In this project, we have built the Flipper-Zero firmware for Particle Argon using .ino files and necessary libraries. We have also learned how to modify the source code and flash the firmware to the device. 
