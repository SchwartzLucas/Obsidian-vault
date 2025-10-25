
```
package objectlife;  
  
public class ObjectLife{  
    public int area( int l, int w){  
        int result = l * w;  
          
        return result;  
    }  
  
    class Client {  
        public static void main(String[] args){  
            ObjectLife of = new ObjectLife();  
            int area = of.area(3,5);  
  
            System.out.println("Area is: " + area);  
            of = null; // explicitly deferences the variable  
        }  
    }  
      
}
```

Primeiro há a criação do objeto, neste caso o objeto ObjectLife of que então é atribuído e armazenado na memória -- enquanto estamos utilizando ele ok, ele se mantem "vivo" (of). na parte final ou "Object destruction" -- Garbage Collection ele se torna "intocável" não podendo mais ser acessado ai sim terminando o seu ciclo de vida, podemos também atribuir null a ele, fazendo o Garbage Collection ser explícito e liberando memória para o programa.
