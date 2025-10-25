
Ela define limitações ou extensibilidade 

#### Final Classes

Classes marcadas como final não podem ser estendidas ( usando o extends), um dos principais exemplos é por exemplo a classe String.

Considerando a seguinte situação: e pudermos estender a classe _String_, substituir qualquer um de seus métodos e substituir todas as _String_instâncias de _String_ pelas instâncias de nossa subclasse de _String_ específica.

O resultado das operações sobre objetos _String_ se tornará imprevisível. E dado que a classe _String_ é usada em todos os lugares, é inaceitável. É por isso que a classe _String_ é marcada como _final_.

exemplo no código:

```
public final class House{
	public int rooms;
}
```
Tentando extender
```
public class Garden exteds House{

}
```

Ao compilar o código virá o seguinte erro: "The type Garden cannot subclass the final class House"

Isso não quer dizer que  ao usarmos final em uma declaração de classe os objetos desta classe também serão imutáveis. É possível modificar o campo do objeto House livremente como:

```
House house = new House();
house.setrooms(3);

assertEquals(3, house.getrooms());

```

