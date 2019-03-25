# Baloto-en-java
Tengo dudas a cerca de la comparación entre una matriz y un vector, ya que para que me imprima la cantidad de aciertos del algoritmo necesito comparar el vector ganador con las filas de las matrices que son n y me de el total de aciertospackage balotomatriz;

import java.util.Arrays;
import java.util.Random;
import javax.swing.JOptionPane;

public class Balotomatriz {
    int cargar[];
    int boleto[];
    int sorteo[][];
    int num;

    public Balotomatriz() {
        num = Integer.parseInt(JOptionPane.showInputDialog("Digite eltamaño de las filas: "));//Comparar el vector con toda la matriz uno x uno
        sorteo = new int[num][5];
        boleto = new int[5];
        cargar = new int[num*5];
    }
    
    public void aciertos (){//Seria en este metodo que tengo la duda
        int acierto = 0,acierto1 = 0;
        for (int i = 0; i < sorteo.length; i++) {
            for (int j = 0; j < 5 ;j++) {
                cargar[acierto]= sorteo[i][j];
                if (cargar [acierto]==boleto[j] ) {
                    acierto++;
                }
            }
        }
        JOptionPane.showMessageDialog(null, "El numero de aciertos es de: " + acierto+"\n");
    }

    public void llenar() {
        Random random = new Random();
        int num1;
        for (int i = 0; i < sorteo.length; i++) {
            for (int j = 0; j < 5; j++) {
                num1 = random.nextInt(49)+1;
                sorteo[i][j] = num1;
            }
        }
    }

    public void mostrarllenar() {
        String acu = " ";
        String acu1 = " ";
        for (int i = 0; i < sorteo.length; i++) {
            for (int j = 0; j < 5; j++) {

                acu = acu + "| " + sorteo[i][j] + " |";
            }

            acu = acu + "\n";

        }
        for (int i = 0; i < 5; i++) {
            acu1 = acu1 + "| " + boleto[i] + " |";
            acu1 = acu1 + "\n";
        }
        JOptionPane.showMessageDialog(null, "Boleto generado es: \n" + acu1 + "Serial personal: \n" + acu);
    }

    public void boletoganador() {
        Random random = new Random();
        int num1;
        for (int i = 0; i < 5; i++) {
                num1 = random.nextInt(49)+1;
                boleto[i] = num1;


        }
    }

    public static void main(String[] args) {
        // TODO code application logic here
        Balotomatriz item = new Balotomatriz();
        item.boletoganador();
        item.llenar();
        item.mostrarllenar();
        item.aciertos();
    }

}
