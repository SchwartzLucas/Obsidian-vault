
Nada mais é que o encadeamento de métodos em uma variável ou um objeto, por exemplo:

```
package MethodChaining;  
  
public class main {  
    public static void main(String[] args){  
  
        String name = "Lucas";  
  
        name = (name.concat(" Schwartz").toUpperCase());  
  
        System.out.println(name);  
    }  
  
}
```

Na variável "name" do tipo String estamos usando os métodos concat() e toUpperCase() para concatenar e colocar as letras para maiúsculo, isso é method chaining. Isso poderia ser escrito sem encadeamento e ficaria da seguinte maneira:

```
package MethodChaining;  
  
public class main {  
    public static void main(String[] args){  
  
        String name = "Lucas";  
  
        name = name.concat(" Schwartz";
        name = name.toUpperCase();  
  
        System.out.println(name);  
    }  
  
}
```

o resultado é o mesmo, mas com mais linhas de código. Method chaining é bom para reduzir o número de linhas do código - imagine que fez essas duas alterações e no meio do código lembrou e fez outra, será meio difícil de lembrar de coisas feitas lá em cima quando se já está embaixo, por isso utilizar method chaining, para conseguir fazer tudo em uma só linha / um só lugar.

```
package MethodChaining;  
  
public class Presenting {  
    private String Name;  
    private int Age;  
    private char Gender;  
  
    public Presenting setName(String name){  
        this.Name = name;  
        return  this;  
    }  
  
    public Presenting setAge(int age){  
        this.Age = age;  
        return this;  
    }  
  
    public Presenting setGender(char gender){  
        this.Gender = gender;  
        return this;  
    }  
  
    public void Presenting(){  
        String presenting = "Nome: " + Name + " idade: " + Age +" do genero " + (Gender == 'F' ? "Feminino" : "masculino");  
  
        System.out.println(presenting);  
    }  
}
```

```
package MethodChaining;  
  
public class main {  
    public static void main(String[] args){  
  
        String name = "Lucas";  
  
        name = (name.concat(" Schwartz").toUpperCase());  
  
        System.out.println(name);  
  
        Presenting p1 = new Presenting();  
  
        p1.setName("Lucas").setAge(21).setGender('M');  
  
        p1.Presenting();  
    }  
  
}
```

Utilizando classe e retornando o objeto nos métodos da classe.