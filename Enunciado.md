# Ejercicio de Postulación - Área de Interrogaciones

Nombre: **Francisco Cornejo**

Email: **fcornejoq@estudiante.uc.cl**

Telegram: **@VerditoRaccoon**

## Código solución (NO MODIFICAR)

```python
#code.py
def obtener_proximos(partidos, equipo):
    equipos = []
    ex_rivales = []
    for partido in partidos:
        if partido[0] not in equipos:
            equipos.append(partido[0])
        if partido[1] not in equipos:
            equipos.append(partido[1])
        if equipo == partido[0]:
            ex_rivales.append(partido[1])
        if equipo == partido[1]:
            ex_rivales.append(partido[0])
    pendientes = []
    for rival in equipos:
        if rival not in ex_rivales:
            pendientes.append(rival)
    return pendientes
```

## Runner Personalizado (Opcional Modificar)

```python
from functools import partial

def obtener_proximos_modificada(func_original, partidos, equipo):
    try:
        resultado = func_original(partidos, equipo)
        if equipo in resultado:
            resultado.remove(equipo)
        resultado.sort()
        print(resultado)
    except TypeError:
        print("Tipo de variable retornado incorrecto.")
        pass

# Con esto reescribimos la función original para capturar el capturar resultado del alumno y modificarlo si es necesario
try:
    obtener_proximos = partial(obtener_proximos_modificada, obtener_proximos)
    obtener_proximos(partidos, equipo)
except NameError:
    print("Función 'obtener_proximos' no definida")
```

## Enunciado

# DCCampeonato

El tan esperado DCCampeonato de Fútbol está por comenzar y, con todos los equipos ya preparados, aún faltan demasiadas fechas por organizar. Por ello, los representantes de cada equipo buscarán tu ayuda para que, a través de tus conocimientos de **programación** y de **funciones**, logres identificar qué equipos faltarían por enfrentarse.

## Objetivo

Para esto tendrás que definir la función ```obtener_proximos```, la cual recibirá una *lista de listas* con los partidos que ya están registrados y programados en el campeonato, y un *string* del nombre del equipo a analizar. 

Tu objetivo será ver qué partidos del equipo dado faltan por programar, considerando que debe enfrentarse a cada uno de los distintos equipos que se encuentren en la lista de partidos. La función debe retornar una *lista* con los nombres de los equipos con los que **aún no juega**.

No te preocupes por el *input* ya que este será manejado por nosotros. Sólo debes realizar la función descrita.

## Ejemplo

### Input
```python
partidos = [
    ["Equipo1", "Equipo2"], 
    ["Equipo3", "Equipo4"],
    ["Equipo4", "Equipo1"],
    ["Equipo2", "Equipo3"]]
equipo = "Equipo3"
```
### Output
```python
['Equipo1']
```
### Explicación

La función recibe una *lista de listas* con los partidos ya programados entre los equipos, junto a un *string* señalando que el equipo a analizar será el 'Equipo3'. Tras pasar por la función, el único equipo con el cual le faltaría hacer un partido sería con el 'Equipo1', siendo el contenido de la *lista* retornada.

## Testcases
### Testcase 1
#### Input
```python
partidos = [
    ["Union Espanola", "Palestino"], 
    ["Universidad de Chile", "Colo Colo"],
    ["Universidad Catolica", "Union Espanola"],
    ["Palestino", "Colo Colo"],
    ["Colo Colo", "Universidad Catolica"]]
equipo = "Universidad de Chile"
```
#### Output
```python
['Palestino', 'Union Espanola', 'Universidad Catolica']
```

### Testcase 2
#### Input
```python
partidos = [
    ["Chile", "Argentina"], 
    ["Bolivia", "Mexico"],
    ["Argentina", "Mexico"],
    ["Chile", "Bolivia"],
    ["Mexico", "Chile"]]
equipo = "Mexico"
```
#### Output

```python
[]
```

### Testcase 3
#### Input
```python
partidos = [
    ["Real Madrid", "FC Barcelona"], 
    ["Liverpool", "Real Madrid"],
    ["FC Barcelona", "Manchester United"],
    ["FC Barcelona", "Liverpool"],
    ["Manchester United", "Liverpool"],
    ["Liverpool", "Juventus"],
    ["Juventus", "FC Barcelona"],
    ["Manchester United", "Juventus"]]
equipo = "Real Madrid"
```
#### Output
```python
['Juventus', 'Manchester United']
```