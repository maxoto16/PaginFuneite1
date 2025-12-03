✅ EJERCICIO 1 — Ordenar Pares al Inicio e Impares al Final Usando Selection Sort

✔ Sin usar otra estructura
✔ Reacomodar pares → ordenar
✔ Reacomodar impares → ordenar
✔ Sólo con el mismo arreglo

⭐ Código Completo del Ejercicio 1
public static void sortEvenOddWithSelection(int[] arr) {

    // =====================================
    // 1. Primera pasada: mover pares al inicio
    // =====================================
    int evenIndex = 0;

    for (int i = 0; i < arr.length; i++) {
        if (arr[i] % 2 == 0) {
            // intercambiar arr[i] con arr[evenIndex]
            int temp = arr[i];
            arr[i] = arr[evenIndex];
            arr[evenIndex] = temp;

            evenIndex++;
        }
    }

    // now: [PARES ...] [IMPARES ...]

    // =====================================
    // 2. Ordenar SOLO los pares (0 a evenIndex - 1)
    // =====================================
    selectionSort(arr, 0, evenIndex - 1);

    // =====================================
    // 3. Ordenar SOLO los impares (evenIndex a arr.length - 1)
    // =====================================
    selectionSort(arr, evenIndex, arr.length - 1);
}


/**
 * Selection Sort entre índices start y end.
 */
public static void selectionSort(int[] arr, int start, int end) {
    for (int i = start; i <= end; i++) {
        int minIndex = i;

        for (int j = i + 1; j <= end; j++) {
            if (arr[j] < arr[minIndex]) {
                minIndex = j;
            }
        }

        // intercambiar
        int temp = arr[i];
        arr[i] = arr[minIndex];
        arr[minIndex] = temp;
    }
}

⭐ PRUEBA EN MAIN
public static void main(String[] args) {

    int[] datos = {7, 2, 9, 4, 6, 3, 8};

    sortEvenOddWithSelection(datos);

    System.out.print("Resultado: ");
    for (int n : datos) {
        System.out.print(n + " ");
    }
}

✔ Salida esperada:
2 4 6 8 3 7 9

✅ EJERCICIO 2 — Insertion Sort + Comparar Primer y Último

El programa debe:

✔ Pedir n
✔ Leer n números
✔ Ordenar con Insertion Sort
✔ Comparar primer vs último
✔ Imprimir resultado

⭐ Código Completo del Ejercicio 2
import java.util.Scanner;

public class Main {

    // =============== INSERTION SORT ===============
    public static void insertionSort(int[] arr) {
        for (int i = 1; i < arr.length; i++) {

            int key = arr[i];
            int j = i - 1;

            // mover elementos mayores a la derecha
            while (j >= 0 && arr[j] > key) {
                arr[j + 1] = arr[j];
                j--;
            }

            arr[j + 1] = key;
        }
    }

    public static void main(String[] args) {

        Scanner sc = new Scanner(System.in);

        System.out.print("Ingresa la cantidad de elementos: ");
        int n = sc.nextInt();

        int[] arr = new int[n];

        // Leer datos
        System.out.println("Ingresa " + n + " números:");
        for (int i = 0; i < n; i++) {
            arr[i] = sc.nextInt();
        }

        // Ordenar
        insertionSort(arr);

        // Mostrar arreglo ordenado
        System.out.print("Arreglo ordenado: ");
        for (int num : arr) {
            System.out.print(num + " ");
        }
        System.out.println();

        // Comparar primer y último
        int primero = arr[0];
        int ultimo = arr[n - 1];

        if (primero == ultimo) {
            System.out.println("El primer y último elemento SON IGUALES.");
        } else if (primero < ultimo) {
            System.out.println("El primer elemento es MENOR que el último.");
        } else {
            System.out.println("El primer elemento es MAYOR que el último.");
        }
    }
}
