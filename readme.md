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

## Configuration

Betaflight configurator, "Configuration" tab

Receiver section : 
    Serial-base receiver
    SBUS

RSSI (Signal Strenght) section :
    RSSI_ADC : Off ????

System Configuration section :
    Gyro update frequency : 8 KHZ
    PID loop frequency : 8 KHZ
    Accelerometer : ON (for motors vibrations measurement)
    
 Other Features Section
     Airmode ON
     All others OFF
     
 ESC/Motor Features Section :
    Multishot
    


## Motors direction

Connect a battery, and with the help of motors tab in betaflight, check motors directions.

## flash and configure ESC

Run blheli configurator
Flash all escs to last version (16.6 at writing time)
Change motor direction for motors tested with wrong direction.

Recheck motors direction

Set beacon delay to 2 minutes
Set beep strength to 2

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

=====================>>>>>>>>

## Create a new model on the transmitter
## Link receiver

Red LED on RX means it’s not bound or not detecting TX. To bind, enter Bind mode on TX, hold down F/S button on RX and power on. After a few seconds, Green LED will light up indicates binding has completed.

To setup up failsafe, power on both TX and RX. Set your TX channels to desire positions, and press the F/S button on the RX. The green LED should flashes and indicates F/S has been setup. Please confirm if F/S is now working as expected by turning off TX. To remove F/S, simply rebind the RX.

## Modes

configuration battery scale


## Receiver

## Anti-gravity

## notch filters

