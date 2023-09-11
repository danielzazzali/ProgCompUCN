# Introducción a la Biblioteca Estándar de C++

## ¿Qué es la Biblioteca Estándar de C++?

La Biblioteca Estándar de C++ (STL) es una colección de clases y funciones diseñada para hacer que el uso de las
estructuras de datos y los algoritmos comunes sea más fácil. Incluye cuatro componentes: algoritmos, contenedores,
funciones e iteradores.

- **Algoritmos**: Operaciones aplicables a rangos de elementos.
- **Contenedores**: Objetos que almacenan datos. Incluye `vector`, `list`, `deque`, `set`, `map` y más.
- **Funciones**: Interfaces de clases que manejan excepciones.
- **Iteradores**: Objetos que permiten recorrer elementos de un contenedor.

## Importancia de la STL en la programación competitiva

La STL es una herramienta valiosa en la programación competitiva. Sus ventajas son:

- **Rapidez**: Ofrece algoritmos y contenedores eficientes que ahorran tiempo de programación.
- **Portabilidad**: Los códigos usando STL funcionarán en diferentes sistemas.
- **Eficiencia**: Diseñada para un alto rendimiento, crucial para competencias.

---

## Contenedores

### `std::vector`
Esta es una arreglo contiguo dinámico que puede cambiar de tamaño.

```cpp
#include <iostream>
#include <vector>
 
int main()
{
    // Create a vector containing integers
    std::vector<int> v = {8, 4, 5, 9};
 
    // Add two more integers to vector
    v.push_back(6);
    v.push_back(9);
 
    // Overwrite element at position 2
    v[2] = -1;
 
    // Print out the vector
    for (int n : v)
        std::cout << n << ' ';
    std::cout << '\n';
    
    return 0;
}
```

### `std::deque`
Una cola doble donde puedes insertar o eliminar elementos del principio y del final de manera eficiente.

```cpp
#include <deque>
#include <iostream>
 
int main()
{
    // Create a deque containing integers
    std::deque<int> d = {7, 5, 16, 8};
 
    // Add an integer to the beginning and end of the deque
    d.push_front(13);
    d.push_back(25);
 
    // Iterate and print values of deque
    for (int n : d)
        std::cout << n << ' ';
    std::cout << '\n';
    
    return 0;
}
```

### `std::array`
Un arreglo contiguo de tamaño fijo.

```cpp
#include <array>
#include <iostream>

int main() {
    std::array<int, 5> arr = {1, 2, 3, 4, 5};
    for (int i : arr) {
        std::cout << i << " ";
    }
    // Output: 1 2 3 4 5

    // array <int , 5> arr;
    // arr.fill(1);

    return 0;
}
```
### `std::list`
Una lista doblemente enlazada.

```cpp
#include <list>

int main() {
    std::list<int> l = {1, 2, 3};
    l.push_front(0); 
    l.push_back(4);
    for (int i : l) {
        std::cout << i << " "; 
    }
    // Output: 0 1 2 3 4
}
```
### `std::stack`
Un stack LIFO (último en entrar, primero en salir).

```cpp
#include <stack>

int main() {
    std::stack<int> s;
    s.push(1); 
    s.push(2); 
    while(!s.empty()) {
        std::cout << s.top() << " "; 
        s.pop();
    }
    // Output: 2 1
}
```
### `std::queue`
Una cola FIFO (primero en entrar, primero en salir).

```cpp
#include <queue>

int main() {
    std::queue<int> q;
    q.push(1); 
    q.push(2);
    while(!q.empty()) {
        std::cout << q.front() << " "; 
        q.pop();
    }
    // Output: 1 2
}
```
### `std::priority_queue`
Una cola en la que el elemento más grande tiene prioridad.

```cpp
#include <queue>

int main() {
    std::priority_queue<int> pq;
    pq.push(1); 
    pq.push(2); 
    pq.push(3);
    while(!pq.empty()) {
        std::cout << pq.top() << " "; 
        pq.pop();
    }
    // Output: 3 2 1
}
```
### `std::set`
Un conjunto de claves únicas.

```cpp
#include <set>

int main() {
    std::set<int> s = {1, 4, 2, 1, 4};
    for (int i : s) {
        std::cout << i << " "; 
    }
    // Output: 1 2 4
}
```
### `std::map`
Almacena pares clave-valor de manera ordenada.

```cpp
#include <map>

int main() {
    std::map<std::string, int> m;
    m["apple"] = 1;
    m["orange"] = 2;
    for(auto& i : m) {
        std::cout << i.first << " " << i.second << "\n"; 
    }
    // Output: 
    // apple 1
    // orange 2
}
```
---

## Algoritmos

### `std::sort`
Ordena los elementos en un rango. Aquí ordenamos un vector entero:

```cpp
#include <algorithm>
#include <vector>

int main() {
    std::vector<int> v = {3, 1, 4, 1, 5, 9, 2};
    std::sort(v.begin(), v.end());
    for(auto n : v)
        std::cout << n << " ";
    // Output: 1 1 2 3 4 5 9
}
```

### `std::binary_search`

Busca un elemento especificado en un rango ordenado y devuelve si está presente o no:

```cpp
#include <algorithm>
#include <vector>

int main() {
    std::vector<int> v = {1, 2, 3, 4, 5};
    std::cout << std::binary_search(v.begin(), v.end(), 3);  // Output: 1 (true)
    std::cout << std::binary_search(v.begin(), v.end(), 6);  // Output: 0 (false)
}
```

### `std::next_permutation`

Genera la siguiente permutación de un rango en orden lexicográfico:

```cpp
#include <algorithm>
#include <string>

int main() {
    std::string s = "123";
    do {
        std::cout << s << "\n";
    } while(std::next_permutation(s.begin(), s.end()));
    // Output:
    // 123
    // 132
    // 213
    // 231
    // 312
    // 321
}
```

### `std::lower_bound`

Encuentra el primer elemento que no es menos que un valor dado:

```cpp
#include <algorithm>
#include <vector>

int main() {
    std::vector<int> v = {1, 2, 2, 2, 3, 4, 5};
    auto it = std::lower_bound(v.begin(), v.end(), 2);
    std::cout << *it;  // Output: 2
}
```

### `std::upper_bound`

Encuentra el primer elemento que es mayor que un valor dado:

```cpp
#include <algorithm>
#include <vector>

int main() {
    std::vector<int> v = {1, 2, 2, 2, 3, 4, 5};
    auto it = std::upper_bound(v.begin(), v.end(), 2);
    std::cout << *it;  // Output: 3
}
```

### `std::max` y `std::min`

Devuelven el máximo y mínimo de dos valores, respectivamente:

```cpp
#include <algorithm>

int main() {
    std::cout << std::max(1, 2);  // Output: 2
    std::cout << std::min(1, 2);  // Output: 1
}
```

### `std::merge`

Une dos rangos ordenados en uno:

```cpp
#include <algorithm>
#include <vector>
#include <iterator>

int main() {
    std::vector<int> v1 = {1, 2, 3}, v2 = {4, 5, 6}, v3;
    std::merge(v1.begin(), v1.end(), v2.begin(), v2.end(), std::back_inserter(v3));
    for(auto n : v3)
        std::cout << n << " ";
    // Output: 1 2 3 4 5 6
}
```

### `std::reverse`

Invierte un rango:

```cpp
#include <algorithm>
#include <vector>

int main() {
    std::vector<int> v = {1, 2, 3, 4, 5};
    std::reverse(v.begin(), v.end());
    for(auto n : v)
        std::cout << n << " ";
    // Output: 5 4 3 2 1
}
```

### `std::swap`

Intercambia los valores de dos objetos:

```cpp
#include <algorithm>

int main() {
    int a = 5, b = 10;
    std::swap(a, b);
    std::cout << "a = " << a << ", b = " << b;  // Output: a = 10, b = 5
}
```
---
## Utilities

### `std::pair`
Es una estructura que puede contener dos elementos de cualquier tipo de dato.

```cpp
#include <utility>

int main() {
    // Crea un par de un entero y una cadena.
    std::pair<int, std::string> p = std::make_pair(1, "one");
    
    // Imprime el primer y segundo componentes del par.
    std::cout << p.first << ", " << p.second;  // Output: 1, one
}
```

### `std::tuple`
Permite aunar múltiples valores posiblemente heterogéneos, como si fuesen un único objeto.

```cpp
#include <iostream>
#include <tuple>

int main() {
    // Crea una tupla con tres elementos: entero, cadena y carácter.
    std::tuple<int, std::string, char> t = std::make_tuple(1, "one", 'a');  

    // Imprime el primer (get<0>), segundo (get<1>) y tercer (get<2>) componentes de la tupla.
    std::cout << std::get<0>(t) << ", " << std::get<1>(t) << ", " << std::get<2>(t);  // Output: 1, one, a
}
```