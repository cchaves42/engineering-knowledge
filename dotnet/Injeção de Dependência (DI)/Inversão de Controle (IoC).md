
A Inversão de Controle (Inversion of Control) é um **princípio de design** que determina que o controle sobre a criação da dependência seja feito por um agente externo, como um container ou framework.

Exemplo:

```csharp
public class PedidoService 
{
   private IEmailService _emailService;
   
   public PedidoService(IEmailService emailService)
   {
        _emailService = emailService;
   }
}
```

`PedidoService` não conhece a implementação de `EmailService`. O controle de criação da dependência foi transferido para fora da classe.