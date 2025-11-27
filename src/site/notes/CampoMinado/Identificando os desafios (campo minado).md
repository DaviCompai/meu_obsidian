---
{"dg-publish":true,"permalink":"/campo-minado/identificando-os-desafios-campo-minado/"}
---

2025-11-26 20:11

Status: beta

Tags: [[CampoMinado/Campo Minado\|Campo Minado]]
# Identificando os desafios (campo minado)

Minha forma favorita de organizar um programa é apartir dos desafios apresentados pela mesma. Dessa forma, consigo separar o código facilmente, sem ficar "perdido" em momento algum.

Acredito que podemos separar este programa em 3 desafios principais:

## 1.**Criar o bloco do campo**
Existem infinitas formas de criar as bombas, mas todas elas irão precisar comportar as características das mesmas.
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
>  Structs e classes [[Structs em Csharp#local dentro do código\|não podem ser declaradas dentro da classe programa/main!]]
>  Além disso, a [[Structs em Csharp#Atenção!\|forma que elas devem ser declaradas]] pode ser diferente em versões mais antigas do csharp
Q
 
Inicialmente, fiz a seguinte struct:
```
struct Espaco
{
    public bool foiInteragido = false;
    public bool eBomba = false;
    public bool eUmaBandeira = false;
    public int? bombasAoRedor; 
    // o ponto de interrogação significa "sem valor inicial"
	public char? simbolo;
	
	public Espaco(){} //sem esta linha, as atribuições não funcionam corretamente
}
```
A variável simbolo representa o valor que será mostrado no console quando o campo inteiro for exibido.

Precisaremos escolher simbolos, assim como escolhemos atribuições anteriormente. Para isso, podemos usar caracteres usuais (letras ou simbolos mais comuns,números, etc) ou especiais (chamados de "unicodes"). 
>[!Danger]- Atenção
Em relação aos unicodes, certa cautela é necessária, já que alguns deles não aparecem no console, aparecendo como um "?". 
Alguns deles começam a funcionar com a adição deste comando:
Console.OutputEncoding = System.Text.Encoding.UTF8
>
>Essa informação se torna útil na próxima seção.

## 2.**Criar o campo**
O campo ficará dentro de uma matriz dimensional, já que o mesmo tem uma organização completamente compatível com ela.
*[[Entendendo matrizes\|revisão de matrizes/por que usar neste momento?]]*

Para criar nossa matriz que representará o campo, podemos criar um método (mesmo que uma função)
```
    public static Espaco[,] criarCampo(int numeroDeBombas,int tamanhoX,int tamanhoY)
    {
        Espaco[,] campo = new Espaco[tamanhoX,tamanhoY];
        return campo;
    }
```
esse método cria e retorna uma matriz com a estrutura que representa cada espaço, porém, ele não gera as bombas.

Parar gerar as bombas, você ira precisar adicionar algumas linhas que sorteiem campos aleatórios da gerada, e que declare o campo .eBomba como verdadeiro.

Para isso, você pode fazer um loop while que roda enquanto o número total de bombas não alcança o número desejado, com um [[Numeros aleatorios em csharp\|gerador de inteiros]] aleatórios tendo as cordenadas maximas x e y como número máximo (lembrando que matrizes começam em 0, então um campo com 8 de altura tem o y até 7).
2.1 **Saída para o terminal**

3.**Entrada do usuário**




###### Referências





 