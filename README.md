# Circuitpython-2020-2021

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

``` python
import board
import time
import pulseio
import servo
import touchio

#Servo setup
pwm = pulseio.PWMOut(board.A2, duty_cycle=2 ** 25, frequency=25)

my_srvo = servo.ContinuousServo(pwm)

# Touch pins setup
Tch_A0 = touchio.TouchIn(bo
Tch_A1 = touchio.TouchIn(board.A1)

# Code
while True:

    if Tch_A0.value:
        print("oh im dizzy") # A0 has been touched
        my_srvo.throttle = 1 # Moves to 180
       
    if Tch_A1.value:
        print("please, stop spinning me") # A1 has been touched
        my_srvo.throttle = -1 # Moves to 0

    time.sleep(0.10) 
```
