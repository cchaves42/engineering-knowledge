1) **Problema**: Dados não necessários ficam expostos à camadas externas.
2) **Consequência**: Retorno de informações não necessárias
3) **Solução**: Retornar somente as informações necessárias
4) **Mecanismo**: Criar uma classe que tenha somente as informações necessárias
5) **Resultado**: As classes externas não conhecem a entidade
6) **O que eu ganhei com essa mudança?**
	1) Exposição somente dos dados necessários por questão de segurança ou reduzir o tamanho da carga para melhorar o desempenho
	2) DTOs e entidades podem evoluir sem impactar externamente


**Nomenclatura**

UserDTO -> Retorno do repositório
UserResponse -> Dados de saída
UpdateUserRequest -> Dados de entradas

Principal função do DTO é armazenar e transferir dados. Geralmente não tem métodos e nem lógica de negócio.

Pode adicionar validações e formatações.

Exemplo: Formatação de data
```csharp
public DateTime StartDate { get; set; }

public string FormattedDate => StartDate.ToString("dd/MM/yyyy");
```


Mapeamento
- Manual
- Bibliotecas (AutoMapper)
- Método de extensão

Criar uma classe estática (não permite instancia) com métodos estáticos
- Entidade -> DTO
- DTO -> Entidade
- Outras demandas: Lista e etc


