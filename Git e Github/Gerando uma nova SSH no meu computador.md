
comando para gerar uma nova SSH para o Github no mac 

```shell
ssh-keygen -t ed25519 -C "your_email@example.com"
```

Coloquei o arquivo em /Users/lucasschwartzdesouza/ssh - fazendo assim deu certo, apenas dando enter sem colocar nada não criou o arquivo na pasta do meu usuário

No meu deu ruim, segui estes passos:

1. verificar se existe uma chave SSh
	ls -al ~/.ssh
2. Criar uma nova chave SSh caso não tenha
	ssh-keygen -t ed25519 -C "seu-email-do-github"
3. Adicionar a chave ao ssh-agent
	eval "$(ssh-agent -s)"
	ssh-add ~/.ssh/id_ed25519
4. Copiar a chave publica 
	pbcopy < ~/.ssh/id_ed25519.pub
5. Teste a conexão
	ssh -T git@github.com
	