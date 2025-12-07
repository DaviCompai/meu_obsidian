---
{"dg-publish":true,"permalink":"/1-bruto/programacao/csharp/projetos/campo-minado/identificando-os-desafios-campo-minado/","created":"2025-11-26T19:15:11.283-03:00","updated":"2025-12-02T22:57:24.815-03:00"}
---

26-11-2025 20:11

Status: beta

Tags: [[1 - Bruto/programação/csharp/projetos/CampoMinado/Campo Minado\|Campo Minado]]
# Identificando os desafios (campo minado)

Minha forma favorita de organizar um programa é apartir dos desafios apresentados pelo mesmo. Dessa forma, consigo separar o código facilmente, sem ficar "perdido" em momento algum.

Acredito que podemos separar este programa em 3 desafios principais:

---
## 1.**Criar o bloco do campo**
Existem infinitas formas de criar os blocos, mas todas elas irão precisar comportar as características dos mesmos.
Essas características são as seguintes:
**O bloco já foi interagido de alguma forma?** (valor booleano)
![](https://raw.githubusercontent.com/DaviCompai/meu_obsidian/imagens/escondido%20(2).png)
**O bloco é uma bomba?** (valor booleano)
![](https://raw.githubusercontent.com/DaviCompai/meu_obsidian/imagens/bomba(2).png)
**Se o bloco não for uma bomba, quantas bombas a ao redor do mesmo?**(valor inteiro)
![](https://raw.githubusercontent.com/DaviCompai/meu_obsidian/imagens/Pastedimage20251126202612.png)
**Se o bloco não for uma bomba e nem foi interagido anteriormente, ele está marcado com uma bandeira?** (valor booleano)
![](https://raw.githubusercontent.com/DaviCompai/meu_obsidian/imagens/bandeira(2).png)

> [!faq]- E a localização?
>Esta pergunta é valida!
>A localização de cada bloco será definida dentro de uma matriz no desafio 2, onde criaremos o campo.

Para armazenar essas informações no nosso programa, podemos utilizar [structs ou classes](https://www.alura.com.br/artigos/c-sharp-entendendo-classes-e-structs).
Pessoalmente acredito que neste caso o uso de structs seja mais adequado. 
> [!Danger]- Erro?
>  Structs e classes [[1 - Bruto/programação/csharp/Structs em Csharp#local dentro do código\|não podem ser declaradas dentro da classe programa/main!]]
>  Além disso, a [[1 - Bruto/programação/csharp/Structs em Csharp#Atenção!\|forma que elas devem ser declaradas]] pode ser diferente em versões mais antigas do csharp
Q
 
 Recomendo que você faça a própria struct e as suas próprias variáveis com os nomes que soam mais intuitivos para você.
Inicialmente, fiz a seguinte struct:
![](https://raw.githubusercontent.com/DaviCompai/meu_obsidian/imagens/IdentificandoOsDesafios1.png)
>[!abstract]- código
>```
>struct Espaco
>{
>    public bool foiInteragido = false
>    public bool eBomba = false;
>    public bool eUmaBandeira = false;
>    public int? bombasAoRedor;
>    // o ponto de interrogação significa "sem valor inicial"
>    public char? simbolo;
>    public Espaco(){} 
>    //sem esta linha, as atribuições não funcionam corretamente
> }
>```



A variável simbolo representa o valor que será mostrado no console quando o campo inteiro for exibido.

Precisaremos escolher simbolos, assim como escolhemos atribuições anteriormente. Para isso, podemos usar caracteres usuais (letras ou simbolos mais comuns,números, etc) ou especiais (chamados de "unicodes"). 
>[!Danger]- Atenção
Em relação aos unicodes, certa cautela é necessária, já que alguns deles não aparecem no console, aparecendo como um "?". 
Alguns deles começam a funcionar com a adição deste comando:
>```Console.OutputEncoding = System.Text.Encoding.UTF8```
>
>Essa informação se torna útil na próxima seção.

---
## 2.**Criar o campo**
O campo ficará dentro de uma matriz dimensional, já que o mesmo tem uma organização completamente compatível com ela.
*[[1 - Bruto/programação/Entendendo matrizes|revisão de matrizes/por que usar neste momento?]]*

Para criar nossa matriz que representará o campo, podemos criar um método (mesmo que uma função)
![](https://raw.githubusercontent.com/DaviCompai/meu_obsidian/imagens/IdentificandoOsDesafios2.png)
>[!abstract]- código
>```
>public static Espaco[,] criarCampo(int numeroDeBombas,int tamanhoX,int tamanhoY)
>{
>	Espaco[,] campo = new Espaco[tamanhoX,tamanhoY];
>	return campo;
>}
>```

esse método cria e retorna uma matriz com a estrutura que representa cada espaço, porém, ele não gera as bombas nem calcula quantas bombas estão presentes ao redor de cada espaço.

>[!FAQ]- Como testo meu método?
>Você pode usar a função disponivel em 2.1, logo abaixo.

Parar gerar as bombas, você ira precisar adicionar algumas linhas que sorteiem campos aleatórios da matriz gerada anteriormente, e que declare o campo booleano relacionado a presença de bombas como verdadeiro.

Para isso, você pode fazer um [loop for](https://www.rocketseat.com.br/blog/artigos/post/csharp-estruturas-de-repeticao-na-pratica) que roda até atingir o número de bombas desejado, com um [[1 - Bruto/programação/csharp/Numeros aleatorios em csharp|gerador de inteiros]] sendo usado para escolher aleatoriamente o X e o Y de cada bomba.

Porém, como faço para testar esse código?
#### 2.1 **Saída para o terminal**
Usaremos um método que percorre por todos os espaços de uma matriz e a imprime no console.

Para isso, podemos usar dois loops for, um dentro do outro:
![](https://raw.githubusercontent.com/DaviCompai/meu_obsidian/imagens/IdentificandoOsDesafios3.png)
>[!abstract]- código
>```
>  public static void imprimir(Espaco[,] campoMinado)
>   {
> 	  for (int y = 0; y < campoMinado.GetLength(1); y++)
>       {
> 	          for (int x = 0; x < campoMinado.GetLength(0); x++)
> 			 {
> 				if (campoMinado[x, y].eBomba)
> 				{
> 				Console.Write("!");
> 				}
> 				else
> 				{
> 				Console.Write("0");
> 				}
> 			 }
> 	   Console.Write("\n");
> 	   }
>  }
>```
(Não usaremos exatamente este método para a versão final do programa: ela tem função de teste.)

campoMinado.GetLenght(V) mostra o tamanho da dimensão V, com X sendo a dimensão 0 e Y sendo a dimensão 1.
Nessa método, nós printamos "!" se um espaço tiver uma bomba e "0" se não, e, quando chegamos ao final da mesma, avançamos para a próxima, até o fim da matriz.
#### 2.2 bombas Ao redor
Para calcular o número de bombas ao redor de um bloco, você irá precisar escanear a variável que represente ser uma bomba em todos os blocos ao redor, e, caso ela seja verdadeira, adicionar 1 ao valor que representa as bombas ao redor.

>[!Danger]- Atenção!
>O código para calcular o número de bombas ao redor só pode ser executado após o campo inteiro ser calculado

Para a primeira parte, você pode usar um código similar a esse:
![](https://raw.githubusercontent.com/DaviCompai/meu_obsidian/imagens/carbon.png)
>[!abstract]- código
> ```
> for (int xAoRedor = xAoRedorMin; xAoRedor <= xAoRedorMax; xAoRedor++)
 >  {
>	for (int yAoRedor = yAoRedorMin; yAoRedor <= yAoRedorMax; yAoRedor++)
>	{
>		//código que você deseja rodar.
>		//irá precisar acessar o campo de alguma forma, usando
>		//xAoRedor e yAoRedor como parametros.
>	}
 >  }
 > ```

Neste código, `xAoRedor` representa a coordenada x do bloco sendo testado atualmente; `xAoRedorMin` representa o menor valor x (nesse caso, deve ser `(xDoBlocoAtual) -1`) e `xAoRedorMax` representa o maior valor de x (nesse caso, deve ser `(xDoBlocoAtual) +1`),  com o mesmo para os valores de Y.

é preciso executar este código para todos os espaços da matriz, o que pode ser atingido com dois loops for.
>[!abstract]- pseudo-código
> ```
> 	Para todo valor X e valor Y dentro da matriz CampoMinado:
> 		Para todo valor X entre os espaços X-1 e X+1, e para todo valor Y entre os espaços Y-1 e Y+1:
> 			Se CampoMinado[xAoRedor,yAoRedor].Bomba for verdadeiro:
> 				Some 1 a CampoMinado[xAtual,yAtual]
 >```

[Exemplo procurar bombas campo minado](1%20-%20Bruto/programação/csharp/projetos/CampoMinado/Exemplo%20procurar%20bombas%20campo%20minado.md)


### Pronto!
A parte do código que gera o campo já está pronta.

---
## 3.**Entrada do usuário**




###### Referências





 