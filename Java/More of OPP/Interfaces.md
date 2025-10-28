
Em Java, uma interface é um tipo abstrato que contém uma coleção de métodos e variáveis constantes. É um dos conceitos centrais em Java e é **usado para alcançar a abstração, polimorfismo e heranças múltiplas.

## Regras para uso de interfaces:

Em uma interface, podemos usar:
- [constantes variáveis](https://www.baeldung.com/java-final)
- [métodos abstractos](https://www.baeldung.com/java-abstract-class)
- [métodos estáticos](https://www.baeldung.com/java-static-default-methods)
- [métodos padrão](https://www.baeldung.com/java-static-default-methods)

Também devemos lembrar que:

- não podemos instanciar interfaces diretamente
- uma interface pode estar vazia, sem métodos ou variáveis nele
- não podemos usar a palavra final na definição da interface, pois resultará em um erro de compilador
- todas as declarações de interface devem ter o modificador de acesso público ou padrão; o modificador de resumo será adicionado automaticamente pelo compilador
- um método de interface não pode ser protegido ou final
- até que os métodos de interface Java 9 não pudessem ser private_privados; no entanto, o Java 9 introduziu a possibilidade de definir [métodos privados em interfaces](https://www.baeldung.com/java-interface-private-methods)
- variáveis de interface são públicas, estáticas e finais por definição; não temos permissão para alterar sua visibilidade

Agora a implementação feita para usar como exemplo e explicação de uso das interfaces:

```
package Interfaces;  
  
public interface Comparator {  
    public void Compare(Employee employeeA, Employee employeeB);  
}
```

primeiro é criado uma interface chamada de Comparator com o uso da palavra interface (quase igual a criação de uma classe) onde esta possui apenas um método Compare() que espera duas variáveis employeeA e emplyeeB (ambos objetos da classe Employee) - exemplo da classe employee (usando o conceito de encapsulamento):

```
package Interfaces;  
  
public class Employee {  
     private double Salary;  
     private String Name;  
     private int Id;  
  
     public Employee(){  
  
     }  
  
     public Employee(double salary, String name, int id){  
         this.Id = id;  
         this.Name = name;  
         this.Salary = salary;  
     }  
  
     public double getSalary(){  
         return this.Salary;  
     }  
     public String getName(){  
         return this.Name;  
     }  
     public int getId(){  
         return this.Id;  
     }  
  
    public void setId(int id) {  
        this.Id = id;  
    }  
  
    public void setName(String name) {  
        this.Name = name;  
    }  
  
    public void setSalary(double salary) {  
        this.Salary = salary;  
    }  
}
```

Podemos ver que a classe employee possui suas variáveis privadas, fazendo com que elas possam ser acessadas somente pela classe e seus métodos (utilizamos get() e set() para acessar esses valores) - focaremos na variável double Salary e seus métodos getSalary() e setSalary() porque iremos utilizar isso, além dos outros métodos de nome, na nossa próxima classe que ira implementar a nossa interface:

```
package Interfaces;  
  
public class EmployeeSalaryComparator implements Comparator{  
  
    public EmployeeSalaryComparator(){ }  
  
    @Override  
    public void Compare(Employee employeeA, Employee employeeB) {  
        if(employeeA.getSalary() > employeeB.getSalary()){  
            System.out.println("O salario de "+ employeeA.getName() + " é de R$" + employeeA.getSalary()+" e é maior que o sálario do "  
                    + employeeB.getName() + ", com uma diferença de: " + (employeeA.getSalary() - employeeB.getSalary()));  
        } else if(employeeB.getSalary() > employeeA.getSalary()){  
            System.out.println("O salario de "+ employeeB.getName() + " é de R$ " + employeeB.getSalary()+" e é maior que o sálario do "  
                    + employeeA.getName() + ", com uma diferença de: " + (employeeB.getSalary() - employeeA.getSalary()));  
        }else {  
            System.out.println("Ambos ganham o mesmo sálario de: " + employeeA.getSalary());  
        }  
    }  
}
```

Implementamos o método Compare da nossa interface comparator nesta nossa classe EmployeeSalaryComparator primeiramente usando a palavra reservada imlpements para indicar qual interface a nossa classe ira implementar e depois usamos o @Override e o mesmo método da interface, mas agora decidimos o que irá ser feito com os dois valores passados.

Como podemos visualizar ao longo desta implementação, é pego o sálario do primeiro e comparado com o segundo, visto qual é maior e retornado a frase para output dizendo o nome, o salário e a diferença entre os salários. Iremos ver melhor agora a saída e utilização final na classe para rodar tudo isso:

```
package Interfaces;  
  
public class RunInterface {  
    public static void main(String[] args){  
        Employee a = new Employee(3655,"Lucas", 1  );  
        Employee b = new Employee(3000, "Paulo", 2);  
  
        EmployeeSalaryComparator compare = new EmployeeSalaryComparator();  
        compare.Compare(a,b);  
    }  
}
```

Em nossa classe RunInterface instanciamos dois objetos Emplyee, sendo eles a e b, além de instanciar também a classe EmployeeSalaryComparator com a variável compare, quando utilizados o método Compare() que foi implementado nesta classe da interface Comparator e sua saída ficará desta maneira:

```
O salario de Lucas é de R$3655.0 e é maior que o sálario do Paulo, com uma diferença de: 655.0
```
