**Juego de la Oca - Entrega Final**

**Instrucciones para ejecutar el codigo**

- Tener instalado Visual Studio Code (VSC).
- Abrir el archivo del codigo en VSC.
- Correr el codigo en VSC para jugar el Juego de la Oca.

**Funciones del codigo**

- lanzar_dados()
Descripcion: Simular el lanzamiento aleatorio de los dos dados retornando el resultado.

- posiciones_oca()
Descripcion: Aplicar los efectos de las casillas oca: avanzar a la siguiente oca y volver a lanzar los dados.

- posiciones_especiales()
Descripcion: Aplicar los efectos de las casillas especiales (puente, laberinto y muerte), respectivamente.

- posiciones_espe_turnos()
Descripcion: Aplicar los efectos de las casillas especiales (posada, pozo y carcel), las cuales, hacen perder turnos.

- casilla_excedente()
Descripcion: Aplicar la regla de que si un jugador excede la meta debe devolverse la cantidad de casillas excedidas.

- imprimir_tablero()
Descripcion: Imprimir tablero dinamico, en forma de espiral (8x8) y simbolos visuales claros.

- mostrar_posiciones_jugadores()
Descripcion: Imprimir las posiciones de los jugadores conforme el juego avanza.

- turnos()
Descripcion: Correr el juego implementando turnos secuenciales automaticos a cada jugador y aplicando cada una de las reglas mientras imprime el tablero dinamico.

- config_juego()
Descripcion: Configurar la cantidad de jugadores y registrarlos con sus nombres.

- iniciar_juego()
Descripcion: Imprimir el menu principal e inicializar el juego. Es la funcion principal.

**Estructura del programa**

El programa se compone de 10 rutinas que permiten configurar la cantidad de los jugadores que pueden jugar el juego de la oca, simular el lanzamiento aleatorio de los dados, asignar turnos automaticos y secuenciales para cada jugador, y avanzar en el tablero de 63 casillas aplicando las reglas del juego de la oca relacionadas con las casillas especiales (ocas, puente, laberinto, muerte, pozada, poso y carcel). Asimismo, el codigo permite que gane el jugador que cae exactamente en la casilla meta (63). 

