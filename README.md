# Circuitpython-2020-2021

### [- Flashing Neopixel](https://drive.google.com/file/d/1xIV4XPiyzVJbje4d3qKjFSIho8wrQyDN/view)

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
### [- Blinking LED](https://drive.google.com/file/d/1xfdP2e0o15KPA65ubKCEXpOUFBuyUwMZ/view)

<img src="IMG_20201124_115341~2.jpg?raw=true" width="400" height="300">

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
### [- Capacitive Touch Servo](https://drive.google.com/file/d/1xRx4ZBBYFXx2lvASjYpLX9V4Qhr1xc2n/view)

<img src="Screenshot%202020-09-23%20at%205.05.33%20PM.png" width="350" height="228">

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
touch_A0 = touchio.TouchIn(bo
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
