# Programación Dinámica

Técnica que combina la correctitud de búsqueda completa y la eficiencia de los algoritmos Greedy.

Hay dos usos principales para programación dinámica:
- Encontrar la solución óptima: Queremos encontrar una solución lo más grande posible o lo más pequeño posible.
- Contar el número de soluciones: Queremos calcular el número total de soluciones posibles.

# Problema de las monedas pt. 2

Nuestra tarea es formar una suma de dinero *n* usando las monedas. Los valores de las monedas son:

```plaintext
monedas = {c1, c2,..., ck}
```

Y cada moneda puede ser usada tantas veces como queramos. ¿Cuál es el número mínimo de monedas necesario paras formar *n*?

Usando Greedy, elegimos siempre la moneda más grande posible y, en general, Greedy no siempre produce la solución más óptima.
Usando programación dinámica se resuelve de manera óptima para todo posible conjunto de monedas.

El algoritmo de programación dinámica se basa en una función recursiva que pasa por todas las posibilidades de cómo formar la suma, como un algoritmo de fuerza bruta. Sin embargo, el algoritmo
es eficiente porque utiliza la "memorización" y calcula la respuesta a cada subproblema solo una vez.

## Formulación Recursiva

Tomemos por ejemplo,

```plaintext
{1, 3, 4}
```

"Solve(*x*)" es una función que retorna el número mínimo de monedas necesarias para sumar *x*

Por ejemplo, solve(10) = 3. La solucion óptima es 3+3+4.
La propiedad clave de "solve" es que sus valores pueden calculados recursivamente desde valores más pequeños.

En este caso,
```plaintext
solve(x) = min(solve(x-1) + 1,
              solve(x-3) + 1,
              solve(x-4) +1)
```
Siendo el caso base: solve(0) = 0

Con INF = 999999 (un número cercano a infinito), el algoritmo en código es el siguiente:
```cpp
int solve(int x) {
  if (x < 0) return INF;
  if (x == 0) return 0;
  int best = INF;
  for (auto c : coins) {
    best = min(best, solve(x-c)+1);
  }
  return best;
}
```
Aún así, esta función no es eficiente, puede haber un número exponencial de formas de construir la suma. Para solucionar esto usaremos "memorización" (memoization)

## Memorización
La idea de la programación dinámica es utilizar la memorización para calcular eficientemente
valores de una función recursiva. Esto significa que los valores de la función son
almacenados en un array después de calcularlos. Para cada parámetro, el valor de la función se calcula de forma recursiva solo una vez y después de esto, el valor puede
ser recuperado directamente del array.

Para este problema usaremos los arrays:
```cpp
bool ready[N];
int value[N];
```
ready[] indica si el valor fue calculado en solve(), de ser así, se almacena en value[]. Ahora la función puede ser implementada eficientemente.
```cpp
int solve(int x) {
  if (x < 0) return INF;
  if (x == 0) return 0;
  if (ready[x]) return value[x];
  int best = INF;
  for (auto c : coins) {
    best = min(best, solve(x-c)+1);
  }
  value[x] = best;
  ready[x] = true;
  return best;
}
```
La complejidad de este algoritmo es de O(*nk*), siendo *n* la suma buscada y *k* el número de monedas.

La mayoría de los programadores competitivos prefieren la siguiente implementación, porque
es más corta y tiene factores constantes más bajos.
```cpp
value[0] = 0;
for (int x = 1; x <= n; x++) {
  value[x] = INF;
  for (auto c : coins) {
    if (x-c >= 0) {
    value[x] = min(value[x], value[x-c]+1);
    }
  }
}
```

Aún así, es más fácil pensar en Programación Dinámica de manera recursiva.

Desafío: Consideremos ahora otra versión del problema de la moneda donde nuestra tarea es
calcular el número total de formas de producir una suma x usando las monedas.
Por ejemplo, si coins = {1, 3, 4} y x = 5, hay un total de 6 formas.

Traducido desde Competitive Programmer’s Handbook - Antti Laaksonen
