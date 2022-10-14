# ESE5190-Lab2-Setup
Name: Yuan Chi

Setup environment: 2019 MacBook Air 13-inch, MacOS Monterey 12.6<br>
Processor: 1.6 GHz Intel Core i5<br>
Memory: 8 GB 2133 MHz LPDDR3<br>

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

## 6. Install CMake Tools in VSCode
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

## 8. Add folder to workspace and choose a compiler
Go to the File menu and click on "Add Folder to Workspace..." and navigate to pico-examples repo and click "Okay";<br>
Select "GCC for arm-none-eabi" for compiler";<br>
<img width="1023" alt="image" src="https://user-images.githubusercontent.com/108168201/195749973-35d15a77-5af1-4be9-acc7-dc00752f48c0.png">

## 9. Problem Solving
Problem:<br>
<img width="416" alt="image" src="https://user-images.githubusercontent.com/108168201/195751067-80d19585-4c26-4318-8e56-9c4952e63705.png">

Solution:<br>
Setting an environment variable through CMake tools in VSCode;<br>
<img width="473" alt="image" src="https://user-images.githubusercontent.com/108168201/195751452-3a066b57-89c9-4a53-9f8f-f689cf73c6ab.png"><br>
<img width="462" alt="image" src="https://user-images.githubusercontent.com/108168201/195751495-c4e87746-d1cb-4240-9ac7-f2be473db08c.png">

## 10.Build "Hello World"
Cd into pico-examples and create a build directory:<br>

     $ cd pico-examples
     $ mkdir build
     $ cd build
     
Set the Pico_SDK_PATH (If clone pico-sdk and pico-examples repositories into the same directory side-by-side):

      $ export PICO_SDK_PATH=../../pico-sdk
      
Prepare cmake build directory by running cmake..:

     $ cmake ..
<img width="571" alt="image" src="https://user-images.githubusercontent.com/108168201/195753688-0aa2aada-54a7-4064-894b-2a0ff7c394cd.png">

Change directory into the "hello_world" directory inside the "pico-examples/build" tree, and run make:

     $ cd hello_world
     $ make -j4
<img width="573" alt="image" src="https://user-images.githubusercontent.com/108168201/195754127-454cdb58-9dd4-4fc8-878d-76a011930b63.png">
This will build two separate examples programs in the "hello_world/serial/" and "hello_world/usb/" directories;<br>
Amongst other targets, we have now built:<br>
• serial/hello_serial.elf, which is used by the debugger<br>
• serial/hello_serial.uf2, which can be dragged onto the RP2040 USB Mass Storage Device (UART serial binary)<br>
• usb/hello_usb.elf, which is used by the debugger<br>
• usb/hello_usb.uf2, which can be dragged onto the RP2040 USB Mass Storage Device (USB serial binary)<br>
Where hello_serial directs stdio to UART0 on pins GP0 and GP1, and hello_usb directs stdio to USB CDC serial.<br>


## 11. Flash and run "Hello World"
Connect the laptop to Raspberry Pi using a micro-USB cable;<br>
Hold down the "root" button and press "reset" button at the same time;<br>
Push "hello_usb.uf2" in Raspberry Pi;<br>
Enter the console:

     $ ls /dev/tty.*
     $ screen /dev/tty.board_name 115200
     
 "Hello World!" appears in the console:<br>
<img width="569" alt="image" src="https://user-images.githubusercontent.com/108168201/195757044-e406ab11-2849-40bb-8d7e-9c93688072b2.png">

