---
{"dg-publish":true,"permalink":"/structs-em-csharp/"}
---

2025-11-26 20:49

Status:beta

Tags: [[csharp\|csharp]]
# Structs em C#.

---
## Declaração
Em versões recentes do c#, podemos declarar uma struct da seguinte forma:
```
struct NomeDaStruct
{
   public tipo nomeDaVariavel = valor;
   public NomeDaStruct(){}
}
```
A linha 4 (public NomeDaStruct (){}) é uma função do tipo constructor, e ela define que há declaração explícita dentro da struct, permitindo que a linha 3 funcione corretamente.
Ex:
```
struct Espaco
{
    public bool foiInteragido = false;
    public bool eBomba = false;
    public bool eUmaBandeira = false;
    public int? bombasAoRedor; 
	public char? simbolo;
	
	public Espaco(){} //sem esta linha, as atribuições não funcionam corretamente
}
```
### Atenção!
Este código pode não funcionar em versões mais antigas do C#. Neste caso, precisamos fazer o seguinte:
```
struct NomeDaStruct
{
   public tipo nomeDaVariavel { get; set; };
   public NomeDaStruct(int x)
   {
      NomeDaVarivel = valor;
   }
}
```
"{ get; set; }" define que a variável pode ser acessada e modificada.
Agora usamos o constructor diretamente: Nessas versões mais antigas, as variáveis dentro das structs precisam ser criadas no campo comum, enquanto as declarações de valor padrão ocorrem dentro da função com o nome da struct.
```
   public NomeDaStruct(int x)
   {
      NomeDaVarivel = valor;
   }
```
O uso de "int x" dentro do parênteses da função "NomeDaStruct" é nescessário, já que funções dentro de estruturas precisam de pelo menos um parâmetro, mesmo que ele não seja utilizado. Int X é apenas um exemplo, já que qualquer variável funcionária
Ex:
```
struct Espaco
{
    public bool foiInteragido { get; set; }
    public bool eBomba { get; set; }
    public bool eUmaBandeira { get; set; }
    public int? bombasAoRedor { get; set; }
    // o ponto de interrogação significa "sem valor inicial"
	public char? simbolo { get; set; }
	
	public Espaco(Espaco teste)
	{
	    foiInteragido = false;
	    eBomba = false;
	    eUmaBandeira = false;
	    bombasAoRedor = null;
	    simbolo = null;
	}
}
```
## local dentro do código

>[!danger] ERRADO:
```
public class Program
{
    struct Pessoa
    {
        public int idade;
        public int nome;
    }
    public static void Main(string[] args)
    {
        System.Console.WriteLine("Exemplo!");
    }
}
```
OU
```
public class Program
{
    class Pessoa
    {
        public int idade;
        public int nome;
    }
    public static void Main(string[] args)
    {
        System.Console.WriteLine("Exemplo!");
    }
}
```

>[!success] CORRETO:
```
strut Pessoa
{
    public int idade;
    public int nome;
}
public class Program
{
    public static void Main(string[] args)
    {
        System.Console.WriteLine("Exemplo!");
```
OU
```
class Pessoa
{
    public int idade;
    public int nome;
}
public class Program
{
    public static void Main(string[] args)
    {
        System.Console.WriteLine("Exemplo!");
    }
}
```

Caso seu código tenha um namespace explicito, a struct ou a classe devem ficar dentro do mesmo.

---


###### Referências


