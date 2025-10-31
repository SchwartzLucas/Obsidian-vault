
## Declaração ordem de inicializadores de instância

Análogo para os outros inicializadores discutidos anteriormente, um bloco inicializador de instância não pode fazer uma referência de encaminhamento a um campo por seu nome simples em uma operação de leitura, porque isso violaria a regra de declaração-antes de leitura. No entanto, usando o `this`palavra-chave para acessar um campo não é um problema.

A classe no **Código 1** tem um bloco inicializador de instâncias na linha (1) com referências de encaminhamento para os campos `i`, `j`, e `k`, que são declarados nas linhas (7), (8) e (9), respectivamente. Esses campos são acessados usando o `this`referência em operações de leitura nas linhas (3), (4), (5) e (6). Usar o nome simples desses campos nas linhas (3), (4), (5) e (6) para acessar seus valores violará a regra de declaração-antes do uso, resultando em erros de tempo de compilação – independentemente de os campos serem declarados com expressões de inicializador ou se são finais.

Os campos `i`e `j`são acessados na linha (2) em operações de gravação, que são permitidas usando o nome simples. No entanto, deve-se ter cuidado para garantir que os campos sejam inicializados corretamente. Nas linhas (3), (4) e (5), os campos `i`e `j`ter o valor 10. No entanto, quando as expressões do inicializador são avaliadas nas declarações de campo de instância, o valor de `j`será definido para 100.

**Códigos 1.** Acessando campos usando a palavra-chave this:

```
public class InstanceInitializersII {

   { //Instance initializer with forward references. (1)
      i = j = 10;                                 // (2) Permitted.
      int result = this.i * this.j;               // (3) i is 10, j is 10. 

      System.out.println(this.i);                 // (4) 10
      System.out.println(this.j);                 // (5) 10
      System.out.println(this.k);                 // (6) 50
   }

   // Instance field declarations. 
   int i;             // (7) Field declaration without initializer expression
   int j = 100;       // (8) Field declaration with initializer expression.
   final int k = 50;  // (9) Final instance field with constant expression. 
}
```

**O código 2** ilustra alguns pontos sutis adicionais em relação aos blocos inicializadores de instâncias. Uma referência de encaminhamento ilegal ocorre no código na linha (4), que tenta ler o valor do campo `nsf1`antes de ser declarado. A operação de leitura na linha (11) ocorre após a declaração; portanto, é permitida. Referências encaminhadas feitas no lado esquerdo da atribuição são sempre permitidas, como mostrado nas linhas (2), (3), (5) e (7). Enquanto isso, declarar variáveis locais usando a palavra reservada var em blocos inicializadores de instância é mostrado nas linhas (5) e (12).

**Código 2.** Inicializadores de instâncias e referências de encaminhamento:

```
public class NonStaticForwardReferences {

   {                                    // (1) Instance initializer block.
      nsf1 = 10;                        // (2) OK. Assignment to nsf1 allowed.
      nsf1 = sf1;                       // (3) OK. Static field access in nonstatic context.
      // int a = 2 * nsf1;              // (4) Not OK. Read operation before declaration.
      var b = nsf1 = 20;                // (5) OK. Assignment to nsf1 allowed.
      int c = this.nsf1;                // (6) OK. Not accessed by simple name.
   }

   int nsf1 = nsf2 = 30;                // (7) Nonstatic field. Assignment to nsf2 allowed.
   int nsf2;                            // (8) Nonstatic field.
   static int sf1 = 5;                  // (9) Static field.

   {                                    // (10) Instance initializer block.
      int d = 2 * nsf1:                 // (11) OK. Read operation after declaration.
      var e = nsf1 = 50;                // (12) OK. Assignment to nsf1 allowed.
   }


   public static void main(String[] args) {
      NonStaticForwardReferences objRef = new NonStaticForwardReferences () ;
      System.out.println("nsf1: " + objRef.nsf1) ;
      System.out.println("nsf2: objRef.nsf2);
   }
}
```

O seguinte é a saída do **Código 2** :

`nsf1: 50`  
`nsf2: 30`

Como em uma expressão inicializador de instância, as palavras-chave `this`e `super`pode ser usado para se referir ao objeto atual em um bloco inicializador de instância. (Não é permitida uma declaração de retorno em blocos inicializadores de instância).

Um bloco inicializador de instância pode ser usado para fatorar código de inicialização comum que será executado independentemente de qual construtor é invocado. Um uso típico de um bloco inicializador de instância está em classes anônimas, que não podem declarar construtores, mas podem usar blocos de inicializador de instância para inicializar campos. Na **Código 3**, a classe anônima definida na linha (1) usa um bloco inicializador de instância na linha (2) para inicializar seus campos.

**Código 3.** Bloco inicializador de instâncias em uma classe anônima:

```
class Base {  
    protected int a;  
    protected int b;  
    void print() { System.out.println("a: " + a); }  
}  
  
class AnonymousClassMaker {  
    Base createAnonymous() {  
        return new Base() {     // (1) Anonymous class  
            {                    // (2) Instance initializer  
                a = 5; b = 10;  
            }  
  
            @Override  
            void print() {  
                super.print();  
                System.out.println("b: " + b);  
            }  
        }; // end anonymous class  
    }  
}
```

A seguir está a saída do **Código 3** :

`a: 5`  
`b: 10`

## Manuseio de exceção em blocos de inicializador de instância

O manuseio de exceções em blocos inicializadores de instância é semelhante ao dos blocos inicializadores estáticos. No entanto, o manuseio de exceções em blocos inicializadores de instância difere do que em blocos inicializadores estáticos no seguinte aspecto: A execução de um bloco inicializador de instância pode resultar em uma exceção verificada não capturada, desde que a exceção seja declarada no `throws`cláusula de todo construtor da classe. Os blocos estáticos não podem permitir isso, uma vez que nenhum construtor está envolvido na inicialização de classe. Blocos inicializadores de instâncias em classes anônimas têm liberdade ainda maior: eles podem lançar qualquer exceção.

Código completo com main e após isso o output:

```
package InitializerBlock;  
  
class Base {  
    protected int a;  
    protected int b;  
    void print() { System.out.println("a: " + a); }  
}  
  
class AnonymousClassMaker {  
    Base createAnonymous() {  
        return new Base() {     // (1) Anonymous class  
            {                    // (2) Instance initializer  
                a = 5; b = 10;  
            }  
  
            @Override  
            void print() {  
                super.print();  
                System.out.println("b: " + b);  
            }  
        }; // end anonymous class  
    }  
}  
  
public class InitializerBlock {  
  
    {  
        System.out.println("Static inicializer 1");  
    }  
  
    public InitializerBlock(){  
        System.out.println("object intancied");  
    }  
  
    public static void main(String[] args){  
        InitializerBlock intBlock = new InitializerBlock();  
        InstanceInitializersII instance = new InstanceInitializersII();  
  
        //System.out.println("i na main: "+ instance.i);  
  
        System.out.println("nsf1: " + intBlock.nsf1);  
        System.out.println("nsf2: " + intBlock.nsf2);  
  
        new AnonymousClassMaker().createAnonymous().print();  
  
    }  
  
    static {  
        System.out.println("Static inicializar 2 - after the main method");  
    }  
  
    {                                    // (1) Instance initializer block.  
        int nsf1 = 10;                        // (2) OK. Assignment to nsf1 allowed.  
        nsf1 = sf1;                       // (3) OK. Static field access in nonstatic context.  
        // int a = 2 * nsf1;              // (4) Not OK. Read operation before declaration.        var b = nsf1 = 20;                // (5) OK. Assignment to nsf1 allowed.  
        int c = this.nsf1;                // (6) OK. Not accessed by simple name.  
    }  
  
    int nsf1 = nsf2 = 30;                // (7) Nonstatic field. Assignment to nsf2 allowed.  
    int nsf2;                            // (8) Nonstatic field.  
    static int sf1 = 5;                  // (9) Static field.  
  
    {                                    // (10) Instance initializer block.  
        int d = 2 * nsf1;                // (11) OK. Read operation after declaration.  
        var e = nsf1 = 50;                // (12) OK. Assignment to nsf1 allowed.  
    }  
  
    public static class InstanceInitializersII {  
  
        { //Instance initializer with forward references. (1)  
            i = j = 10;                                 // (2) Permitted.  
            int result = this.i * this.j;               // (3) i is 10, j is 10.  
  
            System.out.println("i na classe static " + this.i);                 // (4) 10  
            System.out.println("j na classe static " + this.j);                 // (5) 10  
            System.out.println("k na classe static " + this.k);                 // (6) 50  
        }  
  
        // Instance field declarations.  
        int i;             // (7) Field declaration without initializer expression  
        int j = 100;       // (8) Field declaration with initializer expression.  
        final int k = 50;  // (9) Final instance field with constant expression.  
    }  
}
```

Output deste código será o seguinte:

```
// output:

Static inicializar 2 - after the main method
Static inicializer 1
object intancied
i na classe static 10
j na classe static 10
k na classe static 50
nsf1: 50
nsf2: 30
a: 5
b: 10
```

Por conta da sequência quanto ao blocos estáticos (static) e instanciação de objetos;
