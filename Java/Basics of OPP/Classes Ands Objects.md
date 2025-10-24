Basics -- uma classe pode ter tudo e você acessa ela no main ou seja onde for (provavelmente utilizando um import se for em passas / namespace diferentes) e então declara uma variável para aquela classe como a classe MinhaClasse será declarada como:

MinhaClasse variável = new MinhaClasse("construtores se houver algum na classe");

dessa maneira sera criado uma variavel daquela classe, podendo assim acessar os métodos e valores dela, além de poder modificá-los ou adicionar novos dependendo de como foi implementada a classe ou os métodos


General form

class classname {
	//  instance variables


	// methods


	// contructor
}

public class caracher {  
  
    String name;  
    int level;  
  
    caracher(){  
        level = 1;  
    }  
      
      
    caracher(String pname, int plevel){  
        this.name = pname;  
        this.level = plevel;  
    }  
  
    void attack(){  
        System.out.println(name + "Attack");  
    }  
}