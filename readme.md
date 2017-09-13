To review using joshua's video : https://www.youtube.com/watch?v=JkggzZySIqs

# Betaflight Configuration Checklist

## Flash betaflight last version

Before installation : 

- To get the target, use following command in CLI

    version

- To dump current configuration, use following command in CLI and save result in a text file

    diff
    
- To switch in DFU mode, use following command in CLI. Then you could install betaflight

    dfu

## Connect to betaflight configurator

If DFU when connected : 

    $ systemctl stop ModemManager.service
    
## Motors ordering and direction

Connect a battery, and with the help of motors tab in betaflight, check motors directions.

## flash and configure ESC

Run blheli configurator
Flash all escs to last version (16.6 at writing time)
Change motor direction for motors tested with wrong direction.

Recheck motors direction

Set beacon delay to 2 minutes
Set beep strength to 2

## Check orientation

Betaflight configurator, "configuration" tab, "Board and Sensor Alignment" section. Normally, you justt have to change yaw field.

## Setup ports

    USB VCP : MSP 115200
    UART 1 : Seria RX

## Configuration Tab

Betaflight configurator, "Configuration" tab

System Configuration section :
    Gyro update frequency : 8 KHZ
    PID loop frequency : 8 KHZ
    Accelerometer : ON (for motors vibrations measurement and for crash recovery feature (bflight >= 3.2))

Receiver section : 
    Serial-base receiver
    SBUS

RSSI (Signal Strength) section :
    RSSI_ADC : Off ????

Features Section
     Airmode ON
     OSD ON (depends on fc, omnibus yes, Lux no, RevoF4 no)
     Antigravity ON
     Dynamic filter ON (betaflight >= 3.2)
     
ESC/Motor Features Section :
    Dshot for racerstar
    Multishot for lux and DYS XM20A

## Receiver tab

- Create a new model on the transmitter
- Link receiver

    Red LED on RX means it’s not bound or not detecting TX. To bind, enter Bind mode on TX, hold down F/S button on RX and power on. After a few seconds, Green LED will light up indicates binding has completed.

    To setup up failsafe, power on both TX and RX. Set your TX channels to desire positions, and press the F/S button on the RX. The green LED should flashes and indicates F/S has been setup. Please confirm if F/S is now working as expected by turning off TX. To remove F/S, simply rebind the RX.


Turn on receiver
 - check channels are ok (4 + arm button)
 - check channels are centered @1500
 - check channel endpoints (1000 and 2000)
 
 Set stickmin to 1010 (above throttle point)
 
 Set stickmax to 1090

## Modes

Set ARM_MODE
Set Beeper ?
Set PREARM for 2 stages arming)

## Failsafe

Remove props, arm the quad, raise throttle a bit and turn off transmitter

## OSD

Configure osd, use previous dump if needed.


## configuration battery scale

??

## Anti-gravity

??

## notch filters

??

To set in an other page
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

