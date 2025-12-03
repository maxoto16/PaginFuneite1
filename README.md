si
📘 Proyecto: Implementación de Algoritmos y Lista Dinámica en Java

Este proyecto reúne tres ejercicios fundamentales de algoritmos y estructuras de datos dentro de un solo programa Java, incluyendo:

🔁 Bubble Sort con conteo de intercambios

🗑️ Eliminación por índice en una lista dinámica

🔎 Búsqueda con indexOf

🖥️ Menú interactivo

🧩 Código totalmente integrado

📊 Diagrama General del Proyecto
flowchart TD
    A[ProgramaUnico.java] --> B[bubbleSortCountSwaps()]
    A --> C[Clase interna MiLista]
    C --> C1[add()]
    C --> C2[removeAt()]
    C --> C3[indexOf()]
    C --> C4[print()]
    A --> D[main() con menú interactivo]

    B --> E[Ordenamiento Bubble Sort]
    C2 --> F[Eliminación por índice]
    C3 --> G[Búsqueda lineal]

🔁 1. Bubble Sort con conteo de swaps

Método:

public static int bubbleSortCountSwaps(int[] arr)

🧠 Diagrama del proceso Bubble Sort
flowchart LR
    A[Inicio] --> B{¿i < n-1?}
    B -->|Sí| C{¿arr[j] > arr[j+1]?}
    C -->|Sí| D[Intercambiar valores]
    D --> E[swaps++]
    C -->|No| F[Siguiente j]
    E --> F
    F --> G{¿Se hicieron cambios?}
    G -->|No| H[Terminar]
    G -->|Sí| I[Siguiente i]
    I --> B
    B -->|No| H


📌 Funcionalidad:

Ordena un arreglo ascendente.

Cuenta cuántos intercambios fueron necesarios.

Optimizado con detección de ordenamiento anticipado.

🗂️ 2. Implementación de Lista Dinámica (MiLista)

Representa una estructura tipo ArrayList hecha manualmente.

📦 Diagrama Interno de MiLista
classDiagram
    class MiLista {
        - int[] arr
        - int size
        + add(int)
        + removeAt(int)
        + indexOf(int)
        + print()
    }

🗑️ removeAt(int index)

Método:

public int removeAt(int index)


📌 Acciones:

Verifica índice válido.

Guarda el valor eliminado.

Recorre elementos hacia la izquierda.

Reduce size.

🔧 Diagrama del proceso removeAt
flowchart TD
    A[removeAt(index)] --> B{¿index válido?}
    B -->|No| C[Lanzar IndexOutOfBoundsException]
    B -->|Sí| D[Guardar valor eliminado]
    D --> E[Recorrer elementos una posición a la izquierda]
    E --> F[size--]
    F --> G[Retornar eliminado]

🔎 3. indexOf(int value)

Método:

public int indexOf(int value)


Funcionalidad:

Busca la primera aparición de un valor.

Retorna -1 si no existe.

🔍 Diagrama del proceso indexOf
flowchart TD
    A[indexOf(value)] --> B[Recorrer arreglo]
    B --> C{¿arr[i] == value?}
    C -->|Sí| D[Retornar i]
    C -->|No| E{¿Fin del arreglo?}
    E -->|No| B
    E -->|Sí| F[Retornar -1]

🖥️ Menú Interactivo
===== MENÚ =====
1. bubbleSortCountSwaps
2. removeAt
3. indexOf
0. Salir

👨‍💻 CÓDIGO COMPLETO (TODO EL MAIN Y TODAS LAS CLASES)
import java.util.Scanner;

public class ProgramaUnico {

    // ===========================
    // 1. bubbleSortCountSwaps
    // ===========================
    public static int bubbleSortCountSwaps(int[] arr) {
        int swaps = 0;
        boolean cambio;

        for (int i = 0; i < arr.length - 1; i++) {
            cambio = false;
            for (int j = 0; j < arr.length - 1 - i; j++) {
                if (arr[j] > arr[j + 1]) {
                    int temp = arr[j];
                    arr[j] = arr[j + 1];
                    arr[j + 1] = temp;
                    swaps++;
                    cambio = true;
                }
            }
            if (!cambio) break;
        }
        return swaps;
    }

    // ===========================
    // Lista dinámica
    // ===========================
    static class MiLista {
        private int[] arr;
        private int size;

        public MiLista() {
            arr = new int[10];
            size = 0;
        }

        public void add(int value) {
            if (size == arr.length) {
                int[] nuevo = new int[arr.length * 2];
                System.arraycopy(arr, 0, nuevo, 0, arr.length);
                arr = nuevo;
            }
            arr[size++] = value;
        }

        public int removeAt(int index) {
            if (index < 0 || index >= size)
                throw new IndexOutOfBoundsException("Índice inválido: " + index);

            int eliminado = arr[index];

            for (int i = index; i < size - 1; i++)
                arr[i] = arr[i + 1];

            size--;
            return eliminado;
        }

        public int indexOf(int value) {
            for (int i = 0; i < size; i++)
                if (arr[i] == value)
                    return i;
            return -1;
        }

        public void print() {
            for (int i = 0; i < size; i++)
                System.out.print(arr[i] + (i < size - 1 ? ", " : ""));
            System.out.println();
        }
    }

    // ===========================
    // MAIN CON MENÚ
    // ===========================
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        MiLista lista = new MiLista();
        int opcion;

        do {
            System.out.println("\n===== MENÚ =====");
            System.out.println("1. bubbleSortCountSwaps");
            System.out.println("2. removeAt");
            System.out.println("3. indexOf");
            System.out.println("0. Salir");
            System.out.print("Elige una opción: ");
            opcion = sc.nextInt();

            switch (opcion) {

                case 1:
                    System.out.println("\n--- Prueba bubbleSortCountSwaps ---");
                    int[] datos = {3, 2, 1};
                    int swaps = bubbleSortCountSwaps(datos);

                    System.out.print("Arreglo ordenado: ");
                    for (int n : datos) System.out.print(n + " ");
                    System.out.println("\nSwaps realizados: " + swaps);
                    break;

                case 2:
                    System.out.println("\n--- Prueba removeAt ---");
                    lista = new MiLista();

                    lista.add(3);
                    lista.add(6);
                    lista.add(9);
                    lista.add(12);
                    lista.add(15);

                    int eliminado = lista.removeAt(2);

                    System.out.println("Eliminado: " + eliminado);
                    System.out.print("Lista: ");
                    lista.print();
                    break;

                case 3:
                    System.out.println("\n--- Prueba indexOf ---");
                    lista = new MiLista();

                    lista.add(4);
                    lista.add(8);
                    lista.add(4);
                    lista.add(10);
                    lista.add(4);

                    System.out.println("indexOf(4) = " + lista.indexOf(4));
                    System.out.println("indexOf(10) = " + lista.indexOf(10));
                    System.out.println("indexOf(7) = " + lista.indexOf(7));
                    break;

                case 0:
                    System.out.println("Saliendo...");
                    break;

                default:
                    System.out.println("Opción inválida.");
            }

        } while (opcion != 0);

        sc.close();
    }
}

🚀 Cómo ejecutar
javac ProgramaUnico.java
java ProgramaUnico
