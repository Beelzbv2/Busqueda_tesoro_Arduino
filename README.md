# Busqueda_tesoro_Arduino
Proyecto 3 de HWD para Arduino UNO de la clase de Hardware digital
Esta tarea se basa en un juego de busqueda de tesoro entre dos placas de arduino UNO, una sirviendo como el "esclavo"
y la otra como el "maestro" en donde un tesoro de 2×2 celdas se ubica aleatoriamente en una grilla
virtual de 100×100 celdas (coordenadas 0 a 100 en cada eje).

Rol de el Esclavo: El jugador gira dos potenciómetros (eje X y eje Y) y el Esclavo envía las coordenadas al
Maestro.

Rol de el Maestro: El maestro sortea y conoce la ubicación del tesoro la convierte en un valor discreto (FRÍO, TIBIO, CALIENTE, AQUÍ) y lo devuelve al Esclavo, que lo muestra en dos LEDs, uno por eje. el maestro tambien tiempo de la partida mediante un LED.

Como se gana?: el jugador debe posicionar ambos ejes sobre el tesoro y mantenerse allí antes de que expire el tiempo. 

INFORMACION:
Esclavo (Joystick) 2 potenciómetros,
pulsador de inicio (INPUT_PULLUP);
2 leds (LED X y LED Y).
Resistencias limitadoras de corriente

Maestro (Juego) LED para mostrar el tiempo (PWM)
Resistencias
Opcional: LCD 16×2 con módulo I2C (A4/A5).



