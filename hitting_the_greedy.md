# Algoritmos greedy

Un algoritmo greedy construye una solución para el problema tomando siempre una decisión que parece la mejor en el momento. Un algoritmo greedy nunca revoca sus decisiones, sino que construye directamente la solución final. Por esta razón, los algoritmos greedy suelen ser muy eficientes.

La dificultad de diseñar algoritmos greedy radica en encontrar una estrategia greedy que siempre produzca una solución óptima para el problema. Las decisiones localmente óptimas en un algoritmo greedy también deben ser globalmente óptimas. A menudo es difícil argumentar que un algoritmo greedy funcione.

# Problema de las monedas

Como primer ejemplo, consideramos un problema donde se nos da un conjunto de monedas y nuestra tarea es formar una suma de dinero *n* usando las monedas. Los valores de las monedas son:

```plaintext
monedas = {c1, c2,..., ck}
```

Y cada moneda puede ser usada tantas veces como queramos. ¿Cuál es el número mínimo de monedas necesario?

Por ejemplo, si las monedas son:

```plaintext
{1, 2, 5, 10, 20, 50, 100, 200}
```

Y n = 520, necesitamos al menos cuatro monedas. La solución óptima es seleccionar monedas:

```plaintext
200 + 200 + 100 + 20
```

cuyo total es ```520```

## Algoritmo greedy

Un simple algoritmo greedy para resolver este problema consiste en seleccionar siempre la moneda más grande posible hasta que se haya construido la suma de dinero requerida.

## Caso general

En el caso general, el conjunto de monedas puede contener cualquier tipo de monedas y el algoritmo codicioso no necesariamente produce una solución óptima.

Podemos demostrar que un algoritmo codicioso no funciona mostrando un contraejemplo donde el algoritmo da una respuesta incorrecta. En este problema, podemos encontrar fácilmente un contraejemplo: si las monedas son:

```plaintext
{1, 3, 4}
```

y la suma objetivo es ```6```, el algoritmo codicioso produce la solución
```plaintext
4 + 1 + 1
```

mientras que la solución óptima es

```plaintext
3 + 3
```

No se sabe si el problema general de monedas puede resolverse usando algún algoritmo greedy.


# Programación de Eventos

Muchos problemas de programación de eventos pueden resolverse utilizando algoritmos greedy. Un problema clásico es el siguiente: Dado *n* eventos con sus tiempos de inicio y fin, encuentra un programa que incluya tantos eventos como sea posible. No es posible seleccionar un evento parcialmente.

## Ejemplo de eventos

Considere los siguientes eventos:

| Evento | Hora de inicio | Hora de finalización |
| --- | --- | --- |
| A | 1 | 3 |
| B | 2 | 5 |
| C | 3 | 9 |
| D | 6 | 8 |

En este caso, el número máximo de eventos que se pueden incluir es dos. Por ejemplo, podemos seleccionar los eventos **B** y **D** de la siguiente manera:

- **Evento B**: Desde la hora 2 hasta la hora 5.
- **Evento D**: Desde la hora 6 hasta la hora 8.

Esta combinación permite programar el máximo número de eventos sin que se superpongan.

![image](https://github.com/danielzazzali/ProgCompUCN/assets/80864796/30e7616b-a232-4b07-8113-3207495ac663)

Es posible inventar varios algoritmos greedy para resolver el problema, pero ¿cuál de ellos funciona en todos los casos?

## Algoritmo 1

La primera idea es seleccionar eventos lo más cortos posibles. En el caso de ejemplo, este algoritmo selecciona los siguientes eventos:

![image](https://github.com/danielzazzali/ProgCompUCN/assets/80864796/6810c447-856e-4c21-97c0-946a12d98afc)

Sin embargo, seleccionar eventos cortos no siempre es una estrategia correcta. Por ejemplo, el algoritmo falla en el siguiente caso:

![image](https://github.com/danielzazzali/ProgCompUCN/assets/80864796/907c4640-c788-4f40-82ee-983078d2ad37)

Si seleccionamos el evento corto, solo podemos seleccionar un evento. Sin embargo, sería posible seleccionar ambos eventos largos.

## Algoritmo 2

Otra idea es seleccionar siempre el siguiente evento posible que comience lo más temprano posible. Este algoritmo selecciona los siguientes eventos:

![image](https://github.com/danielzazzali/ProgCompUCN/assets/80864796/ea28f6ed-006d-44fa-9e19-81e8f14b698c)

Sin embargo, también podemos encontrar un contraejemplo para este algoritmo. Por ejemplo, en el siguiente caso, el algoritmo solo selecciona un evento:

![image](https://github.com/danielzazzali/ProgCompUCN/assets/80864796/4cd9ecbb-558d-4618-9cd6-5504e72cf964)

Si seleccionamos el primer evento, no es posible seleccionar otros eventos. Sin embargo, sería posible seleccionar los otros dos eventos.

## Algoritmo 3

La tercera idea es seleccionar siempre el siguiente evento posible que termine lo antes posible. Este algoritmo selecciona los siguientes eventos:

![image](https://github.com/danielzazzali/ProgCompUCN/assets/80864796/8ce5d2df-cab7-4a0b-aa7b-9a15dddd81cf)

Resulta que este algoritmo siempre produce una solución óptima. La razón de esto es que siempre es una elección óptima seleccionar primero un evento que termine lo antes posible. Después de esto, es una elección óptima seleccionar el siguiente evento usando la misma estrategia, y así sucesivamente, hasta que no podamos seleccionar más eventos.

# Tareas y plazos

Consideremos ahora un problema en el que se nos dan n tareas con duraciones y plazos, y nuestra tarea es elegir un orden para realizar las tareas. Por cada tarea, ganamos d - x puntos, donde d es el plazo de la tarea y x es el momento en que terminamos la tarea. ¿Cuál es el puntaje total más alto que podemos obtener?

Por ejemplo, supongamos que las tareas son las siguientes:

| Tarea | Duración | Plazo |
| --- | --- | --- |
| A | 4 | 2 |
| B | 3 | 5 |
| C | 2 | 7 |
| D | 4 | 5 |

En este caso, un programa óptimo para las tareas es el siguiente:

![image](https://github.com/danielzazzali/ProgCompUCN/assets/80864796/d5e76f31-f064-4313-82fa-9ef995c23555)


En esta solución, C otorga 5 puntos, B otorga 0 puntos, A otorga -7 puntos y D otorga -8 puntos, por lo que el puntaje total es -10.

Sorprendentemente, la solución óptima para el problema no depende en absoluto de los plazos, pero una estrategia greedy correcta es simplemente realizar las tareas ordenadas por sus duraciones en orden creciente.

La razón de esto es que si alguna vez realizamos dos tareas una tras otra de tal manera que la primera tarea tome más tiempo que la segunda tarea, podemos obtener una mejor solución si intercambiamos las tareas. Por ejemplo, considera el siguiente programa:

![image](https://github.com/danielzazzali/ProgCompUCN/assets/80864796/7604efa7-7375-4ae2-adc4-c550225ac89d)

Aquí a > b, por lo que deberíamos intercambiar las tareas:

![image](https://github.com/danielzazzali/ProgCompUCN/assets/80864796/e66205ec-683a-4da7-a47c-3f66ee29c6fe)

Ahora X da ```b``` menos puntos y Y da ```a``` más puntos, por lo que el puntaje total aumenta
en ```a−b > 0```. En una solución óptima, para cualquier par de tareas consecutivas, debe cumplirse
que la tarea más corta viene antes que la tarea más larga. Por lo tanto, las tareas deben
realizarse ordenadas por sus duraciones.





Traducido desde Competitive Programmer’s Handbook - Antti Laaksonen
