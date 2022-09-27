# CircuitPython
This repository will actually serve as a aid to help you get started with your own template.  You should copy the raw form of this readme into your own, and use this template to write your own.  If you want to draw inspiration from other classmates, feel free to check [this directory of all students!](https://github.com/chssigma/Class_Accounts).
## Table of Contents
* [Table of Contents](#TableOfContents)
* [CircuitPython_Servo](#CircuitPython_Servo)
* [CircuitPython_LCD](#CircuitPython_LCD)
* [NextAssignmentGoesHere](#NextAssignment)
---




## CircuitPython_Servo

### for this project we just needed to make a servo turn  using python
this project was very simple as it was the one of our first project of the year so all we needed was the arduino and the computer and the servo 
here is the code i used:
```python
import time  #importing all the things
import board
import pwmio
from adafruit_motor import servo

pwm = pwmio.PWMOut(board.A2, duty_cycle=2 ** 15, frequency=50) # this is where we set of the code


my_servo = servo.Servo(pwm) #defining my serco 

while True:
    for angle in range(0, 180, 5):  # tells it how fast to go and where to stop
        my_servo.angle = angle
        time.sleep(0.05) # pauses it for a second 
    for angle in range(180, 0, -5):  # same code just with the values to turn it around            
        my_servo.angle = angle
        time.sleep(0.05)

```

### Evidence


### Wiring
![download](https://user-images.githubusercontent.com/71406784/192608178-834fa94a-b170-454e-8a54-c0727bf4316f.png)

### Reflection

I didnt have any real problems this project, just had to set up all the wires and the servo in code



## CircuitPython_LCD

### Description & Code

```python
  import time #huge thanks to gaby for help on this code
    import board
    import adafruit_hcsr04
    import neopixel
    import simpleio

    sonar = adafruit_hcsr04.HCSR04(trigger_pin=board.D5, echo_pin=board.D6)   # creating sonar variable
    dot = neopixel.NeoPixel(board.NEOPIXEL, 10, brightness=0.5) # creating dot variable 

    r = 0  # setting my three colors ints to 0
    g = 0
    b = 0


    while True:

    try:
        distance = sonar.distance # setting the variables
        print((distance))

        if distance < 5: # start of if statement if distance is less than f then set the color vaiables to red
            r = 255 # acitivated variable
            g = 0
            b = 0
        elif distance > 5 and distance < 20: # this else statement creates the second color preset
            r = simpleio.map_range(distance, 5, 20, 255, 0) # set up the distance color conection
            b = simpleio.map_range(distance, 5, 20, 0, 255) # set up the distance color conection
            g = 0 
            r = int(r)   # ints set up
            g = int(g)
            b = int(b)
        elif distance > 20 and distance < 35: # this else statement creates the second color preset
            r = 0
            b = simpleio.map_range(distance, 20, 35, 255, 0)  # acitivated variable with the var distance to get blue and green going 
            g = simpleio.map_range(distance, 20, 35, 0, 255)
            r = int(r)
            g = int(g)   # ints set up
            b = int(b)
        elif distance > 35:  #else if for > than 35
            r = 0    #  vars  set to pure green if its out side the range we want
            b = 0
            g = 255
            r = int(r)
            g = int(g)
            b = int(b)
        print(r, g, b)  # prints the color variables to show us the color in code
        time.sleep(0.05)

    except RuntimeError:  # gives us simple error message if it doesn't work 
        print("Retrying!")
        r = 0
        g = 0
        b = 255
        time.sleep(0.1)

    print(r, g, b)  
    dot.fill((r, g, b)) # tells the dot variable what to do
    time.sleep(0.05) # delay so code don't break
```

### Evidence

here is a video.


https://user-images.githubusercontent.com/71406784/191340307-837a51d7-b6ea-4963-bc91-7a316856a9d1.mp4


### Wiring
 This is the wiring diagram:
 ![Screenshot 2022-09-19 151305](https://user-images.githubusercontent.com/71406784/191097368-cd9934de-e873-4235-b3da-187033846d88.png)
 
### Reflection

This project took focus and time to complete and the consistant problem of getting the correct file to the right place in my computer. the code for this is long but not overly complex. I would in the future write my code better and study the concepts of loops and color theor a bit more. 




## NextAssignment

### Description & Code

```python
Code goes here

```

### Evidence

### Wiring

### Reflection
