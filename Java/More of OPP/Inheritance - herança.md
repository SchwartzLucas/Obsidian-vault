
Herança é herdar todo ou o que você quiser de outra classe (superclasse)

no código fica mais ou menos assim:

classe "pai":

```
package inheritance;  
  
public class Animal {  
  
    private boolean Mamifero;  
    private  String Eats;  
    private  int NumberOfLegs;  
  
    public Animal(){  
  
    }  
  
    public Animal(boolean mamifero, String eats, int numberOfLegs){  
        this.Mamifero = mamifero;  
        this.Eats = eats;  
        this.NumberOfLegs = numberOfLegs;  
    }  
  
    public boolean isMamifero(){  
        return Mamifero;  
    }  
  
    public void setMamifero(boolean mamifero){  
        this.Mamifero = mamifero;  
    }  
  
    public String getEats(){  
        return Eats;  
    }  
  
    public void setEats(String eatWhat){  
        this.Eats = eatWhat;  
    }  
  
    public int getNumberOfLegs(){  
        return NumberOfLegs;  
    }  
  
    public void setNumberOfLegs(int numberOfLegs){  
        this.NumberOfLegs = numberOfLegs;  
    }  
  
}
```

classe "Filho" que herda da classe pai usando "extends" e nos construtores passando os valores (como as variáveis são todas privatas, métodos de get e set devem ser feitos para conseguir acessar e modificar as variáveis):

```
package inheritance;  
  
public class Dog extends Animal{  
    private String Color;  
    private String Name;  
  
    public Dog(boolean mamifero, String whatEat, int numberofLegs){  
            super(mamifero, whatEat, numberofLegs);  
            this.Color = "Black";  
            this.Name = "Bolt";  
    }  
  
    public Dog(boolean mamifero, String whatEat, int numberofLegs, String color, String name) {  
            super(mamifero, whatEat, numberofLegs);  
            this.Color = color;  
            this.Name = name;  
    }  
  
    public String getColor(){  
        return Color;  
    }  
  
    public void setColor(String color){  
        this.Color = color;  
    }  
  
    public String getName(){  
        return Name;  
    }  
  
    public void setName(String name){  
        this.Name = name;  
    }  
}
```


podemos ver que a classe Dog herda da classe Animal, possuindo ainda mais complementos como nome e cor da própria classe. Para testarmos podemos usar o programa main:

```
package inheritance;  
  
import java.util.Scanner;  
  
public class TestInheritance {  
    public static void main(String[] args){  
  
        Scanner sc = new Scanner(System.in);  
        Dog dog = new Dog(true, "ração", 4, "white", "Bethoven");  
        dog.setMamifero(false);  
  
        System.out.println("Your dog " + dog.getName() + " is an mamifero? \n" + (dog.isMamifero() ? "YES" : "NO"));  
        System.out.println("What your dog eats? ");  
        String WhatMyDogEats = sc.nextLine();  
        dog.setEats(WhatMyDogEats);  
        System.out.println("My dog eat: " + dog.getEats());  
        System.out.println("And his color is: " + dog.getColor());  
  
        sc.close();  
    }  
}
```

desse jeito eu instanciei um objeto Dog que herda "características" da classe Animal (variáveis e métodos dela) e as uso como precisar