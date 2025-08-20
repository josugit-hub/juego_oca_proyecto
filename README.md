# juego_oca_proyecto
# Codigo desarrollado en Python para simular el Juego de la Oca como proyecto final del curso SOFT-01 Principios de Programacion 1


import sys
import random
import time

meta = 63 #Casilla o posicion meta para ganar el juego.
jugadores = [] #Esta lista vacía guarda los jugadores que se registren en el juego.
cant_jugadores = 0 #Contador de jugadores registrados.
casillas_oca = (5, 9, 14, 18, 23, 27, 32, 36, 41, 45, 50, 54, 59) #Tupla que contiene la cantidad limitada de casillas oca.
casillas_espe_turnos = {"posada": 19, "pozo": 31, "carcel": 52} #Diccionario de casillas especiales que hacen perder turnos.
casillas_especiales = {"puente": 6, "laberinto": 42, "muerte": 58} #Diccionario de casillas especiales que hacen avanzar o perder posiciones.

# Nombre: lanzar_dados
# Responsabilidad: Simular el lanzamiento aleatorio de los dos dados retornando el resultado.
#Parámetros: No recibe parámetros
#Retorno: Sí tiene retorno
# Desarrollado por: Josue Arroyo, Kristel Badilla, Luis Vargas

def lanzar_dados():
    dado1 = random.randint(1, 6)# Genera un número aleatorio entre 1 y 6
    dado2 = random.randint(1, 6)# Genera un número aleatorio entre 1 y 6
    resultado = dado1 + dado2# Suma los valores de ambos dados
    print(f"Dado 1: {dado1}, Dado 2: {dado2}, Total: {resultado}")#Imprime los resultados
    return resultado

# Nombre: posiciones_oca
# Responsabilidad: Aplicar los efectos de las casillas oca: avanzar a la siguiente oca y volver a lanzar los dados.
#Parámetro: 
# Desarrollado por: Josue Arroyo, Kristel Badilla, Luis Vargas

def posiciones_oca(posicion):
    print(f"¡Estás en una oca! Avanzas a la próxima oca.")
    for oca in casillas_oca:
        if oca > posicion:
            nueva_posicion = oca
            print(f"Avanzas de {posicion} a {nueva_posicion}")
            posicion = nueva_posicion
            posicion += lanzar_dados() #Se llama a la funcion para simular el lanzamiento de dados.
            break
    return posicion

# Nombre: posiciones_especiales
# Responsabilidad: Aplicar los efectos de las casillas especiales (puente, laberinto y muerte), respectivamente.
# Desarrollado por: Josue Arroyo, Kristel Badilla, Luis Vargas

def posiciones_especiales(posicion):
    if posicion == casillas_especiales["puente"]:
        print("¡Estás en el puente! Avanzas 6 casillas.")
        posicion += 6
        posicion += lanzar_dados() #Se llama a la funcion para simular el lanzamiento de dados.
    elif posicion == casillas_especiales["laberinto"]:
        print("¡Estás en el laberinto! Retrocedes a la casilla 30.")
        posicion = 30
    elif posicion == casillas_especiales["muerte"]:
        print("¡Has caído en la muerte! Vuelves al inicio.")
        posicion = 0
    return posicion

# Nombre: posiciones_especiales
# Responsabilidad: Aplicar los efectos de las casillas especiales (posada, pozo y carcel), las cuales, hacen perder turnos.
# Desarrollado por: Josue Arroyo, Kristel Badilla, Luis Vargas

def posiciones_espe_turnos(posicion):
    if posicion == casillas_espe_turnos["posada"]:
        print("¡Estás en la posada! Pierdes 1 turno.")
    elif posicion == casillas_espe_turnos["pozo"]:
        print("¡Estás en el pozo! Pierdes 2 turnos.")
    elif posicion == casillas_espe_turnos["carcel"]:
        print("¡Estás en la cárcel! Pierdes 3 turnos.")
    return posicion

# Nombre: casilla_excedente
# Responsabilidad: Aplicar la regla de que si un jugador excede la meta debe devolverse la cantidad de casillas excedidas.
# Desarrollado por: Josue Arroyo, Kristel Badilla, Luis Vargas

def casilla_excedente(posicion, meta):
    excedente = posicion - meta
    posicion = meta - excedente
    return posicion

# Nombre: imprimir_tablero
# Responsabilidad: Imprimir tablero dinamico, en forma de espiral (8x8) y simbolos visuales claros.
# Desarrollado por: Josue Arroyo, Kristel Badilla, Luis Vargas

def imprimir_tablero(posiciones):
    # Lista fija con las 64 casillas del tablero (zigzag en reversa)
    tablero = [
        [63, 62, 61, 60, 59, 58, 57, 56],
        [48, 49, 50, 51, 52, 53, 54, 55],
        [47, 46, 45, 44, 43, 42, 41, 40],
        [32, 33, 34, 35, 36, 37, 38, 39],
        [31, 30, 29, 28, 27, 26, 25, 24],
        [16, 17, 18, 19, 20, 21, 22, 23],
        [15, 14, 13, 12, 11, 10, 9, 8],
        [0, 1, 2, 3, 4, 5, 6, 7,]
    ]

    # Crear símbolos para las 64 casillas
    simbolos = [""] * 64

    simbolos[0] = "Inicio"
    simbolos[1] = "01"
    simbolos[2] = "02"
    simbolos[3] = "03"
    simbolos[4] = "04"
    simbolos[5] = "05"
    simbolos[6] = "06"
    simbolos[7] = "07"
    simbolos[8] = "08"
    simbolos[9] = "09"
    simbolos[10] = "10"
    simbolos[11] = "11"
    simbolos[12] = "12"
    simbolos[13] = "13"
    simbolos[14] = "14"
    simbolos[15] = "15"
    simbolos[16] = "16"
    simbolos[17] = "17"
    simbolos[18] = "18"
    simbolos[19] = "19"
    simbolos[20] = "20"
    simbolos[21] = "21"
    simbolos[22] = "22"
    simbolos[23] = "23"
    simbolos[24] = "24"
    simbolos[25] = "25"
    simbolos[26] = "26"
    simbolos[27] = "27"
    simbolos[28] = "28"
    simbolos[29] = "29"
    simbolos[30] = "30"
    simbolos[31] = "31"
    simbolos[32] = "32"
    simbolos[33] = "33"
    simbolos[34] = "34"
    simbolos[35] = "35"
    simbolos[36] = "36"
    simbolos[37] = "37"
    simbolos[38] = "38"
    simbolos[39] = "39"
    simbolos[40] = "40"
    simbolos[41] = "41"
    simbolos[42] = "42"
    simbolos[43] = "43"
    simbolos[44] = "44"
    simbolos[45] = "45"
    simbolos[46] = "46"
    simbolos[47] = "47"
    simbolos[48] = "48"
    simbolos[49] = "49"
    simbolos[50] = "50"
    simbolos[51] = "51"
    simbolos[52] = "52"
    simbolos[53] = "53"
    simbolos[54] = "54"
    simbolos[55] = "55"
    simbolos[56] = "56"
    simbolos[57] = "57"
    simbolos[58] = "58"
    simbolos[59] = "59"
    simbolos[60] = "60"
    simbolos[61] = "61"
    simbolos[62] = "62"
    simbolos[63] = "63"

    # Agregar símbolos especiales
    if 5 in casillas_oca:
        simbolos[5] += "🦆"
    if 12 in casillas_oca:
        simbolos[12] += "🦆"
    if casillas_especiales.get("muerte") == 58:
        simbolos[58] += "💀"
    if casillas_especiales.get("laberinto") == 42:
        simbolos[42] += "🔀"
    if casillas_especiales.get("puente") == 6:
        simbolos[6] += "🌉"
    if 10 in casillas_espe_turnos.values():
        simbolos[10] += "🔁"

    # Jugadores por casilla (manual)
    jugadores_por_casilla = [""] * 64
    if posiciones[0] >= 0 and posiciones[0] < 64:
        jugadores_por_casilla[posiciones[0]] = "P1"
    if posiciones[1] >= 0 and posiciones[1] < 64:
        if jugadores_por_casilla[posiciones[1]] != "":
            jugadores_por_casilla[posiciones[1]] += ",P2"
        else:
            jugadores_por_casilla[posiciones[1]] = "P2"

    # Imprimir tablero
    print("\n TABLERO")
    print("+-------+-------+-------+-------+-------+-------+-------+-------+")

    fila = 0
    while fila < 8:
        linea_simbolos = "|"
        linea_jugadores = "|"
        col = 0
        while col < 8:
            num_casilla = tablero[fila][col]
            simbolo = simbolos[num_casilla].center(5)
            jugadores = jugadores_por_casilla[num_casilla].center(5)
            linea_simbolos += f" {simbolo}|"
            linea_jugadores += f" {jugadores}|"
            col += 1
        print(linea_simbolos)
        print(linea_jugadores)
        print("+-------+-------+-------+-------+-------+-------+-------+-------+")
        fila += 1

# Nombre: mostrar_posiciones_jugadores
# Responsabilidad: Imprimir las posiciones de los jugadores conforme el juego avanza.
# Desarrollado por: Josue Arroyo, Kristel Badilla, Luis Vargas

def mostrar_posiciones_jugadores(posiciones):
    print("\n Posiciones de los jugadores")
    for idx, pos in enumerate(posiciones):
        nombre = jugadores[idx]
        print(f"Jugador {idx + 1} - {nombre}: casilla {pos}")
    print("-" * 40)

# Nombre: turnos
# Responsabilidad: Correr el juego implementando turnos secuenciales automaticos a cada jugador y aplicando cada una de las reglas mientras imprime el tablero dinamico.
# Desarrollado por: Josue Arroyo, Kristel Badilla, Luis Vargas

def turnos():
    posiciones = [0] * cant_jugadores
    while True:
        imprimir_tablero(posiciones) #Se llama a la funcion para imprimir el tablero cuando los jugadores completen sus turnos.
        mostrar_posiciones_jugadores(posiciones) #Se llama a la funcion para mostrar las posiciones de los jugadores.
        for i, jugador in enumerate(jugadores):
            input(f"\nTurno de {jugador}. Presiona Enter para lanzar dados.")
            posiciones[i] += lanzar_dados() #Se llama a la funcion para simular el lanzamiento de dados.
            pos = posiciones[i]

            if pos in casillas_oca:
                pos = posiciones_oca(pos) #Se llama a la funcion para aplicar el efecto de casilas oca.
            elif pos in casillas_especiales.values():
                pos = posiciones_especiales(pos) #Se llama a la funcion para aplicar los efectos de las casillas especiales que hacen avanzar/perder posiciones.
            elif pos in casillas_espe_turnos.values():
                pos = posiciones_espe_turnos(pos) #Se llama a la funcion para aplicar los efectos de las casillas especiales que hacen perder turnos.

            if pos == meta:
                print(f"\n🎉 ¡{jugador} ha ganado el juego en la casilla {pos}! 🎉")
                imprimir_tablero(posiciones)
                mostrar_posiciones_jugadores(posiciones)
                return
            elif pos > meta:
                print("Te has excedido. Retrocedes según la diferencia.")
                pos = casilla_excedente(pos, meta) #Se llama a la funcion para aplicar la regla de casillas excedentes.

            posiciones[i] = pos
            print(f"{jugador} está ahora en la casilla {pos}")
            time.sleep(1)

# Nombre: config_juego
# Responsabilidad: Configurar la cantidad de jugadores y registrarlos con sus nombres.
# Desarrollado por: Josue Arroyo, Kristel Badilla, Luis Vargas

def config_juego():
    global jugadores, cant_jugadores, cont_jugadores
    print("1. Registrar jugadores (min 2): ")
    print("2. Jugar")
    print("3. Volver al menu principal")
    while True:
        opcion = int(input("Indique la opcion que desea escoger: "))
        match opcion:
            case 1:
                cant_jugadores = int(input("Ingrese la cantidad de jugadores (min 2): "))
                if cant_jugadores < 2:
                    print("No hay el minimo de jugadores requeridos para jugar.")
                else:
                    cont_jugadores = 0
                    while cont_jugadores < cant_jugadores:
                        nombre_jugador = input("Ingrese el nombre del jugador: ")
                        jugadores.append(nombre_jugador) #El metodo append agrega los nombres de los jugadores a la lista vacia de jugadores.
                        cont_jugadores += 1
            case 2:
                print("Todo listo! Vamos a jugar...")
                turnos() #Se llama a la función turnos para inicializar el juego posterior a la configuracion del registro de jugadores.
            case 3:
                print("Volviendo al menu principal...")
                iniciar_juego() #Se llama a la funcion principal para volver al menu principal.
            case _:
                print("Opcion invalida! Por favor, seleccione una opcion valida")

# Nombre: iniciar_juego (main)
# Responsabilidad: Imprimir el menu principal e inicializar el juego. Es la funcion principal.
# Desarrollado por: Josue Arroyo, Kristel Badilla, Luis Vargas

def iniciar_juego():
  print("1. Lanzar dados")
  print("2. Ver posicion de los jugadores")
  print("3. Imprimir tablero")
  print("4. Salir del juego")
  while True:
    opcion = int(input("Digite la opcion que desea escoger(1-4): "))
    match opcion:
      case 1:
        print("Listo? Vamos a jugar!")
        config_juego() #Se llama a la funcion config_juego para comenzar con el registro de los jugadores.
      case 2:
        print("Veamos donde se encuentran los jugadores")
        mostrar_posiciones_jugadores() #Se llama a la funcion mostrar posiciones para ver la posicion de los jugadores.
      case 3:
        print("Imprimiendo tablero...")
        imprimir_tablero() #Se llama a la funcion para imprimir el tablero.
      case 4:
        print("Saliendo del juego...")
        sys.exit() #Esta funcion permite cerrar el ciclo de bandera de la funcion principal.
      case _:
        print("Opcion invalida, digita una opcion valida")

iniciar_juego() #Se llama a la funcion principal (main) para ejecutar el codigo.
