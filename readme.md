# quad-configuration-checklist

## Flash betaflight last version

## Connect to betaflight configurator

If DFU when connected : 

    $ systemctl stop ModemManager.service

## Setup ports

    USB VCP : MSP 115200
    UART 1 : Seria RX

## Check orientation

Betaflight configurator, "configuration" tab, "Board and Sensor Alignment" section. Normally, you justt have to change yaw field.

## Motors direction

Connect a battery, and with the help of motors tab in betaflight, check motors directions.

## flash and configure ESC

Run blheli configurator
Flash all escs to last version (16.6 at writing time)
Change motor direction for motors tested with wrong direction.

## ESC calibration

http://blog-rc.tidom.net/calibrer-esc-betaflight-cleanflight/

Open betaflight configurator and connect it to your board
esc protocol : multishot
min_command = 1000
max_throttle = 2000
Save, reboot, check configuratin
Go to motors tab
set motors to 2000
Branch lipo
Wait end of music
set motors to 1000
Wait end of music
unbranch lipo

Run blheli configurator
Check PM Min Throttle et PPM Max Throttle. Ces deux valeurs ne doivent PAS être égale à respectivement 1000 et/ou 2020. 

Run betaflight configurator to set 
min throttle = max(minmotor 1, minmotor2, minmotor3, minmotor4) +15
max throttle = min(max motor1...

motor stop

ports

telemetry

air_mode

configuration battery scale


## Receiver

