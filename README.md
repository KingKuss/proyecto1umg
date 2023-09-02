# Proyecto 1 Algoritmos
## Presentado por:
### Bryan Josue Alvarez Lopez y Juanfran Isaias Tebalan Tecum
###### Bryan Alvarez: 7690-23-16816
###### Juanfran Tebalan: 7690-23-14080

### En este repositorio, se presentan dos ejercicios de algoritmos en C++, Python y Pseudocódigo.
##### Separados en ejercicios 1 y 2 
###### 1: Triple de Pitágoras.
###### 2: Juego denominado El ahorcado

## Triple de pitagoras.
En matemáticas, se llama terna pitagórica a cualquier conjunto de tres números naturales (a, b, c) para los cuales se cumple la relación a² + b² = c² relacionada con el teorema de pitagoras el cual puede tener respuestas del teorema de euler. Los primeros ejemplos son (3, 4, 5), (5, 12, 13), (6, 8, 10), (7, 24, 25).

## C++ - Triple de pitagoras

```cpp
#include <iostream>
using namespace std;

int main() {
    // Define un limite para las triples generadas
    int limite = 500;
    // Variables que usaremos para los numeros m, n, k, a, b y c
    int m, n, k, a, b, c;

    cout << "Bienvenido al algoritmo para generar Trsiples pitagoricas hasta el limite " << limite << ":\n";

    cout << "Triples pitagóricas hasta el límite " << limite << ":\n";

    // Ciclo exterior para iterar a traves de m
    for (m = 2; m <= limite; m++) {
        // Ciclo medio para iterar a traves de n (n < m)
        for (n = 1; n < m; n++) {
            // Ciclo interno para generar multiples ternas con el mismo m y n
            for (k = 1;; k++) {
                // Calcula los valores de a, b y c segun las formulas pitagoricas
                a = k * (m * m - n * n);
                b = k * 2 * m * n;
                c = k * (m * m + n * n);

                // Si c supera el limite, sal del ciclo interno
                if (c > limite) {
                    break;
                }

                // Imprime la terna pitagorica
                cout << "(" << a << ", " << b << ", " << c << ")\n";
            }
        }
    }

    return 0;
}
```
## Python - Triple de pitagoras
```python
# Define un límite para las triples generadas
limite = 500

print("Bienvenido al algoritmo para generar Tríples pitagóricas hasta el límite", limite, ":")
print("Tríples pitagóricas hasta el límite", limite, ":")

# Ciclo exterior para iterar a través de m
for m in range(2, limite + 1):
    # Ciclo medio para iterar a través de n (n < m)
    for n in range(1, m):
        # Ciclo interno para generar múltiples ternas con el mismo m y n
        k = 1
        while True:
            # Calcula los valores de a, b y c según las fórmulas pitagóricas
            a = k * (m ** 2 - n ** 2)
            b = k * 2 * m * n
            c = k * (m ** 2 + n ** 2)

            # Si c supera el límite, sal del ciclo interno
            if c > limite:
                break

            # Imprime la terna pitagórica
            print("(", a, ",", b, ",", c, ")")

            k += 1
```
## Pseudocodigo - Triple de pitagoras
```Pseudocode
Algoritmo GenerarTernasPitagoricas
    // Definir un límite para las ternas generadas
    Definir limite Como Entero
    limite <- 500
    // Variables para los números m, n, a, b y c de la terna pitagórica
    Definir m, n, a, b, c Como Entero
	
    Escribir "Ternas pitagóricas hasta el límite ", limite, ":"
	
    // Ciclo para iterar a través de los números m
    Para m <- 2 Hasta limite Con Paso 1 Hacer
        // Ciclo anidado para iterar a través de los números n (n < m)
        Para n <- 1 Hasta m - 1 Con Paso 1 Hacer
            // Calcular los valores de a, b y c según las fórmulas pitagóricas
            a <- m * m - n * n
            b <- 2 * m * n
            c <- m * m + n * n
			
            // Comprobar si c es un número entero y no supera el límite
            Si c <= limite Entonces
                // Imprimir la terna pitagórica
                Escribir "(", a, ", ", b, ", ", c, ")"
            Fin Si
        Fin Para
    Fin Para
Fin Algoritmo
```


## Juego de ahorcado.
Este código implementa un juego de ahorcado simple en C++ que permite al jugador adivinar una palabra secreta dentro de un límite de intentos. La palabra se muestra inicialmente con asteriscos y se revela a medida que el jugador adivina letras correctamente.


## C++ - Ahorcado
```cpp
#include <iostream>
#include <string>
using namespace std;

int main() {
    string palabraSecreta = "programacion"; // La palabra a adivinar (sin espacios ni acentos)
    string palabraAdivinada(palabraSecreta.length(), '*'); // Escribe la palabra secreta con guiones bajos
    int intentos = 0; // Contador de intentos
    char letra;
    bool letraAdivinada = false;
    cout << "¡Bienvenido al juego de ahorcado!" << endl;

    // Bucle principal del juego
    while (palabraAdivinada != palabraSecreta && intentos < 5) {
        cout << "Palabra a adivinar: " << palabraAdivinada << endl;

        cout << "Ingresa una letra: ";
        cin >> letra;

        // Comprueba si la letra ingresada está en la palabra secreta
        for (int i = 0; i < palabraSecreta.length(); i++) {
            if (palabraSecreta[i] == letra) {
                palabraAdivinada[i] = letra;
                letraAdivinada = true;
            }
        }

        // Si la letra no fue adivinada, aumenta el contador de intentos
        if (!letraAdivinada) {
            cout << "Letra incorrecta. Intentos restantes: " << 5 - intentos << endl;
            intentos++;
        }
        else {
            letraAdivinada = false;
        }

    }

    // Comprueba si el jugador ganó o perdió y muestra el mensaje correspondiente
    if (intentos < 5) {
        cout << "¡Felicidades! Has adivinado la palabra: " << palabraSecreta << endl;
    }
    else {
        cout << "¡Agotaste tus intentos! La palabra correcta era: " << palabraSecreta << endl;
    }

    return 0;
}
```
## Python - Ahorcado
```python
# Inicialización de variables
palabraSecreta = "programacion"  # La palabra a adivinar (sin espacios ni acentos)
palabraAdivinada = '*' * len(palabraSecreta)  # Inicializa la palabra adivinada con guiones bajos
intentos = 0  # Contador de intentos

print("¡Bienvenido al juego de ahorcado!")

# Bucle principal del juego
while palabraAdivinada != palabraSecreta and intentos < 5:
    print("Palabra a adivinar:", palabraAdivinada)

    letra = input("Ingresa una letra: ")

    # Comprueba si la letra ingresada está en la palabra secreta
    letraAdivinada = False
    for i in range(len(palabraSecreta)):
        if palabraSecreta[i] == letra:
            palabraAdivinada = palabraAdivinada[:i] + letra + palabraAdivinada[i + 1:]
            letraAdivinada = True

    # Si la letra no fue adivinada, aumenta el contador de intentos
    if not letraAdivinada:
        print("Letra incorrecta. Intentos restantes:", 5 - intentos)
        intentos += 1

# Comprueba si el jugador ganó o perdió y muestra el mensaje correspondiente
if intentos < 5:
    print("¡Felicidades! Has adivinado la palabra:", palabraSecreta)
else:
    print("¡Agotaste tus intentos! La palabra correcta era:", palabraSecreta)
```

## Adjunto un video acerca de nuestro tema, y nuestros proyectos en un breve resumen
# https://youtu.be/phnB7hUmLRg

## Tareas que realizaron los integrantes del grupo:
#### Bryan: 
###### El Algoritmo de el triple de pitagoras y el repositorio en Github
#### Juanfran: 
###### El Algoritmo de el juego Ahorcado y el video en Youtube

## Gracias por su atencion
## Saludos
