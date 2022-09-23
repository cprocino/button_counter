# CPyProjectTemplate
This was a bit more complex than the last few projects. we needed to make a LCD print a counter that would go up or down depedent on buttons 
this project was very simple as it wwas the first project of the year so all we needed was the arduino and the computer
here is the code i used:
import board
from lcd.lcd import LCD
from lcd.i2c_pcf8574_interface import I2CPCF8574Interface
from digitalio import DigitalInOut, Direction, Pull # set up code

# get and i2c object
i2c = board.I2C()       # button set up 
btn = DigitalInOut(board.D3) 
btn.direction = Direction.INPUT
btn.pull = Pull.UP
# some LCDs are 0x3f... some are 0x27.
lcd = LCD(I2CPCF8574Interface(i2c, 0x27), num_rows=2, num_cols=16) # lCD set up 
cur_state = True  # setting up boolean 
prev_state = True
buttonPress = 0

while True: # basic while loop
    cur_state = btn.value  # setting button to current state
    if cur_state != prev_state:  # if statment for button press
        if not cur_state:      # if not current position 
            buttonPress = buttonPress + 1  # counts 
           lcd.clear()                     # clears laps message
            lcd.set_cursor_pos(0, 0)  # cursor position
            lcd.set_cursor_pos(1, 0)
            lcd.print("BTN Press:")  # displays btn press on lcd
            lcd.print(str(buttonPress))
        else:
            lcd.clear()  # clears lcd 

    prev_state = cur_state  # closes while loop

I didnt have any real problems this project, just had to set up all the accounts and downloads.
