🚀 T1 — PROYECTO 1 (El que me diste al inicio)

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

Bubble Sort con conteo de intercambios

Implementación manual de MiLista

indexOf

removeAt

Menú interactivo

📌 (Ya lo generé y no lo repito para no saturar, pero si quieres lo vuelvo a incluir completo en un README).

🚀 T2 — PROYECTO 2 (SinglyLinkedList + toArray + BubbleSort)

Este es TOTALMENTE INDEPENDIENTE del T1.
Aquí está TODO EL CÓDIGO COMPLETO con comentarios.

📦 T2 — CÓDIGO COMPLETO
⭐ Node.java
// Nodo para la lista simplemente ligada
public class Node {
    int data;       // valor almacenado
    Node next;      // referencia al siguiente nodo

    public Node(int data) {
        this.data = data;
        this.next = null;
    }
}

⭐ SinglyLinkedList.java
public class SinglyLinkedList {

    private Node head;   // inicio de la lista
    private int size;    // cantidad de nodos

    public SinglyLinkedList() {
        this.head = null;
        this.size = 0;
    }

    // ============================================
    // a) AGREGAR AL FINAL
    // ============================================
    public void addLast(int value) {
        Node nuevo = new Node(value);

        // Lista vacía
        if (head == null) {
            head = nuevo;
        } else {
            // Recorrer hasta el último nodo
            Node actual = head;
            while (actual.next != null) {
                actual = actual.next;
            }
            actual.next = nuevo;
        }

        size++;
    }

    // ============================================
    // b) REGRESAR EL TAMAÑO
    // ============================================
    public int size() {
        return size;
    }

    // ============================================
    // c) OBTENER UN NODO POR ÍNDICE
    // ============================================
    public int get(int index) {
        if (index < 0 || index >= size) {
            throw new IndexOutOfBoundsException("Índice inválido: " + index);
        }

        Node actual = head;
        for (int i = 0; i < index; i++) {
            actual = actual.next;
        }

        return actual.data;
    }

    // ============================================
    // d) IMPRIMIR LA LISTA
    // ============================================
    public void printList() {
        Node actual = head;
        while (actual != null) {
            System.out.print(actual.data);
            if (actual.next != null) System.out.print(", ");
            actual = actual.next;
        }
        System.out.println();
    }
}

⭐ Main.java (toArray + BubbleSort + Prueba)
import java.util.*;

public class Main {

    // =====================================================
    // Convertir lista a arreglo
    // =====================================================
    public static int[] toArray(SinglyLinkedList list) {

        int[] arr = new int[list.size()];

        // Rellenar arreglo usando get(i)
        for (int i = 0; i < arr.length; i++) {
            arr[i] = list.get(i);
        }

        return arr;
    }

    // =====================================================
    // Bubble Sort ascendente
    // =====================================================
    public static void bubbleSort(int[] arr) {
        boolean cambio;

        do {
            cambio = false;

            for (int i = 0; i < arr.length - 1; i++) {
                if (arr[i] > arr[i + 1]) {

                    // intercambiar
                    int temp = arr[i];
                    arr[i] = arr[i + 1];
                    arr[i + 1] = temp;

                    cambio = true;
                }
            }
        } while (cambio);
    }

    // =====================================================
    // MAIN
    // =====================================================
    public static void main(String[] args) {

        // 1) Crear lista
        SinglyLinkedList lista = new SinglyLinkedList();

        // 2) Agregar temperaturas
        lista.addLast(28);
        lista.addLast(31);
        lista.addLast(26);
        lista.addLast(30);
        lista.addLast(29);

        // 3) Imprimir lista original
        System.out.println("Lista original:");
        lista.printList();

        // 4) Convertir a arreglo
        int[] arr = toArray(lista);

        // 5) Ordenar con Bubble Sort
        bubbleSort(arr);

        // 6) Imprimir arreglo ordenado
        System.out.println("Arreglo ordenado:");
        for (int n : arr) {
            System.out.print(n + " ");
        }
        System.out.println();
    }
}

✔ Salida esperada del T2
Lista original:
28, 31, 26, 30, 29

Arreglo ordenado:
26 28 29 30 31
