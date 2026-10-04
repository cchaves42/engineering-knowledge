
**LLM (Large Language Model - Modelo de Linguagem de Grande Escala)**: Modelo de IA treinado com uma grande quantidade de textos para aprender padrões da linguagem e a partir de uma sequência de tokens, prever quais tokens provavelmente vêm em seguida.

```
Entrada
↓
"Dependency Injection é uma técnica que"
↓
LLM
↓
"permite"
```

A partir da frase "Dependency Injection é uma técnica que" o modelo calcula probabilidades para possíveis próximos tokens:

```
permite       45%
possibilita   20%
utiliza       10%
```

O modelo escolhe um token e continua o processo:

```
"Dependency Injection é uma técnica que"
↓
"permite"
↓
"Dependency Injection é uma técnica que permite"
↓
"uma"
↓
"Dependency Injection é uma técnica que permite uma"
```


**Tokens / Arquitetura**

![[fluxo_llm.png]]


**Transformer**: Arquitetura de rede neural artificial criada em 2017.
Traduz a linguagem natural para o que a LLM interpreta (números).
Divide a entrada em partes (tokens) e codifica para números.

**Vocabulário**
Um vocabulário maior gera gera menos tokens.
Quando há menos tokens, é necessáro dividir a palavra em mais partes.

Exemplo:
**1 mil tokens**
entendimento -> `ent` `end` `i` `ment` `o`

**200 mil tokens**
entendimento -> `entendi` `mento`

**Autoregressão / Geração autoregressiva**
A cada rodada, o texto gerado entra no próximo cálculo (aumento de custo).

1ª rodada - 3 tokens
```
Dependency Injection é
```

2ª rodada - 4 tokens
```
Dependency Injection é uma
```

3ª rodada - 5 tokens
```
Dependency Injection é uma técnica
```