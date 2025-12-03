---
{"dg-publish":true,"permalink":"/1 - Bruto/programação/csharp/projetos/CampoMinado/Exemplo procurar bombas campo minado/","created":"2025-12-02T22:09:04.863-03:00","updated":"2025-12-02T22:17:59.037-03:00"}
---

02-12-2025 22:09

Status: completo

Tags:[[1 - Bruto/programação/csharp/projetos/CampoMinado/Campo Minado\|Campo Minado]]
# Exemplo procurar bombas campo minado

descobrindo a quantidade de números ao redor de `campoMinado[2,2]`
(verde: bloco sendo processado)
(vermelho: parte sendo testada)
(parenteses = valor real)

 ```
 xAoRedorMin(1) = xDoBlocoAtual(2) - 1;
 xAoRedorMax(3) = xDoBlocoAtual(2) +1;
 yAoRedorMin(1) = yDoBlocoAtual(2) - 1;
 xAoRedorMax(3) = xDoBlocoAtual(2) +1;
 
 for (int xAoRedor = xAoRedorMin(1); xAoRedor <= xAoRedorMax(3); xAoRedor++)
 {
	for (int yAoRedor = yAoRedorMin(1); yAoRedor <= yAoRedorMax(3); yAoRedor++)
	{
		if(campoMinado[xAoRedor,yAoRedor].eBomba)
		{
			campoMinado[xDoBlocoAtual(2),yDoBlocoAtual(2)].bombasAoRedor++;
		}
	}
 }
```
 ![](/img/user/7 - Arquivos/imagens/códigos/campo minado/AcharBomba/matrizAcharBombas_1.png)
- - - 
para `xDoBlocoAtual == 1` e `yDoBlocoAtual == 1`:
![](https://raw.githubusercontent.com/DaviCompai/meu_obsidian/imagens/matrizAcharBombas_2.png)
`campoMinado[1,1].eBomba` é true: 
IF executa: número de bombas cresce (`campoMinado[2,2].bombasAoRedor = 1`)
 
 ---
Para `xDoBlocoAtual == 1` e `yDoBlocoAtual == 2`
![](/img/user/7 - Arquivos/imagens/códigos/campo minado/AcharBomba/matrizAcharBombas_5.png)
`campoMinado[1,2].eBomba` é false:
IF não executa.

---
Para `xDoBlocoAtual == 1` e `yDoBlocoAtual == 3`
![](https://raw.githubusercontent.com/DaviCompai/meu_obsidian/imagens/matrizAcharBombas_8.png)
`campoMinado[1,3].eBomba` é false:
IF não executa.

---
Para `xDoBlocoAtual == 2` e `yDoBlocoAtual == 1` 
![](/img/user/7 - Arquivos/imagens/códigos/campo minado/AcharBomba/matrizAcharBombas_3.png)
`campoMinado[2,1].eBomba` é false:
IF não executa.

---
Para `xDoBlocoAtual == 2` e `yDoBlocoAtual == 2
![](https://raw.githubusercontent.com/DaviCompai/meu_obsidian/imagens/matrizAcharBombas_6.png)
`campoMinado[2,2].eBomba` é false:
IF não executa.

---
Para `xDoBlocoAtual == 2` e `yDoBlocoAtual == 3` 
![](/img/user/7 - Arquivos/imagens/códigos/campo minado/AcharBomba/matrizAcharBombas_9.png)
`campoMinado[3,2].eBomba` é true:
 IF executa: número de bombas cresce (`campoMinado[2,2].bombasAoRedor = 2`)

---
Para `xDoBlocoAtual == 3` e `yDoBlocoAtual ==1`
![](/img/user/7 - Arquivos/imagens/códigos/campo minado/AcharBomba/matrizAcharBombas_4.png)
`campoMinado[2,2].eBomba` é false:  
IF não executa.

---
Para `xDoBlocoAtual == 3` e `yDoBlocoAtual == 2`
![](https://raw.githubusercontent.com/DaviCompai/meu_obsidian/imagens/matrizAcharBombas_7.png)
`campoMinado[2,2].eBomba` é false:  
IF não executa.

---
Para `xDoBlocoAtual == 3` e `yDoBlocoAtual == 3
![](https://raw.githubusercontent.com/DaviCompai/meu_obsidian/imagens/matrizAcharBombas_10.png)
`campoMinado[2,2].eBomba` é true:  
IIF executa: número de bombas cresce (`campoMinado[2,2].bombasAoRedor = 3`)



###### Referências


