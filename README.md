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

## 6. Install CMake Tools in VSC
Type Cmd+shift+X and search for "CMake Tools";<br>
Click on the entry in the list;<br>
Click on the install button;<br>
<img width="1025" alt="image" src="https://user-images.githubusercontent.com/108168201/195746036-5498c639-0f64-448c-b749-fc2eab02acb7.png">

## 7. Set the Pico_SDK_PATH environment virable
Navigate to the pico-examples directory;<br>
Create a .vscode directory and add a file called settings.json;<br>
Copy these lines to settings.json;<br>

     {
     "cmake.environment": {
         "PICO_SDK_PATH": "../../pico-sdk"
     },
     "C_Cpp.default.configurationProvider": "ms-vscode.cmake-tools"
     }
     

Click on the Cog Wheel at the bottom of the navigation bar on the left-hand side of the interface and select "Settings";<br>
Click on the "Extensions" and "CMake Tools configuration";<br>
Scroll down to " Cmake: Generator: and enter " Unix Makefiles" into the box;<br>
<img width="1023" alt="image" src="https://user-images.githubusercontent.com/108168201/195748545-9f13a2a6-9b3d-4883-a9f0-09a82742f235.png">

