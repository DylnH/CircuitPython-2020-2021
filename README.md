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
