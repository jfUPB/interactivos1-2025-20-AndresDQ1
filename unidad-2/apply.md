# Unidad 2


## 🛠 Fase: Apply
### actividad 4

### actividad 5

```python
from microbit import *
import utime

STATE_CONFIG = 0
STATE_ARMED = 1
STATE_BOOM = 2

MIN = 1
MAX = 6

time_left = 2
time=utime.ticks_ms()
state = STATE_CONFIG

    
while True:
    #estado config
    if state==STATE_CONFIG:
        display.show(time_left)
        if button_a.was_pressed() and time_left<MAX:
            time_left += 1
        if button_b.was_pressed() and time_left>MIN:
            time_left -= 1
        if accelerometer.was_gesture('shake'):
            state = STATE_ARMED
            time = utime.ticks_ms()

        #estado armed     
    elif state== STATE_ARMED:
        if utime.ticks_diff(utime.ticks_ms(),time)>=1000:
            time_left -=1
            time = utime.ticks_ms()
            if time > 0:
                display.show(time_left)
            else:
                state= STATE_BOOM
               

        #estado boom
    elif state ==STATE_BOOM:
        display.show(Image.SAD)
        if pin_logo.is_touched():
            state==STATE_CONFIG
            time=2

```

