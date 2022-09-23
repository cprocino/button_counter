# CPyProjectTemplate
This was a bit more complex than the last few projects. we needed to make a LCD print a counter that would go up or down depedent on buttons 
This was not too hard of a project because i had done it last year of a previous project 
Huge thanks to Anton for help with this code:
    import board
    from lcd.lcd import LCD
    from lcd.i2c_pcf8574_interface import I2CPCF8574Interface
    from digitalio import DigitalInOut, Direction, Pull # set up code

    i2c = board.I2C()       # button set up 
    btn = DigitalInOut(board.D3) 
    btn.direction = Direction.INPUT
    btn.pull = Pull.UP

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
