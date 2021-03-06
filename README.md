# Flick
Resources for Flick range

# Setup Flick
Just run the following script in a terminal window and Flick will be automatically setup.
```bash
# Run this line and Flick will be setup and installed
curl -sSL https://pisupp.ly/flickcode | sudo bash
```

# Python API (Coming soon)

# Command Line
```bash
# Run a demo script to test the various gestures
python ~/Flick/flick/flickdemo.py
```

# Hardware tips
You can find a full quick start guide at the [MakerZone Flick Quick Start and FAQ](https://www.pi-supply.com/make/flick-quick-start-faq) where we also provided a pinout diagram for all the boards.

## Flick large pin mapping 
We arranged the connectivity so that only the pins on the left side of Raspberry Pi's header are required to be connected to the Flick Large.

**Flick -> Raspberry Pi**
```bash
LED2 (Red)   -> Pin 15
LED1 (Green) -> Pin 7
GND          -> Pin 9
TS           -> Pin 13
Reset        -> Pin 11
SCL          -> Pin 5
SDA          -> Pin 3
VCC          -> Pin 1
```
### Controlling the dual LED on Flick large
We have provided a dual LED for additional customisable feedback on the Flick large. The red LED is connected to Pin 15/GPIO22 whereas the green LED is connected to Pin7/GPIO4.
You can drive these LEDs programmatically or via the command line.

#### Bash
This will turn on the green LED
```bash
gpio -g mode 22 out
gpio -g write 22 1
```
This will turn off the red LED
```bash
gpio -g mode 4 out
gpio -g write 4 0
```

#### Python
This will turn off the green using RPi.GPIO
```Python
import RPi.GPIO as GPIO
GPIO.setmode(GPIO.BCM)
GPIO.setup(22, GPIO.OUT)
GPIO.output(22, True)
```

This will turn off the green LED using gpiozero
```Python
from gpiozero import LED
led = LED(22)
led.on()
```

# Additional information
The Flick boards use the MGC3130 3D gesture controller based on Microchip's patented Gestic© technology. You can find more at [Microchips's website](http://www.microchip.com/design-centers/capacitive-touch-sensing/gestic-technology/overview)

The Flick boards can also be used with Microchip [Aurea Software Package](http://www.microchip.com/mymicrochip/filehandler.aspx?ddocname=en565745) and the [MGC3130 Development Kit Hillstar](http://www.microchip.com/DevelopmentTools/ProductDetails.aspx?PartNO=dm160218). The Aurea comes with a demo application which can be used to test the boards. It also has a mouse emulator and a media player controller.
