
Pode ser um framework que gerencia a criação de objetos e injeta a dependência de forma automática.

O .NET possui um IoC Container nativo  em Microsoft.Extensions.DependencyInjection e existem outros que podem ser instalados.

## Tempo de Vida do Serviço

Controla por quanto tempo um objeto vai existir após ter sido criado pelo container.

1) **Problema**: O container precisa saber quando criar uma instância de um serviço e quando reutilizá-la.
2) **Consequência**: Compartilhamento de estado de forma inadequada
3) **Solução**: Definir um tempo de vida para cada serviço
4) **Mecanismo**: Controlar o tempo de vida para cada serviço usando `Transient`, `Scoped` ou `Singleton`

**Transient**

```text
Cada vez que o serviço for solicitado, uma nova instância será criada.
```

Exemplo:
PedidoService → IEmailService → EmailService (1)
PedidoService → IEmailService → EmailService (2)

Mesmo dentro da mesma requisição, serão instâncias diferentes.

**Scoped**

```text
Um instância por escopo (geralmente uma requisição HTTP)
```

Exemplo: 

Requisição 1:
PedidoService → EmailService (1)
ClienteService → EmailService (1)

PedidoService e ClienteService usarão a mesma instância de EmailService, já que ambas chamam EmailService na mesma requisição.

**Singleton**

```text
Uma única instância durante toda a vida da aplicação.
```

Exemplo:

Aplicação Rodando → EmailService criado → Todas as requisições para EmailService estarão na mesma instância. Se a aplicação for encerrada, a instância deixa de existir.