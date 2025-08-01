```
                                                       ▀▀▀▀▀     ▀▀▀▀▀          ▀▀█▀▀
                                                       ▄▀▀▀▄  ▄  ▄▀▀▀▄  ▄  ▄▀▀▀▄  █  ▄▀▀▀▄
                                                       █   █  █  █   █  █  █   █  █  █   █
                                                        ▀▀▀   █   ▀▀▀   █   ▀▀▀   ▀   ▀▀▀
                                                              █      ▄▄▄█▄▄▄    █   █  
                                                              ▀      █  █  █     █▄█
                                                            ▀▀▀▀▀    █  █  █      ▀
                                                                     ▀  ▀  ▀
▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄▄
       
```
# TOTEM split keyboard

TOTEM is 34 keys column-staggered split keyboard made by @geigeigeist. It uses the Seeed XIAO RP2040.

You can use this command to compile the firmware

```
# install prerequisites
sudo apt install -y git make gcc avr-libc avrdude dfu-programmer dfu-util libusb-dev libusb-1.0-0-dev libnewlib-arm-none-eabi gcc-arm-none-eabi python3 python3-pip python3-venv

# start a python environment for qmk
python3 -m venv .venv-qmk
source .venv-qmk/bin/activate

# download qmk firmware repo
git clone https://github.com/vial-kb/vial-qmk
cd vial-qmk

# install the qmk software
pip install qmk
qmk setup

# in case of errors, you can reset the submodules and re-init them
# git submodule update --init --recursive --force

# now, for the layout:
TOTEMLAYOUT="~/layout/totem"
# create symlink to TOTEM layout inside the vial-qmk firmware folder
ln -s $TOTEMLAYOUT keyboards/totem

# finally, make the left and right hand side, while also renaming the left and right hand side
make totem:vial:uf2-split-right ; mv .build/totem_vial.uf2 .build/totem_vial_right.uf2 
make totem:vial:uf2-split-left ; mv .build/totem_vial.uf2 .build/totem_vial_left.uf2

echo "Find your firmware in $pwd/.build/"
```
