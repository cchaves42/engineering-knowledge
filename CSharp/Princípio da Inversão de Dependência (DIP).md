
É um dos cinco **princípios** SOLID.

Ele orienta que `[1] módulo de alto nível não devem depender de módulos de baixo nível e ambos devem depender de abstrações` e `[2] abstrações não devem depender de detalhes, mas detalhes devem depender de abstrações`

Exemplo:

```csharp
public class PedidoService 
{
   private EmailService _emailService;
   
   public PedidoService() 
   {
       _emailService = new EmailService();
   }
}
```

`PedidoService` depende diretamente de uma implementação concreta de `EmailService`

O DIP é um princípio de designer que orienta a evitar esse tipo de depêndencia.