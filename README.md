# Circuitpython-2020-2021

### [- Flashing Neopixel](https://drive.google.com/file/d/1xIV4XPiyzVJbje4d3qKjFSIho8wrQyDN/view?usp=sharing)

<img src="IMG_20201130_134731~2.jpg?raw=true" width="400" height="300">

``` python
import board
import neopixel
import time

dot = neopixel.NeoPixel(board.NEOPIXEL, 1)

while True:
    print("WARNING...May cause seizure...Whoops¯\_(ツ)_/¯")
    dot.fill((0,0,255))
    time.sleep(.08)
    dot.fill((0,255,255))
    time.sleep(.08)
    dot.fill((255,0,255))
    time.sleep(.08)
    dot.fill((0,255,0))
    time.sleep(.08)  
```
_________________________________________________________________________________________________________________________________________________________________________

### [- Blinking LED](https://drive.google.com/file/d/1xfdP2e0o15KPA65ubKCEXpOUFBuyUwMZ/view?usp=sharing)

<img src="IMG_20201124_115341~2.jpg?raw=true" width="400" height="300">

### - Wiring Diagram

<img src="Screenshot%202020-12-18%20at%209.51.50%20PM.png?raw=true" width="300" height="225">

``` python
import board
import digitalio
import time
 
led = digitalio.DigitalInOut(board.A1)
led.direction = digitalio.Direction.OUTPUT
 
while True:
    led.value = True
    time.sleep(0.5)
    led.value = False
    time.sleep(0.5)  
```
_________________________________________________________________________________________________________________________________________________________________________

### [- Capacitive Touch Servo](https://drive.google.com/file/d/1xRx4ZBBYFXx2lvASjYpLX9V4Qhr1xc2n/view?usp=sharing)

<img src="IMG_20201130_134047.jpg?raw=true" width="400" height="300">


### - Wiring Diagram

<img src="Screenshot%202020-12-18%20at%208.52.04%20PM.png?raw=true" width="300" height="225">

``` python
import board
import time
import pulseio
import servo
import touchio

#Servo setup
pwm = pulseio.PWMOut(board.A2, duty_cycle=2 ** 25, frequency=25)

my_servo = servo.ContinuousServo(pwm)

# Touch pins setup
touch_A0 = touchio.TouchIn(board.A0)
touch_A1 = touchio.TouchIn(board.A1)

# Code
while True:

    if touch_A0.value:
        print("oh im dizzy") # A0 has been touched
        my_servo.throttle = 1 # Moves to 180
       
    if touch_A1.value:
        print("please, stop spinning me") # A1 has been touched
        my_servo.throttle = -1 # Moves to 0

    time.sleep(0.10)
```
_________________________________________________________________________________________________________________________________________________________________________

### [- Distance Sensor](https://drive.google.com/file/d/1xwy4iNiz7cOKDy6K5ZTevV009zKRLCnS/view?usp=sharing)

<img src="IMG_20201204_145331.jpg?raw=true" width="400" height="300">

### - Wiring Diagram

<img src="Screenshot%202020-12-18%20at%209.28.11%20PM.png?raw=true" width="300" height="225">

``` python
import board
import neopixel
import adafruit_hcsr04
import simpleio

HCSR04 = adafruit_hcsr04.HCSR04(echo_pin=board.A1, trigger_pin=board.A2)
neopixel = neopixel.NeoPixel(board.NEOPIXEL, 1, brightness=.1)

R = 0
B = 0
G = 0

while True:
    try:
        dist = HCSR04.distance
        if dist < = 10:
            R = simpleio.map_range(dist, 0, 25, 255, 0)
            B = simpleio.map_range(dist, 10, 25, 0, 255)
            G = simpleio.map_range(dist, 25, 40, 0, 255)
        else:
            R = simpleio.map_range(dist, 0, 25, 255, 0)
            B = simpleio.map_range(dist, 25, 40, 255, 0)
            G = simpleio.map_range(dist, 25, 40, 0, 255)
        neopixel.fill((int(R), int(G), int(B)))
```
_________________________________________________________________________________________________________________________________________________________________________

### [- Photointerrupter](https://drive.google.com/file/d/1zR5QSH5Q5MA70bo70wDd5sJEvBPeExNe/view?usp=sharing)

<img src="IMG_20201218_191443.jpg?raw=true" width="400" height="300">

### - Wiring Diagram

<img src="Screenshot%202020-12-18%20at%209.15.44%20PM.png?raw=true" width="300" height="225">

``` python
from digitalio import DigitalInOut, Direction, Pull
import time
import board

Int = DigitalInOut(board.A2)
Int.direction = Direction.INPUT
Int.pull = Pull.UP

counter = 0

state = False
photo = False

max = 4
start = time.time()
while True:
    photo = Int.value
    if photo and not state:
            counter += 1
    state = photo

    remaining = max - time.time()

    if remaining <= 0:
        print("I see you this many times:", str(counter))
        max = time.time() + 4
        counter = 0
```
_________________________________________________________________________________________________________________________________________________________________________

### - Credit


- System of wiring Diagrams influenced by [Alden Dent]( https://github.com/adent11)

