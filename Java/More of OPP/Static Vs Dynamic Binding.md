
Em **Java**, _binding_ (ou **vinculação**) é o processo de associar uma **chamada de método** com o **código que deve ser executado**.

Existem dois tipos principais: **static binding** (vinculação estática) e **dynamic binding** (vinculação dinâmica).

Diferenças:

### **Static Binding (Vinculação Estática)**

- Também chamada de **early binding** (_vinculação antecipada_).
    
- Acontece **em tempo de compilação**.
    
- O compilador já sabe **qual método será chamado**.
    
- Ocorre com:
    
    - **métodos static**
        
    - **métodos final**
        
    - **métodos private**
        
    - **atributos (variáveis)**

Exemplo: 

```
class Animal {
    static void som() {
        System.out.println("Som genérico de animal");
    }
}
```

```
class Dog extends Animal {
    static void som() {
        System.out.println("Latido");
    }
}
```

```
public class Main {
    public static void main(String[] args) {
        Animal a = new Dog();
        a.som(); // Saída: Som genérico de animal
    }
}
```

Nota-se que mesmo que a seja um Cachorro, o método chamado é o da **classe Animal**,
porque o método som() é **estático** — a escolha é feita **em tempo de compilação**.

### **Dynamic Binding (Vinculação Dinâmica)**

- Também chamada de **late binding** (_vinculação tardia_).
    
- Acontece **em tempo de execução**.
    
- O Java decide **qual método chamar com base no objeto real**, não na referência.
    
- Ocorre com **métodos de instância sobrescritos** (overridden).

Exemplo:

```
class Animal {
    void som() {
        System.out.println("Som genérico de animal");
    }
}
```

```
class Cachorro extends Animal {
    @Override
    void som() {
        System.out.println("Latido");
    }
}
```

```
public class Main {
    public static void main(String[] args) {
        Animal a = new Cachorro();
        a.som(); // Saída: Latido
    }
}
```

Aqui, mesmo que a seja uma variável do tipo Animal, o método chamado é o da **classe Cachorro**, porque o **objeto real** é um Cachorro. A decisão ocorre **em tempo de execução** → _dynamic binding_.

Em resumo:

|**Tipo de Binding**|**Quando ocorre**|**Com o que ocorre**|**Exemplo típico**|
|---|---|---|---|
|**Static Binding**|Tempo de compilação|static, final, private, atributos|a.som() (método static)|
|**Dynamic Binding**|Tempo de execução|Métodos sobrescritos (overriding)|a.som() (método instância)|