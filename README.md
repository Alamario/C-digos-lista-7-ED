import java.util.*;
import java.io.*;

class Elemento{
    String ip;
    int cont;
    
    public Elemento(){
        
    }

}

public class Teste {
    public static void main(String[] arg) throws Exception{
       LinkedList<Elemento> L = new LinkedList();
       FileInputStream stream = new FileInputStream("C:\\Users\\Sarai\\Desktop\\acesslog\\access.log");
       InputStreamReader reader = new InputStreamReader(stream);
       BufferedReader br = new BufferedReader(reader);
       String linhaLog = br.readLine();
     
        
       //enquanto que a linha do arquivo log for diferente de null
       while(linhaLog != null){
           
          
          
           Elemento E = new Elemento();
           String ipLog = linhaLog.substring(0, linhaLog.indexOf("-") - 1);
           // apenas String ip do log
           
           
           //a variavel ip do elemento armazena ip log
           E.ip = ipLog;
           
           //int h para saber se o ip log já está na lista
           int h = 0;
           
           //variavel a para percorrer a lista
        
           
           //variavel a para percorrer a lista
           ListIterator<Elemento> a = L.listIterator();

           
           //método para saber se ip log já foi usado e acrescentar no contador
       
               while(a.hasNext()){
                   Elemento A = new Elemento();
                   A = a.next();
                   if(A.ip.equals(E.ip)){
                       h++;
                       A.cont++;
                       a.equals(A);
                   
                   }
                         
               
           }
           
         
           //caso o ip log não esteja na lista     
           if(h==0){
               
               E.cont++;
               L.add(E);//add o elemente E que contem o ip log na lista e aumente 1 seu contador
               
           }
        
              
          linhaLog = br.readLine();
       }
       
       int D = 100;
       FileInputStream str = new FileInputStream("C:\\Users\\Sarai\\Desktop\\acesslog\\ajuda.txt");
       InputStreamReader rd = new InputStreamReader(str);
       BufferedReader brd = new BufferedReader(rd);
       String linhaConsulta = brd.readLine();
       
       long media, soma = 0, mediana, DP, somadp = 0, max = 0, min = 100000;
       long[] tempo = new long[D];
       while(linhaConsulta != null){
           int aux = 0;
           ListIterator<Elemento> in = L.listIterator();
           long inicio = System.currentTimeMillis();
           while(in.hasNext()){
               
               Elemento El = in.next();
               if(El.ip.equals(linhaConsulta)){
                   System.out.println(El.ip + ": " + El.cont);
               
               }
             
             
           }
           long fim = System.currentTimeMillis();
           tempo[aux] = fim - inicio;
          
           aux++;
           
       linhaConsulta = brd.readLine();
       }
       
       int aux = 0;
       while(aux < D){
           soma = soma + tempo[aux];
           
           if(tempo[aux] > max)
               max = tempo[aux];
           if(tempo[aux] < min)
               min = tempo[aux];
           aux++;
       
       }
       media = soma/D;
        
        
        mediana = (tempo[1] + tempo[0])/D;
        
        aux = 0;
        while(aux < D){
            somadp = somadp + ((tempo[aux] - media)*(tempo[aux] - media));
            aux++;
        
        }
        DP = (long) Math.sqrt(somadp/D);
        
        System.out.println("\n");
        System.out.println("Tempo medio: " + media + " milisegundos");
        System.out.println("mediana: " + mediana + " milisegundos");
        System.out.println("minimo: " + min + " milisegundos");
        System.out.println("maximo: " + max + " milisegundos");
        System.out.println("Desvio Padrao: " + DP);
      
 }
    
}
