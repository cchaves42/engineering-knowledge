
```
problema → consequência → solução → mecanismo → resultado
```

```csharp
public class PedidoService 
{
    private EmailService _emailService;
    
    public PedidoService()
    {
       _emailService = new EmailService()
    }
}
```

1) **Problema**: `PedidoService` cria diretamente uma instância de `EmailService`, ficando dependente de uma implementação concreta. Acoplamento.
2) **Consequência**: `PedidoService` está acoplado a implementação concreta de`EmailService`e precisa ser alterado caso a implementação seja substituída
3) **Solução**: `PedidoService` depender de uma abstração de `EmailService`em vez da implementação concreta
4) **Mecanismo**: Fornecer a implementação de `EmailService`através de uma abstração
5) **Resultado**: `PedidoService`não precisa conhecer a implementação concreta de `EmailService`. A implementação foi substituída por uma abstração.
6) **O que eu ganhei com essa mudança?**
	1) PedidoService não precisa instanciar EmailService diretamente
	2) Facilidade para criar mocks nos testes
	3) Responsabilidade de criar as dependências de EmailService fica fora de PedidoService.

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

```csharp
public class EmailService : IEmailService
{
   public void Enviar(string mensagem) 
   {
      // envia e-mail
   }
}
```

**Resumo**: Injeção de Dependência é uma técnica/padrão em que uma classe recebe externamente as dependências de que precisa, em vez de criá-las diretamente. 

Classe que cria diretamente uma dependência → gera acoplamento → queremos depender de uma abstração → recebemos a implementação externamente → a dependência é injetada.