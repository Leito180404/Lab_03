public class MergeSort {

    // Método principal para ordenar un arreglo
    public static void mergeSort(int[] array) {
        if (array.length <= 1) {
            return; // El arreglo ya está ordenado
        }
        
        int mid = array.length / 2;  // Encuentra el punto medio
        int[] left = new int[mid];  // Sub-arreglo izquierdo
        int[] right = new int[array.length - mid];  // Sub-arreglo derecho

        // Copiar los datos en los arreglos izquierdo y derecho
        System.arraycopy(array, 0, left, 0, mid);
        System.arraycopy(array, mid, right, 0, array.length - mid);

        // Ordenar los sub-arreglos recursivamente
        mergeSort(left);
        mergeSort(right);

        // Fusionar los arreglos ordenados
        merge(array, left, right);
    }

    // Método para fusionar dos sub-arreglos ordenados
    public static void merge(int[] array, int[] left, int[] right) {
        int i = 0, j = 0, k = 0;

        // Combinamos los arreglos izquierdo y derecho
        while (i < left.length && j < right.length) {
            if (left[i] <= right[j]) {
                array[k] = left[i];
                i++;
            } else {
                array[k] = right[j];
                j++;
            }
            k++;
        }

        // Copiar los elementos restantes de left[], si los hay
        while (i < left.length) {
            array[k] = left[i];
            i++;
            k++;
        }

        // Copiar los elementos restantes de right[], si los hay
        while (j < right.length) {
            array[k] = right[j];
            j++;
            k++;
        }
    }

    // Método para imprimir un arreglo
    public static void printArray(int[] array) {
        for (int i : array) {
            System.out.print(i + " ");
        }
        System.out.println();
    }

    public static void main(String[] args) {
        int[] array = {38, 27, 43, 3, 9, 82, 10};

        System.out.println("Arreglo Original:");
        printArray(array);

        mergeSort(array);  // Ordenar el arreglo

        System.out.println("Arreglo Ordenado:");
        printArray(array);
    }
}
