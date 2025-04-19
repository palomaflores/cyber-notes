# GIT MERGE
O  `git merge` junta o conteúdo de duas branches. Ele pega as mudanças feitas em uma branch e aplica na branch atual

- **Acessar branch que vai receber as alterações:**
```bash
git checkout main
```

- **Mesclar a outra branch (ex: branch-b) na atual:**
	- O Git vai unir os commits das duas branches
	- Pode acontecer um merge automático, sem conflitos
	- Um commit de merge pode ser criado automaticamente, dependendo do caso.
```bash
git merge branch-b
```

#### Em caso de conflitos
**Importante!** Conflitos acontecem quando duas branches modificaram as mesmas linhas ao mesmo tempo
1. **O Git vai mostrar os arquivos em conflito com as marcações:**
```
<<<<<<< HEAD
código da branch atual
=======
código da branch que está sendo mesclada
>>>>>>> branch-b
```

2. **Resolver manualmente e salvar**
	- 2.1. Git vai responder:
	- 2.2. O Git vai editar o arquivo automaticamente, marcando os conflitos:
	- 2.3. Escolher qual manter:
	- 2.4. Salvar arquivo > Marcar conflito como resolvido > Fazer commit de merge
	
```bash
# Resposta Git
CONFLICT (content): Merge conflict in app.js
Automatic merge failed; fix conflicts and then commit the result.

# Edição Git
<<<<<<< HEAD
// Essa é a versão da branch atual (main)
console.log("Olá, mundo!");
=======
 // Essa é a versão da branch que você tentou mesclar (branch-b)
console.log("Olá, universo!");
>>>>>>> branch-b

# Escolher branch (escolhi branch-b)
console.log("Olá, universo!");

# Marcar como resolvido
git add app.js

# Commit merge
git commit
```

- **Obs: Se eu quiser mesclar/juntar as duas branches:**
	- Depois de resolver, remova as marcações do Git (`<<<<<<<`, `=======`, `>>>>>>>`).
```js
console.log("Olá, mundo!");
console.log("Olá, universo!");
```

### Resumo

|Comando|Ação|
|---|---|
|`git merge nome-da-branch`|Mescla a branch especificada na branch atual|
|`git merge --no-ff nome`|Força commit de merge, mesmo em fast-forward|
|`git merge --abort`|Cancela o merge em andamento (se der conflito)|
