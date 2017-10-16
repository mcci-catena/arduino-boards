# arduino-boards
This repository contains Boards Manager file(.json) and the related packages for Arduino IDE.

The packages are is compressed files(.zip) from [ArduinoCore-samd](https://github.com/mcci-catena/ArduinoCore-samd) repository.

In order to successfully build and upload the code to the Catena boards, please look at the following steps:

1. Install latest version of Arduino IDE (https://www.arduino.cc/en/Main/Software).
2. Clone desired sketch repositories using 'git'.
3. Install MCCI Catena BSP using the .json file.
4. Install the required Arduino libraries using 'git'.
5. Build and Download.

## Installing the MCCI Catena BSP
Go to `File>Preferences>Settings` in the Arduino IDE and add `https://github.com/mcci-catena/arduino-boards/raw/master/BoardManagerFiles/package_mcci_index.json` to the list in `Additional Boards Manager URLs`. Use a comma(`,`) or add a new line after clicking a small icon next to the text box to separate multiple entries if needed.

## Installing the required libraries
Before you build, you must also install the following libraries.
*  https://github.com/mcci-catena/Adafruit_FRAM_I2C
*  https://github.com/mcci-catena/Catena4410-Arduino-Library
*  https://github.com/mcci-catena/arduino-lorawan
*  https://github.com/mcci-catena/Catena-mcciadk
*  https://github.com/mcci-catena/arduino-lmic
*  https://github.com/mcci-catena/Adafruit_BME280_Library
*  https://github.com/mcci-catena/Adafruit_Sensor
*  https://github.com/mcci-catena/RTCZero
*  https://github.com/mcci-catena/BH1750

The script `git-boot.sh` in [Catena4410-sketches/catea4450m101_sensor](https://github.com/mcci-catena/Catena4410-Sketches/tree/master/catena4450m101_sensor) repositorty will get all the things you need.

It's easy to run, provided you're on Windows, macOS, or Linux, and provided you have `git` installed. We tested on Windows with git bash from https://git-scm.org, on macOS 10.11.3 with the git and bash shipped by Apple, and on Ubuntu 16.0.4 LTS (64-bit) with the built-in bash and git from `apt-get install git`.

```shell
$ cd Catena4410-Sketches/catena4450m101_sensor
$ ./git-boot.sh
```

It has a number of advanced options; use `./git-boot.sh -h` to get help, or look at the source code [here](gitboot.sh).

**Beware of issue #18**.  If you happen to already have libraries installed with the same names as any of the libraries in `git-repos.dat`, `git-boot.sh` will silently use the versions of the library that you already have installed. (We hope to soon fix thisto at least tell you that you have a problem.)

## Build and Download

Shutdown the Arduino IDE and restart it, just in case.

Ensure selected board is 'Catena4410'/'Catena4450' (in the GUI, check that `Tools`>`Board "..."` says `"Catana4410"/"Catena4450"`.

Follow normal Arduino IDE procedures to build the sketch: `Sketch`>`Verify/Compile`.

## Load the sketch into the Catena

Make sure the correct port is selected in `Tools`>`Port`. 

Load the sketch into the Catena using `Sketch`>`Upload` and move on to provisioning.

### gitboot.sh and the other sketches
The sketches in other directories in this tree are for engineering use at MCCI. `git-boot.sh` does not necessarily install all the required libraries needed for building them. However, all the libraries should be available from https://github.com/mcci-catena/.

