Classes abstract e Método abstract

Classes abstratas não podem ser implementadas na classe main por serem abstratas - elas só servem para serem "Pais" das outras classes por exemplo a classe Animal:

```
package Abstract;  
  
public abstract class Animal {  
  
    String Name;  
  
    public Animal(String name){  
        this.Name = name;  
    }  
  
    public abstract void FazerSom(); // não precisa implementar - quem herda que implementa  
    public void dormir(){  
        System.out.println( Name + " está domindo");  
    }  
}
```

Utilizamos a palavra reservada abstract na classe Animal e no método FazerSom() - visto que este método por ser abstrato, ele não recebe implementação alguma na classe principal e sim nas que herdam dele por exemplo as classes Dog e Cat:

```
package Abstract;  
  
public class Cat extends Animal{  
  
  
    public Cat(String name) {  
        super(name);  
    }  
  
    @Override  
    public void FazerSom() {  
        System.out.println("Miau");  
    }  
}
```

```
package Abstract;  
  
public class Dog extends Animal{  
  
    public Dog(String name) {  
        super(name);  
    }  
  
    @Override  
    public void FazerSom() {  
        System.out.println("Au AU");  
    }  
}
```

Utilizando a palavra @Override sobre-ecrevemos o método FazerSom da classe principal (herdamos com o extends no inicio da classe "public class "nome da classe" extends "nome da classe herdada".") e podemos fazer com que esta classe implemente qualquer coisa para cada uma das classe, pois depois ao inicializarmos elas na main - farão coisas diferentes, mesmo tendo o mesmo nome (mas estarão em variáveis de objeto diferentes) exemplo na classe main:

```
package Abstract;  
  
public class Main {  
    public static void main(String[] args) {  
        Dog c1 = new Dog("Hex");  
  
        c1.FazerSom();  
        c1.dormir();  
  
        Cat c2 = new Cat("Suq");  
  
        c2.FazerSom();  
        c2.dormir();  
    }  
}
```

Instanciadas as variáveis c1 e c2 das classes Dog e Cat ambas terão output diferentes (terão o que foi implementado dentro de suas classe)

```
// OUTPUT DA MAIN

Au AU
Hex está domindo
Miau
Suq está domindo

```
