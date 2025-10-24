um modificador de acesso em java especifica qual das classes consegue acessar uma dada classe e seus métodos / campos

![[Pasted image 20251023210138.png]]


Private
Exemplo de código e explicação

public class Clock {
	private double time = 10;
}

isso quer dizer que a variável time que é do tipo double só poderá ser acessada pelo código que esta dentro da classe Clock, fazendo assim com que todo o código fora disso não possa acessar esta variável

um Construtor privado não pode ser instanciado ou chamado em qualquer outro lugar do projeto / código a não ser dentro da sua própria classe. Ele consegue ainda sim ser chamado por outro construtor dentro da própria classe ou por métodos estáticos (static...), um exemplo:

```
class MinhaClasse{
	private String name = "Joao";
	
	private MinhaClasse(String name){
		this.name = name;
	}
	public MinhaClasee(String name, String sobrenome){
		this(name);
		this.name += sobrenome;
	}
	public static MinhaClasse novoNome(){
		return new MinhaClasse("Lucas");
	}
}
```

essa versão da MinhaClasse contem um construtor privado e um publico. O construtor privado é chamado pelo publico (declarando o "this()"), o construtor privado também é chamado pelo método estático novoNome()


Default

Em Java, o modificador de acesso padrão (ou

_default_) é aplicado quando nenhum outro modificador (`public`, `protected` ou `private`) é especificado explicitamente para uma classe, método, ou atributo. Ele também é chamado de _package-private_ (privado de pacote). 

Características do modificador `default`

- **Ausência de palavra-chave:** Não há uma palavra-chave para o modificador `default`. Você o usa simplesmente omitindo os outros modificadores de acesso.
- **Visibilidade restrita:** A visibilidade de um membro com acesso `default` se restringe às classes que pertencem ao mesmo pacote.
- **Uso:** É útil para encapsular componentes internos de um pacote que não precisam ser acessados por classes de fora, mas que precisam ser compartilhados entre as classes que o compõem.

Exemplo
```
// Arquivo: meupacote/MinhaClasse.java
package meupacote;

public class MinhaClasse {
    // Membro com acesso default (package-private)
    String atributoDefault = "Acesso apenas no mesmo pacote";

    // Método com acesso default
    void metodoDefault() {
        System.out.println("Método com acesso default.");
    }
}


// Arquivo: outro_pacote/ClasseFora.java
package outro_pacote;

import meupacote.MinhaClasse;

public class ClasseFora {
    public void testarAcesso() {
        MinhaClasse obj = new MinhaClasse();
        // Erro de compilação!
        // System.out.println(obj.atributoDefault); // Acesso negado
        // obj.metodoDefault(); // Acesso negado
    }
}

```

protected

O modificador de acesso

`protected` em Java permite que membros (variáveis, métodos ou construtores) de uma superclasse sejam acessíveis por: 

- Qualquer classe dentro do **mesmo pacote**.
- **Subclasses**, mesmo que estejam em um **pacote diferente**. 

Essa visibilidade é mais ampla que a de um membro `default` (sem modificador) e mais restritiva que a de um membro `public`. É útil para expor detalhes de implementação para classes filhas, mas mantê-los ocultos do "mundo exterior" do código.

Acesso por: 

||Mesma Classe|Mesmo Pacote|Subclasse (pacote diferente)|Outra Classe (pacote diferente)|
|**`protected`**|Sim|Sim|Sim|Não|

public

publico 