	Facilitam a modelagem de dados imutáveis
	São essencialmente classes finais (final)
	Atributos finais (final)

Fornece implementações dos métodos
	Equals
	Hascode
	toString

Exemplo de código Record:

```
package Records;  
  
public record Retangulo(double largura, double altura) {  
  
    public Retangulo{  
        if (largura <= 0 || altura <= 0){  
            throw new IllegalArgumentException();  
        }  
  
    }  
        public double area(){  
            return largura * altura;  
        }  
  
        public double perimetro(){  
            return 2 * (altura + largura);  
        }  
  
        public static Retangulo Retanguloquadrado(double lado){  
            return new Retangulo(lado, lado);  
        }  
}
```

Nele, utilizamos a palavras reservada record e montamos como se fosse uma classe, a única diferença é que records possuem apenas dados e variáveis imutáveis o contrutor da classe record deve ser implementada em sua declaração e não em um construtor dentro do record como nas classes normais.

Nesse nosso record Retangulo temos uma largura e uma altura (ambos do tipo double) e no seu corpo monstamos métodos de regra como apenas o "public Retangulo" - utilizamos apenas o nome do record para isso e abrimos as chaves para montar. Também montamos um métodos estático do tipo Retangulo, fazendo assim devemos retornar um Retangulo também, nesse caso o nome do método é "Retanguloquadrado" e ele recebe apenas um lado e cria um novo retangulo com altura e largura referentes a esse lado (Retangulos quadrados possuem os lados iguais)

Implementando esse record temos em nossa classe RunRecord que também é nosso main, o seguinte código:

```
package Records;  
  
public class RunRecord {  
    public static void main(String[] args){  
        Retangulo retangulo = new Retangulo(5.0, 3.0);  
  
        System.out.println("Altura: " + retangulo.altura());  
        System.out.println("Largura: " + retangulo.largura());  
        System.out.println("Area: " + retangulo.area());  
        System.out.println("Perimetro: " + retangulo.perimetro());  
  
        System.out.println(retangulo.toString());  
  
        Retangulo Quadrado = Retangulo.Retanguloquadrado(5.0);  
        System.out.println("Area: " + Quadrado.area());  
    }  
}
```

```
// Output do código acima: 

Altura: 3.0
Largura: 5.0
Area: 15.0
Perimetro: 16.0
Retangulo[largura=5.0, altura=3.0]
Area: 25.0

```

Limitações
	Herença
		Records não podem ser estendidos (não pode se usar herança)
	Campos mutáveis (impossível, todos devem ser imutáveis) 