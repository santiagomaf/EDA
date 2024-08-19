# Libro guia

Un algoritmo es cualquier proceso computacional.\
Dentro de un algoritmo debe tener un conjunto de entradas y salidas y estas pueden tener distintos tipos de instrucciones o sentencias.
- Asignación
- Operaciones de entrada/salida
- Control de flujo condicional
- Control de flujo competitivo

### Tiempo de ejecución

Se determina por dos factores:
- El costo de ejecutar una sentencia.
- La frecuencia de ejecución.

$$ T(n) = \sum_{s=@} costo(s) * frecuancia(s) $$

Donde *s* es una sentencia de *@*.

Un ejemplo:
````c++
if n%2 = 0 then
    ans <-- true
else
    ans <-- false
end if
return ans
````
Vamos viendo los costos.
$$ T (n) =costo(s_{if} ) × frecuencia(s_{comp})+
costo(s_{asig} ) × frecuencia(s_{asig} )+
costo(s_{return}) × frecuencia(s_{return})
 $$
es igual a: $$ T(n) = 1+1+1 = 3  $$

### Algoritmos De Ordenación

##### Ordenación por Selección

Es un algorimo fácil de implementar. Es ir recorriendo el arreglo de entrada y en cada posición seleccionar el menor de los que faltan por ordenar, luego el elemento selecionado es intercambiado por el elemento de la posición actual.

El bloque de código quedaria así:
````cpp
#include <iostream>
#include <vector>

void Ordenacion_por_seleccion(std::vector<int>& arr) {
    int n = arr.size();
    for (int i = 0; i < n - 1; ++i){
        int IndexMin = i;
        for (int j = i +1; j < n;++i){
            if (arr[j] < arr[IndexMin]){
                IndexMin = j;
            }
        }
        std::swap(arr[i], arr[IndexMin]);
    }
}

````
Esto vendría siendo el algoritmo de una ordenación por selección.\
Basicamente el primer *for* recorre la lista hasta el penultimo numero, dentro del este ciclo hay otro que parte desde el indice del primero + 1 y va buscando un valor menor gracias a un *if* si lo encuentra lo **intercambia**, así hasta el final de la lista.
##### Inserción
Es un algoritmo que sigue la regla de *ordenación de cartas*, vamos recoriendo la lista y lo va poniendo en la posición que corresponde.

````cpp
#include <iostream>
#include <vector>

void InsertionSort(std::vector<int>& arr){

    int n = arr.size();
    for (int i = 1; i < n; ++i){
        int key = arr[i];
        int j = i - 1;

        while (j >= 0 && arr[j] > key){
            arr[j+1] = arr[j];
            --j;
        }
        arr[j+1] = key;
    }
}
````

Si revisamos este algoritmo podemos ver que entra un arreglo de n numeros, luego entra en un ciclo for que marca *i* como la clave, que parte en la segunda posición, y la clave *j* como i - 1, esta parte en la primera posición, lo otro que definimos es la variable *key* que es el numero que esta en la posición i de la lista que vamos a analizar. Luego de definir las variables entra en un *while* que como condiciones tiene que si j es mayor o igual a 0 y que el numero de la posición de j es mayor que la variable key entra, osea nuestro elemento es menor que el valor de j, lo que hace es que la variable j+1 pasa a ser la j, luego se resta 1 a j y luego pasa a ser j+1 igual a la llave.\
En mis palabras es que agarra un numeo y cuando ese numeor el siguente es menor, mueve el menor todo el rato hacia atras hasta que el numero que topa es mayor

