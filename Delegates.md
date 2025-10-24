Delegates em C# são tipos que representam referências a métodos, permitindo armazenar, passar e invocar métodos como variáveis, com assinatura e retorno específicos

-- Delegate é uma forma de atribuir um método a uma variável.

EX:

método calcular

public void Calcular(){
	Soma somar = calculadoreQueSoma;

	 int valor Somado = somar(5,10);
}

delegate calculadora

delegate int Soma(int a, int b);

int CalculadoraQueSoma(int a, int b){
	return  a + b;
}

delegates padrões 

Func<int, int, int>

genérico que retorna um valor, os dois primeiros parâmetros tem que ser do mesmo tipo do métodos que a variável vai referenciar e o ultimo parâmetro é o retorno

Actions são Func que não retorna um valor

Action< int >