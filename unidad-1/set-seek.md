# Unidad 1

## 🔎 Fase: Set + Seek

### Actividad 1
Qué es un sistema interactivo?
son sistemas creados combinando elementos fisicos con digitales para crear una experiencia que reacciona según la interacción del usuario

¿Cómo podrías aplicar lo que has visto en tu perfil profesional?
creando experiencias interactivas en lugares de entretenimiento, como museos, parques , ferias, etc. o implementando esto para videojuegos con dispositivos externos al mando

### Actividad 2
¿Qué es el diseño/arte generativo?
hace referencia a una práctica artistica donde se utiliza un conjunto de reglas en un programa informatico y se pone en marcha automaticamente para generar una obra

Cómo podrías aplicar lo que has visto en tu perfil profesional?
creando experiencias interactivas donde con unas reglas se crea una reacción diferente según la interacción del usuario 

### Actividad 3
#### microbit
inputs: botones y el acelerómetro y puerto de comunicación

outputs:puerto de comunicación

#### pc
inputs: puerto usb. botón "send love"

outputs:datos enviados por el puerto usb, pantalla

proceso: parte del codigo que procesa inputs para enviar outputs

### Actividad 4
```
function setup() {
  createCanvas(400, 400);
}

function draw() {
  background(255);
  
}
function mouseMoved() {
  let r = random(255);
  let g = random(255);
  let b = random(255);

  let size = random(10, 75);

  //dibujo circulo
  fill(r, g, b);
  ellipse(random(width), mouseY,size,size);
}
```
