## Voroscope Firmware GRBL-HAL

#### A fork of the grblHal RP2040 driver

This firmware targets the Raspberry Pi Pico MCU on the BigTreeTech SKR Pico 1.0 motion control board.

### Contents

- [Environment setup](#environment-setup)
- [Build steps](#build-steps)

### Environment setup

These instructions require a Linux distribution; macOS may be used with a different toolchain.

#### Windows configuration

If using Windows, it is recommended to install the Pico SDK and the build toolchain in an Ubuntu distribution under the Windows Subsystem for Linux (WSL), which has a dedicated extension in VSCode.

Open a PowerShell or Command Prompt terminal with administrator privileges and install WSL:

```ps1
wsl --install
```

To view a listing of available Linux distros:

```ps1
wsl --list --online
```

However, by default, Ubuntu should be automatically installed on the system. From this point, you may run all following commands in an Ubuntu terminal accessed via the Windows terminal program.

#### Pico SDK

Create a directory to store the Pico SDK:

```zsh
mkdir -p ~/Code/pico
cd ~/Code/pico
```

Clone the SDK repository (only include the master branch):

```zsh
git clone https://github.com/raspberrypi/pico-sdk.git --recurse-submodules --branch master
```

Occasionally, you may wish to update the SDK:

```zsh
git pull
git submodule update --remote
```

Create an environment variable called `PICO_SDK_PATH` that points to the location of the SDK (you may wish to automate variable creation in the relevant environment file):

```zsh
export PICO_SDK_PATH=~/Code/pico/pico-sdk
```

Install the build toolchain:

```zsh
sudo apt install cmake gcc-arm-none-eabi libnewlib-arm-none-eabi build-essential
```

Clone the source repository:

```zsh
cd ~/Code
git clone git@github.com:cellino-biotech/voroscope-firmware-grblhal-RP2040.git --recurse-submodules
```

### Build steps

Enter the project directory:

```zsh
cd ~/Code/voroscope-firmware-grblhal-RP2040
```

If it does not exist, create a `build` directory:

```zsh
mkdir build
```

Identify the source and build directories (only needs to be performed once):

```zsh
cmake -S . -B ./build
```

Run the build process:

```zsh
cmake --build ./build
```
