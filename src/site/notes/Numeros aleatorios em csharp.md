---
{"dg-publish":true,"permalink":"/numeros-aleatorios-em-csharp/"}
---

2025-11-27 16:07

Status: beta

Tags: [[csharp\|csharp]]
# Numeros aleatorios em c#.

Para criar **variáveis aleatórias** em c#,  você precisa de uma váriavel do tipo random, que pode ser inicializada com
```
Random nomeDaVariavel = new Random();
```

para gerar inteiros aleatórios menores que um valor Z e maiores que 0:
```
nomeDaVariavel.Next(ValorZ)
```
>[!Danger]- Atenção!
>isso significa que esta linha:
>
>int valorAleatorio = nomeDaVariavel.Next(100)
>
>pode gerar qualquer número de 0 a 99. Para gerar números até 100, o parametro ValorZ deve ser 101.

Para gerar valores iguais ou maiores que um ValorW e menores que um valorZ:
```
nomeDaVariavel.Next(ValorW,ValorZ)
```

###### Referências


