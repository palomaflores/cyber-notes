# GIT BRANCH
As `branches` no Git são linhas paralelas de desenvolvimento, elas permitem que alterações sejam realizadas sem afetar o código principal (`main`)
O `git branch` gerencia as branches (ramificações) em um repositório

- **Listar branches:**
	- Mostra todas as branches locais
	- A branch atual fica com um `*` na frente

```bash
git branch
```

- **Criar uma nova branch:**
	- Cria uma nova branch a partir da branch atual
	- **NÃO MUDA PARA ESSA BRANCH AUTOMATICAMENTE**

```bash
git branch nome-nova-branch
```

- **Criar e trocar de branch ao mesmo tempo:**

```bash
git checkout -c nome-nova-branch
```

- **Trocar de branch :**
```bash
git checkout nome-da-branch #Nome da branch que quer entrar
```

- **Deletar uma branch local:**
	- Só deleta a branch se ela já tiver sido mesclada
	- Usar comando `-D` para deletar mesmo com mudanças não mescladas

```bash
git branch -D nome-da-branch
```

- **Ver branches remotas:**
	- Mostrar as branches que estão no repositório remoto (ex: GitHub)

```bash
git branch -r
```

- **Ver todas as branches (local e remotas):**

```bash
git branch -a
```

#### Tabela
|Comando|Ação|
|---|---|
|`git branch`|Lista branches locais|
|`git branch nova-branch`|Cria uma branch|
|`git branch -d nome`|Deleta branch|
|`git branch -D nome`|Força deleção|
|`git branch -r`|Lista branches remotas|
|`git branch -a`|Lista todas (local + remoto)|
