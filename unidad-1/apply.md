# Unidad 1

## 🛠 Fase: Apply

### actividad 5
se creó un sistema operativo donde se mantiene presionado el boton A del microbit para cambiar el color de un cuadrado en el editor de p5.js de verde a rojo

el microbit manda información cuando el boton de A se mantiene presionado, lo que hace que el codigo en p5 pueda cambiar el color. pero si no se presiona envia "N" y en el codigo de P5 mantiene su color original

### Actividad 6
https://editor.p5js.org/adquintero2244/sketches/RWEIIwyd-

```javascript
let port;
let connectBtn;
let connectionInitialized = false;

let x; // posición en X 

function setup() {
  createCanvas(400, 400);
  background(220);
  
  x = width / 2; 
  
  port = createSerial();
  connectBtn = createButton("Connect to micro:bit");
  connectBtn.position(80, 350);
  connectBtn.mousePressed(connectBtnClick);
}

function draw() {
  background(220);

  if (port.opened() && !connectionInitialized) {
    port.clear();
    connectionInitialized = true;
  }

  if (port.availableBytes() > 0) {
    let dataRx = port.read(1); 
    if (dataRx == "L") {
      x -= 10; // izquierda
    } else if (dataRx == "R") {
      x += 10; // derecha
    }
  }

  // Dibuja el círculo
  fill("rgb(185,33,181)");
  ellipse(x, height / 2, 50, 50);

  
  if (!port.opened()) {
    connectBtn.html("Connect to micro:bit");
  } else {
    connectBtn.html("Disconnect");
  }
}

function connectBtnClick() {
  if (!port.opened()) {
    port.open("MicroPython", 115200);
    connectionInitialized = false;
  } else {
    port.close();
  }
}

```

```python
from microbit import *
import utime

uart.init(baudrate=115200)

while True:
    if button_a.is_pressed():
        uart.write('L')  
        utime.sleep(0.5) 
    elif button_b.is_pressed():
        uart.write('R') 
        utime.sleep(0.5)
```
