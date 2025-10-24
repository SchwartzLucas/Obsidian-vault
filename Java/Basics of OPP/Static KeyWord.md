
Por exemplo, temos o código a seguir:

```
public class Classe{
	public static int count = 0;
	
	Classe(){
		count++;
	}
}
```

desse modo, a variável estática count será compartilhada por toda a minha classe
Quando criamos os objetos da nossa classe Classe na Main, acessamos a variável estática:

```
public class MinhaClasse{
	public static void Main(String[] args){
		Classe c1 = new Classe();
		
		System.out.printl(Classe.count)
		// o output será 1		
		
		Classe c2 = new Classe();
		
		System.out.printl(Classe.count)
		// output será 2
	}
}
```

O output será 2 ou 1 porque a variável count é estática e é incrementado por um a cada vez que um novo objeto da classe Classe é criado. Também é possível acessar a variável estática usando qualquer objeto desta classe, como o c1 ou o c2 com c1.count e c2.count

# **Métodos Estáticos**

Quando usamos um método estático, ele pertence a classe em vez das instâncias. Desse modo, pode ser chamado sem criar instâncias de classe. É usado para alterar o conteúdo estático da classe. 

Restrições:

1. Métodos estáticos não podem usar membros não estáticos (non-static) - variáveis ou funções da classe
2. Métodos estáticos não podem usar as palavras-chave this ou super

Ex:

```
public class Classe{
	public static int count = 0;
	
	Classe(){
		count++;
	}
	
	public static void increment(){
		count++
	}
}
```

Métodos estáticos também podem ser chamados de instância da classe

```
public class MinhaClasse{
	public static void Main(String[] args){
		
		Classe.increment();
		Classe.increment();
		
		System.out.printl(Classe.count)
		// output será 2
	}
}
```

O output será 2, porque é incrementada pelo método estático increment(). Semelhante às variáveis estáticas, os métodos estáticos também podem ser acessados usando variáveis de instância.

# **Blocos Estáticos**

São blocos de código usados para inicializar variáveis estáticas. Esses blocos são executados imediatamente após a declaração de variáveis estáticas.

Ex:

```
public class Earth{
	public static final int moon_counter;
	
	static{
		moon_counter = 1;
	}
}
```

```
public class Main{
	public static void Main(String[] args){
		System.out.println(Earth.moon_counter);
		
		// output sera 1
	}
}
```

O output será 1 porque a variável moon_counter é atribuído esse valor no bloco static na classe Earth.

# **Static Nested Classes (Classes estáticas aninhadas)**

Uma classe pode possuir classe aninhada estática que pode ser acessada usando o nome da classe externa.

Ex:

```
public class Outer{
	
	public Outer(){
	
	}
	
	public static class Inner{
		
		public Inner(){
		
		}
	}
}
```

Neste exemplo a classe Inner pode ser acessada diretamente como um membro estático da classe Outer desta maneira:

```
public class Main {
	public static void main(String[] args){
		Outer.Inner inner = new Outer.Inner();
	}
}
```

Popularmente usado em java.
