# GIT ADD
O comando `git add` é usado para preparar arquivos para serem commitados no Git.
O que o `git add` faz?
- Ao realizar mudanças no projeto, o Git percebe essas mudanças mas não salva elas automaticamente no histórico. É preciso dizer os Git quais arquivos quer incluir no commit usando o comando `git add`

##### Comando específicos do `git add`
```bash
# Adicionar arquivos específicos
git add nome-do-arquivo

# Adiciona todos os arquivos de uma pasta específica
git add nome-da-pasta/

# Adiciona TUDO o que foi modificado
git add .
```


- **Para ver o que mudou e o que está pronto para commitar:**
```bash
git status
```

- **Para adicionar novos arquivos e ignorar deletados:**
```bash
git add -u
```