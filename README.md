# ESE5190-Lab2-Setup
Name: Yuan Chi

Setup environment: 2019 MacBook Air 13-inch, MacOS Monterey 12.6


## 1. Install Homebrew
     $ /bin/bash -c "$(curl -fsSL
     https://raw.githubusercontent.com/Homebrew/install/master/install.sh)"
   
## 2. Install toolchain
     $ brew install cmake
     $ brew tap ArmMbed/homebrew-formulae
     $ brew install arm-none-eabi-gcc
     
## 3. Create Pico directory
     Cd Document
     Mdkir pico
     Cd pico
     
## 4. Clone Pico-sdk and Pico-examples
          $ git clone -b master https://github.com/raspberrypi/pico-sdk.git
          $ cd pico-sdk
          $ git submodule update --init
          $ cd ..
          $ git clone -b master https://github.com/raspberrypi/pico-examples.git

## 5. Download Visual Studio Code
https://code.visualstudio.com/download

