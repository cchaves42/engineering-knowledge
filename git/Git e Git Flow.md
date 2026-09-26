
## Git

Sistema de controle de versão que registra todas as alterações feitas no código de um projeto ao longo do tempo.

 *  Com o controle de versão é possível recuperar o histórico completo de alterações permitindo identificar o que mudou, quando mudou e quem mudou. 
 * Possibilidade de restaurar o código em casos de erro.
 * Trabalho em equipe sem sobrescrever o arquivo. Se mais de uma pessoa editar o mesmo arquivo, o git identificará e possibilitará a resolução do conflito.

### Comandos básicos

```script
git init
```

**Cria um novo repositório Git no diretório atual
* Adiciona `.git` necessária para o controle de versão
___
```script
git branch -m <novoNome>
```
**Renomear uma branch**
* Renomeia a branch atual

```script
git branch -m <nomeAtual> <novoNome>
```
* Renomeia uma branch específica

___
```script
git checkout <branch>
```
* **O `git checkout` possui diversas responsabilidades:**
	* Troca de branch;
	* Cria uma branch (argumento `-b`);
	* Restaura arquivos e commits

```
git switch <branch>
```
* **O `git switch` possui operações relacionadas a branchs:**
	* Troca de branch
	* Cria uma branch (argumento `-c`ou `--create`)

___
```
git rebase
```
* **Reposiciona os commits de uma branch**
	* Reaplica commits de uma branch sobre uma nova base, criando novos commits e alterando o histórico da branch.

```
Antes:

A---B---C  main
     \
      D---E  feature
```

```
Depois do rebase:

A---B---C  main
         \
          D'---E'  feature
```

Neste exemplo, o commit D foi reposicionado para depois do C.

⚠️ **Atenção**: O uso de rebase em projetos compartilhados com outras pessoas precisa ser usado com cautela já que o histórico pode causar divergências.
## Git Flow

Git Flow é um modelo de organização das branchs que define pápeis e fluxos para as branchs utilizadas no desenvolvimento, pré-releases e correções de bugs em produção.

`⚠️ O papel de cada branch pode variar conforme o processo da equipe. A descrição foi escrita com base na minha experiência atual.`

**Branchs Principais**
main → representa o código de produção
develop → representa as funcionalidades que estão prontas para ir para produção

**Branchs de Suporte**
hotfix/* → utilizada para correção de um bug em produção
feature/* → utilizada para uma nova funcionalidade
release/* → utilizada para preparar uma versão para produção

**Hotfix**
```
main → hotfix/* → main → develop
```

**Feature**
```
develop → feature/* → develop
```

**Release**
```
develop → release/* → main
```


### Fluxos

**Desenvolvimento**
```
main
  │
  └── develop
        │
        └── feature/*
              │
              └── develop
```

**Release**
```
develop
   │
   └── release/*
          │
          ├── main
          │
          └── develop
```

**Hotfix**
```
main
  │
  └── hotfix/*
         │
         ├── main
         │
         └── develop
```