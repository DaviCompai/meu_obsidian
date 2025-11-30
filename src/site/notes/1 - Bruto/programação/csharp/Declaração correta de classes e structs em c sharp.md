---
{"dg-publish":true,"permalink":"/1 - Bruto/programação/csharp/Declaração correta de classes e structs em c sharp/"}
---

2025-11-26 20:49

Status:beta

Tags: [[3 - Tags/csharp\|3 - Tags/csharp]]
# Declaração correta de classes e structs em c sharp

---

## local:

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
    }
}
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


