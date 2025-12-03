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
