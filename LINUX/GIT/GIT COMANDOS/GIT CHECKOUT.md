# GIT CHECKOUT
O  `git checkout` serve para trocar de branch, restaura arquivos ou commits e criar uma nova branch (comando `-b`)

- **Trocar de branch:**
	- Muda da branch atual para outra
	- O Git atualiza os arquivos do diretório local para refletir o estado da branch

```bash
git checkout nome-da-branch
```

- **Criar e trocar para uma nova branch:**
	- Cria e já entra na nova branch

```bash
git checkout -b nova-branch
```

- **Restaurar arquivos específicos (descartar alterações):**
	- Restaura o arquivo para o estado anterior de commit
	- Cuidado! Esse comando descarta as mudanças que não foram commitadas

```bash
git checkout -- caminha/do/arquivo
```

- **Navegar por versões antigas (commits)**
	- Troca o repositório inteiro para a versão de um commit antigo
	- Fica no temporariamente no "modo detached HEAD" (fora de qualquer branch)

```bash
git checkout abc1234
```

Obs: O `1234` (no exemplo `abc1234`) representa **os primeiros caracteres do hash de um commit**. No Git, **todo commit tem um identificador único**, chamado de **SHA-1 hash**, que geralmente é uma sequência longa como esta: `abc1234f9a8e2b0cd0f93c9d0456e709ef1aa12b`

- **Salvar alguma alteração no no "modo detached HEAD":**
```bash
git checkout -b nova-branch
```

### Como ver o hash do commit?
- **Ao usar o comando `git log` vai aparecer:**
```bash
commit abc1234f9a8e2b0cd0f93c9d0456e709ef1aa12b # abc1234 é a primeira parte do commit
Author: Paloma
Date:   Fri Apr 19 10:32:00 2025 -0300
```
