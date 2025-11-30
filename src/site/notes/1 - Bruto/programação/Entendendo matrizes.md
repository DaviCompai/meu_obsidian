---
{"dg-publish":true,"permalink":"/1 - Bruto/programação/Entendendo matrizes/"}
---

2025-11-27 15:12

Status:beta

Tags: [programação](programação.md)
# Entendendo matrizes

Uma matriz bidimensional pode ser representada como um plano cartesiano composto por valores inteiros (ou uma grade).

Digamos que temos uma matriz chamada "rosto", onde um valor de 1 representa um pixel preto, e um valor de 0 representa um pixel branco.
```
class Program 
{
  static void Main() 
  {
    int[,] rosto = new int[5,5]; //declara uma matriz com valores inteiros, tendo "5 de altura" e "5 de largura".
  }
}
```
Inicialmente, ela se parece com isso:

|  0  |  0  |  0  |  0  |  0  |
| :-: | :-: | :-: | :-: | :-: |
|  0  |  0  |  0  |  0  |  0  |
|  0  |  0  |  0  |  0  |  0  |
|  0  |  0  |  0  |  0  |  0  |
|  0  |  0  |  0  |  0  |  0  |
###### Todos os valores estão zerados, então a imagem é completamente branca.
visualmente:
![](https://raw.githubusercontent.com/DaviCompai/meu_obsidian/imagens/matriz_0.png)

Agora considerando que podemos acessar os pixeis da seguinte forma:
```
rosto[x,y] = estado (1 ou 0)
```
podemos adicionar as seguintes linhas:
```
rosto[0,4] = 1;
rosto[1,1] = 1;
rosto[2,1] = 1;
rosto[3,1] = 1;
rosto[4,4] = 1;
```
gerando:

|  1  |  0  |  0  |  0  |  1  |
| :-: | :-: | :-: | :-: | :-: |
|  0  |  0  |  0  |  0  |  0  |
|  0  |  0  |  0  |  0  |  0  |
|  0  |  1  |  1  |  1  |  0  |
|  0  |  0  |  0  |  0  |  0  |
###### .
![](https://raw.githubusercontent.com/DaviCompai/meu_obsidian/imagens/matriz_1.png)

Você pode continuar expandindo esse exemplo, deixando o rosto feliz:
```
    rosto[0,2] = 1;
    rosto[4,2] = 1;
```

|  1  |  0  |  0  |  0  |  1  |
| :-: | :-: | :-: | :-: | :-: |
|  0  |  0  |  0  |  0  |  0  |
|  1  |  0  |  0  |  0  |  1  |
|  0  |  1  |  1  |  1  |  0  |
|  0  |  0  |  0  |  0  |  0  |
###### .
![](https://raw.githubusercontent.com/DaviCompai/meu_obsidian/imagens/matriz_2.png)
E então triste:
```
    rosto[0,2] = 0; //deixa os pixeis adicionados anteriormente brancos
    rosto[4,2] = 0;
    rosto[0,0] = 1; 
    rosto[4,0] = 1;
```

|  1  |  0  |  0  |  0  |  1  |
| :-: | :-: | :-: | :-: | :-: |
|  0  |  0  |  0  |  0  |  0  |
|  0  |  0  |  0  |  0  |  0  |
|  0  |  1  |  1  |  1  |  0  |
|  1  |  0  |  0  |  0  |  1  |
###### .
![](https://raw.githubusercontent.com/DaviCompai/meu_obsidian/imagens/matriz_3.png)

Acredito que esse exemplo demonstre como matrizes podem ser usadas para simbolizar grades de pixeis/objetos, como no projeto do campo minado.
###### Referências


