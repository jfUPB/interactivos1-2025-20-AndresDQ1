# Unidad 2

## 🔎 Fase: Set + Seek  

### Actividad 1
1. el codigo modifica 2 leds del microbit haciendo que se prendan y apaguen a intervalos de tiempos diferentes
2. estado init: donde se inicia el conteo yse enciende por primera vez el led y WaitTimeout: donde se espera el tiempo para que se vuelva a prender el led
3. el tiempo medido (utime.ticks_ms()) ya que no hay reacción externa de un usuario y el tiempo es lo unico que hace que cambie los estados
4. 1. prender los 2 leds en especifico con un brillo en especifico (9)  2.resetear el tiempo cuando se prende el bombillo

### Actividad 2

```python
from microbit import *
import utime

class Semaforo:
    def __init__(self):
        self.state = "Rojo"
        self.startTime = utime.ticks_ms()
        self.interval = 2000  

    def update(self):
        if utime.ticks_diff(utime.ticks_ms(), self.startTime) > self.interval:
            self.cambiar_estado()
            self.startTime = utime.ticks_ms()

    def cambiar_estado(self):
        if self.state == "Rojo":
            self.state = "Verde"
        elif self.state == "Verde":
            self.state = "Amarillo"
        elif self.state == "Amarillo":
            self.state = "Rojo"
        self.estados()

    def estados(self):
        display.clear()
        if self.state == "Rojo":
            display.set_pixel(2, 4, 9)
        elif self.state == "Amarillo":
            display.set_pixel(2, 2, 7)
        elif self.state == "Verde":
            display.set_pixel(2, 0, 5)
semaforo = Semaforo()

while True:
    semaforo.update()
```
2.los estados son cada uno de los colores, los eventos son los intervalos de tiempo de 2 segundos entre los cambios de colores y las acciones cambiar de estado al de otro color y encender el color del led correspondiente

### Actividad 3
1. para que en ningun momento el programa tenga un fin, siempre hay 2 salidas posibles para que cada estado llegue a otro estado, hacieno que el programa no tenga una indicación de parar
2. estados	STATE_HAPPY, STATE_SMILE, STATE_SAD, STATE_INIT
   eventos: pulsacion del boton y el paso del tiempo
   acciones: mostrar la imagen correspondiente, cambiar de estado y reiniciar el tiempo


