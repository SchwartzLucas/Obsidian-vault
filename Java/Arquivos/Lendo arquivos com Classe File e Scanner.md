
utilizando os imports  java.io.File e  java.util.Scanner conseguimos acessar um arquivo dentro do computador passando um caminho e ler o conteúdo dele. Precisamos instanciar um Objeto FIle e passar nele o Path (caminho) para o nosso arquivo e depois com o Scanner conseguimos ler este arquivo, da seguinte maneira: 

```
import java.io.File;  
import java.io.IOException;  
import java.util.Scanner;  
import java.io.FileNotFoundException;  
  
public class Main {  
    public static void main(String[] args) {  
        File file = new File("/Users/lucasschwartzdesouza/Documents/teste.txt");  
        Scanner sc = null;  
        try {  
            sc = new Scanner(file);  
            while (sc.hasNextLine()){  
                System.out.println(sc.nextLine());  
            }  
        } catch (IOException e) {  
			System.out.println("Error: " + e.getMessage());
        }finally {  
            if (sc == null) {  
                sc.close();  
            }  
        }  
    }  
    }
```

Estamos usando a estrutura try catch e finally por boas práticas para pegar erro e fechar o nosso Scanner corretamente mesmo que acontece algum erro e ele não tenha sido iniciado (conteúdo dele seja null). 

Lemos o conteúdo do arquivo teste.txt usando o bloco while(sc.hasNextLine()) para ler as linhas do nosso arquivo.