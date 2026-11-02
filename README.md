# Busqueda_tesoro_Arduino
Proyecto 3 de HWD para Arduino UNO de la clase de Hardware digital
Esta tarea se basa en un juego de busqueda de tesoro entre dos placas de arduino UNO, una sirviendo como el "esclavo"
y la otra como el "maestro" en donde un tesoro de 2×2 celdas se ubica aleatoriamente en una grilla
virtual de 100×100 celdas (coordenadas 0 a 100 en cada eje).

Rol de el Esclavo: El jugador gira dos potenciómetros (eje X y eje Y) y el Esclavo envía las coordenadas al
Maestro.

Rol de el Maestro: El maestro sortea y conoce la ubicación del tesoro la convierte en un valor discreto (FRÍO, TIBIO, CALIENTE, AQUÍ) y lo devuelve al Esclavo, que lo muestra en dos LEDs, uno por eje. el maestro tambien tiempo de la partida mediante un LED.

Como se gana?: el jugador debe posicionar ambos ejes sobre el tesoro y mantenerse allí antes de que expire el tiempo. 

INFORMACION HARDWARE:
Esclavo (Joystick) 2 potenciómetros,
pulsador de inicio (INPUT_PULLUP);
2 leds (LED X y LED Y).
Resistencias limitadoras de corriente

Maestro (Juego) LED para mostrar el tiempo (PWM)
Resistencias
Opcional: LCD 16×2 con módulo I2C (A4/A5).

INFORMACION DE JUEGO:
LED Verde (Temporizador, en el Maestro): inicia en 100% al comenzar la partida y se atenúa progresivamente con PWM
según el tiempo restante, apagándose totalmente al llegar a 0.

Máquina de Estados del Maestro (4 modos):
• INACTIVO: LED verde apagado. El Maestro envía el código 'I' y el Esclavo mantiene sus LEDs apagados. Espera una
solicitud de inicio válida.

• JUGANDO: recepción de coordenadas, cálculo del nivel de cada eje, envío del código de niveles, atenuación del
LED verde y verificación de la condición de victoria.

• VICTORIA: dx = dy = 0 durante 1000 ms. El Maestro envía 'V': los LEDs X e Y del Esclavo parpadean 10 veces (250
ms encendido / 250 ms apagado) y el LED verde queda fijo al 100%. Al terminar, vuelve a INACTIVO.

• DERROTA: el tiempo expira. El Maestro envía 'D': los LEDs del Esclavo se apagan y el LED verde parpadea 10 veces
(250 ms / 250 ms). Al terminar, vuelve a INACTIVO.

Se recomienda usar enum y switch-case.

Esclavo: no requiere máquina de estados de juego; refleja en sus LEDs el último código válido recibido. Pérdida de enlace:
el Esclavo hace parpadear los LEDs X e Y de forma alternada (500 ms); el Maestro aborta la partida, regresa a INACTIVO y
hace parpadear rápidamente el LED verde (250 ms) hasta recuperar el enlace.

