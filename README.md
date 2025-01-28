# Quick note:
- Test env: Ubuntu 24.04 LTS
- IDE: Visual Studio Code (code, build, flash, debug)
- HW: ESP32-C6-DevKitC-1

## Step 1:
- Clone wasm-micro-runtime to ~/

## Step 2:
- Clone this repo to local (e.g. to ~/WASM)

## Step 3:
- check the path for IDF and WAMR

  For IDF, I added this code to ~/.bashrc so I can run the command get_idf to init IDF env.
  ```c
      alias get_idf='. $HOME/esp/esp-idf/export.sh'
  ```
  For WAMR, I add the WAMR path to ~/.profile as follow:
  ```c
    if [ -d "$HOME/wasm-micro-runtime" ] ; then
        PATH="$HOME/wasm-micro-runtime:$PATH"
    fi
  ```

## Step 4:
- Open project in Visual Studio Code and configure:
    + Flash method: UART
    + Port: /dev/ttyUSB0 (this port can be different on other PC). Sometimes we need to open this port manually by using command: sudo chmod a+rw /dev/ttyUSB0
    + IDF_TARGET: esp32c6 chip (via ESP-PROG)
- Update WAMR path:
    + Modify main/idf_component.yml to update override_path to link to WAMR directory
