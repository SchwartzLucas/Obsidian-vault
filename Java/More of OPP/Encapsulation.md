Se tem por encapsulação a omissão dos dados de uma classe para as outras, fazendo com que seus dados possam serem somente acessados pela própria classe, com a utilização de seus métodos (os famosos get() e set()) olhando o exemplo a seguir:

```
package Encapsulation;  
  
public class EncapTest {  
    private String name;  
    private String idNum;  
    private int age;  
  
    public int getAge() {  
        return age;  
    }  
  
    public String getName() {  
        return name;  
    }  
  
    public String getIdNum() {  
        return idNum;  
    }  
  
    public void setAge( int newAge) {  
        this.age = newAge;  
    }  
  
    public void setName(String newName) {  
        this.name = newName;  
    }  
  
    public void setIdNum( String newId) {  
        idNum = newId;  
    }  
  
    public void AllNameAndId(){  
        System.out.println("Name : " + getName() + " Age : " + getAge() + " Id : " + getIdNum());  
    }  
}
```

Os métodos setXXX() e getXXX() públicos são os pontos de acesso das variáveis de instância da classe EncapTest. Normalmente, esses métodos são referidos como getters e setters. Portanto, qualquer classe que queira acessar as variáveis deve acessá-las através desses getters e setters.

As variáveis da classe EncapTest podem ser acessadas usando o seguinte programa:

```
package Encapsulation;  
  
  
public class RunEncap {  
  
    public static void main(String args[]) {  
        EncapTest encap = new EncapTest();  
        encap.setName("James");  
        encap.setAge(20);  
        encap.setIdNum("12343ms");  
  
        encap.AllNameAndId();  
    }  
}
```

O output deste código fica desta maneira:
```
Name : James Age : 20Id : 12343ms
```

Benefícios sobre o encapsulamento:

- Os campos de uma classe podem ser feitos apenas para leitura ou apenas para escrever.
    
- Uma classe pode ter controle total sobre o que está armazenado em seus campos.

Quando falamos de classes de apenas leitura (Read Only) são classes que possuem apenas métodos setters ( setXXX() ) ou de apenas gravação (Write Only) são classe que possuem apenas métodos getters ( getXXX() ).