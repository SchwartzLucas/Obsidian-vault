Um _Java Enum_ é um tipo _Java_ especial usado para definir coleções de constantes. Mais precisamente, um tipo de enum Java é um tipo especial de classe Java. Um enum pode conter constantes, métodos etc. Os enums Java foram adicionados em Java 5.

Será feito no formato exemplo, atribuição e ao final o código completo:

## Exemplo Enum e sua implementação:

```
// Enum Level
package Enums;  
  
public enum Level {  
    HIGH,  
    MEDIUM,  
    LOW  
}


// classe RunEnum
package Enums;  
  
public class RunEnum {  
    public static void main(String[] args){  
        Level level = Level.HIGH;  
    }  
}
```

Observe o `enum`palavra-chave que é usada no lugar de `class` ou `interface`. O Java `enum`sinais de palavra-chave para o compilador Java que esta definição de tipo é um enum.

Você pode se referir às constantes no enum acima como a instanciação de um objeto com o tipo dele (nesse caso Level) o nome da variável e depois a atribuição seria o objeto.valor

## Enums em if

Como os enums Java são constantes, muitas vezes você terá que comparar uma variável apontando para uma constante de enum contra as constantes possíveis no tipo enum. Aqui está um exemplo de uso de um enum Java em um `if`:

```
package Enums;  
  
public class RunEnum {  
    public static void main(String[] args){  
        Level level = Level.HIGH;  
  
  
        if(  level == level.HIGH) {  
            System.out.println("Seu nível é alto");  
        } else if( level == Level.MEDIUM) {  
            System.out.println("Seu nível é médio");  
        } else if( level == level.LOW) {  
            System.out.println("Seu nível é baixo");  
        }  
    }  
}

// output: Seu nível é alto
```

Este código compara o `level`(variável) contra cada um dos possíveis constantes enum no `Level`enum.

Se um dos valores do enum ocorrer com mais frequência do que os outros, verificando esse valor no primeiro `if`-declaração resultará em melhor desempenho, como menos comparação em média são executadas. Mas esta não é uma grande diferença, a menos que as comparações são executadas muito.

## Enums em declarações de switch

Se os seus tipos de enum Java contiverem muitas constantes e você precisar verificar uma variável contra o valores como mostrado na seção anterior, usando um Java `switch`declaração pode Seja uma boa ideia.

Você pode usar enums em declarações de switch como esta:

```
public class RunEnum {  
    public static void main(String[] args){  
        Level level = Level.HIGH;  
    
		switch (level){  
		    case HIGH:  System.out.println("Seu nível é alto");  
		                break;  
		    case MEDIUM: System.out.println("Seu nível é médio");  
		                break;  
		    case LOW:   System.out.println("Seu nível é baixo");  
		                break;  
                  
		}
	}
}

// output: Seu nível é alto
```

Substituindo os if - else com o código a executar se o `level`variável corresponde ao valor constante de Nível dado. O código pode ser uma operação Java simples, a chamada de método etc.

## For loop com Enum

Você pode obter uma matriz de todos os valores possíveis de um tipo de enum Java chamando sua estática `values()`método. Todos os tipos de enum obtêm uma estática `values()`método automaticamente pelo compilador Java. Aqui está um exemplo de iterar todos os valores de um enum:

```
for(Level level1 : Level.values()){  
    System.out.println(level1);  
}

// output: 
HIGH
MEDIUM
LOW
```

Nota-se que desta maneira deve se criar uma nova variável dentro do for loop (Level level1)

## Enums método toString()

Uma classe enum automaticamente recebe o método `toString()` na classe quando compilado. O `toString()` retorna um valor de string do nome da instância de enum dada. Aqui está um exemplo:

```
String levelHighText = Level.HIGH.toString();
```


## Valor do enumof()

Uma classe enum automaticamente recebe um método estático `valueOf()` na classe quando compilado. O método `valueOf()` pode ser usado para obter uma instância da classe enum para um determinado valor String. Aqui está um exemplo:

```
Level level2 = Level.valueOf("HIGH");
```

após essa implementação a variável level2 ira apontar para Level.HIGH

## Campos Enum - valores

Você pode adicionar campos a um enum Java. Assim, cada valor de enum constante obtém esses campos. Os valores de campo devem ser fornecidos ao construtor do enum ao definir as constantes. Modificamos nosso enum para:

```
package Enums

public enum Level {
    HIGH  (3), 
    MEDIUM(2),  
    LOW   (1)   
    ; // semicolon needed when fields / methods follow


    private final int levelCode;

    private Level(int levelCode) {
        this.levelCode = levelCode;
    }
}
```

Observe como o enum no exemplo acima tem um construtor que leva um `int`. O construtor de enum define o `int`. Quando os valores constantes do enum são definidos, um valor `int` é passado para o construtor de enum.

O construtor do `enum` deve ser `private`. Você não pode usar `public` ou `protected` para um  `enum`. Se você não especificar um modificador de acesso o construtor do `enum` será implicitamente `private`.

## Métodos Enum

É possível adicionar métodos a um enum também, por exemplo:

```
package Enums;  
  
public enum Level {  
    HIGH  (3),  
    MEDIUM(2),  
    LOW   (1);  
  
  
    private final int levelCode;  
  
    private Level(int levelCode) {  
        this.levelCode = levelCode;  
    }  
      
    public int getLevelCode(){  
        return this.levelCode;  
    }  
}
```

Você chama um método enum através de uma referência a um dos valores constantes. Aqui está o exemplo de chamada de método  enum:

```
System.out.println(level.getLevelCode());
```

O output será 3 (porque está variável é Level.HIGH com o valor constante de 3).

Os métodos não estão restritos a métodos simples de get e set. Você também pode criar métodos que fazem cálculos baseados nos valores de campo da constante do enum. Se seus campos não forem declarados `final`você pode até modificar os valores dos campos (embora isso possa não ser uma ideia tão boa, considerando que o suposto é enums serem constantes).

## Métodos abstratos

É possível que uma classe de enum tenha métodos abstratos também. Se uma classe enum tem um método abstrato, então cada instância da classe enum deve implementá-la. Aqui está um exemplo de método abstrato de enum:

```
package Enums;  
  
public enum LevelTwo {  
        HIGH{  
            @Override  
            public String asLowerCase() {  
                return HIGH.toString().toLowerCase();  
            }  
        },  
        MEDIUM{  
            @Override  
            public String asLowerCase() {  
                return MEDIUM.toString().toLowerCase();  
            }  
        },  
        LOW{  
            @Override  
            public String asLowerCase() {  
                return LOW.toString().toLowerCase();  
            }  
        };  
  
        public abstract String asLowerCase();  
    }
```

Observe a declaração do método abstrato na parte inferior da classe enum. Observe também como cada instância do enum (cada constante) define sua própria implementação deste método abstrato. Usar um método abstrato é útil quando você precisa de uma implementação diferente de um método para cada instância de um enum.

## Enum interface

Um `Enum`pode implementar uma [Interface Java](https://jenkov.com/tutorials/java/interfaces.html) no caso de você sentir que faz sentido na sua situação. Aqui está um exemplo de um `Enum`implementação de uma interface:

```
package Enums;  
  
public enum EnumImplementingInterface implements MyInterface{  
  
    FIRST("First Value"), SECOND("Second Value");  
  
  
    private String description = null;  
  
    private EnumImplementingInterface(String desc){  
        this.description = desc;  
    }  
  
    @Override  
    public String getDescription() {  
        return this.description;  
    }  
}
```

É o método `getDescription()`que vem da interface `MyInterface`.

Implementação de uma interface com um `Enum`poderia ser usado para implementar um conjunto de diferentes `Comparator`constantes que podem ser usadas para classificar coleções de objetos. Classificação de objetos em Java é explicado mais detalhadamente no [Tutorial de Classificação](https://jenkov.com/java-collections/sorting.html) de [Coleção Java](https://jenkov.com/java-collections/sorting.html).

## Enum Set 

Java contém uma implementação especial [do Java Set](https://jenkov.com/java-collections/set.html) chamada `EnumSet`que pode segurar enums mais eficientemente do que as implementações padrão do Java Set. Aqui está como você cria uma instância de uma `EnumSet`:

```
EnumSet<Level> enumSet = EnumSet.of(Level.HIGH, Level.MEDIUM);
```

Uma vez criado, você pode usar o `EnumSet`assim como qualquer outro Conjunto.

## Enum Map

O Java também contém uma implementação especial [do Java Map](https://jenkov.com/java-collection/map.html) que pode usar instâncias enum como chaves. Aqui está um `EnumMap`exemplo:

```
EnumMap<Level, String> enumMap = new EnumMap<Level, String>(Level.class);
enumMap.put(Level.HIGH  , "High level");
enumMap.put(Level.MEDIUM, "Medium level");
enumMap.put(Level.LOW   , "Low level");

String levelValue = enumMap.get(Level.HIGH);
```