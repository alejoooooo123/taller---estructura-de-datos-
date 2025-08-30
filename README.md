# taller---estructura-de-datos-
codigo de taller
import java.util.*;

class GrafoMatriz {
    private List<String> vertices;
    private int[][] matriz;

    public GrafoMatriz() {
        vertices = new ArrayList<>();
        matriz = new int[0][0];
    }

    public void agregarVertice(String v) {
        if (!vertices.contains(v)) {
            vertices.add(v);
            int n = vertices.size();
            int[][] nuevaMatriz = new int[n][n];
            for (int i = 0; i < n - 1; i++) {
                for (int j = 0; j < n - 1; j++) {
                    nuevaMatriz[i][j] = matriz[i][j];
                }
            }
            matriz = nuevaMatriz;
        }
    }

    public void agregarArista(String v1, String v2) {
        int i = vertices.indexOf(v1);
        int j = vertices.indexOf(v2);
        if (i != -1 && j != -1) {
            matriz[i][j] = 1;
            matriz[j][i] = 1; 
        }
    }

    public void mostrarMatriz() {
        System.out.print("   ");
        for (String v : vertices) {
            System.out.print(v + " ");
        }
        System.out.println();
        for (int i = 0; i < vertices.size(); i++) {
            System.out.print(vertices.get(i) + " ");
            for (int j = 0; j < vertices.size(); j++) {
                System.out.print(" " + matriz[i][j]);
            }
            System.out.println();
        }
    }

    public static void main(String[] args) {
        GrafoMatriz g = new GrafoMatriz();
        g.agregarVertice("A");
        g.agregarVertice("B");
        g.agregarVertice("C");
        g.agregarVertice("D");
        g.agregarArista("A", "B");
        g.agregarArista("B", "C");
        g.agregarArista("C", "D");
        g.agregarArista("D", "A");
        g.mostrarMatriz();
    }
}
