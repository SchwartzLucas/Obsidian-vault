
Overloading é quando implementamos o mesmo método várias vezes dentro de uma mesma classe, mas passamos parâmetros diferentes em cada uma delas, como por exemplo:

```
package OverloadigOverriding;  
  
import java.util.Arrays;  
import java.util.Objects;  
  
public abstract class method {  
  
    public void process(int a, int b){  
        System.out.println("processando dois inteiros: " + a + b);  
    }  
    public void process(int[] ints){  
        System.out.println("processando um array: " + Arrays.toString((ints)));  
    }  
    public void process(Object[] obj){  
        System.out.println("processando um objeto: " + Arrays.toString((obj)));  
    }  
  
  
}
```

temos 3 métodos process, mas os 3 fazem coisas diferentes e possuem parâmetros diferentes

Overriding seria sobrescrever esses métodos em outra classe ou lugar, por exemplo:

```
package OverloadigOverriding;  
  
public class MathProcessor extends method{  
  
    @Override  
    public void process(int a, int b){  
        System.out.println("Somando inteiros: " + (a + b));  
    }  
  
    @Override  
    public void process(int[] ints) {  
        int sum = 0;  
        for(int i = 0; i < ints.length; i++){  
            sum += ints[i];  
        }  
        System.out.println("Soma dos inteiros do array: " + sum);  
    }  
  
}
```

Utilizamos as palavras reservadas extends para se referir a outra classes (super) e a palavra @Override para sobrescrever os métodos da outra classe para fazer outra coisa que somente a classe MathProcessor faz com esses métodos (quase como ua classe abstrata, mas sem a obrigação de escrever os métodos todos)

Rodando isso:

```
package OverloadigOverriding;  
  
public class Runit {  
    public static void main(String[] args){  
        MathProcessor mp = new MathProcessor();  
        method mt = new method();  
  
        int[] a = {1,2,3,4,5};  
        mp.process(a);  
        mp.process(2,3);  
  
        mt.process(a);  
        mt.process(2,3);  
    }  
}
```

obtemos o output:

```
Soma dos inteiros do array: 15
Somando inteiros: 5
processando um array: [1, 2, 3, 4, 5]
processando dois inteiros: 23
```

Dessa maneira podemos chamar o mesmo método e ele irá entender o que usar conforme o que foi passado nele.