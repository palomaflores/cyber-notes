# GIT COMMIT
O comando `git commit` salva as alterações no histórico do repositório.
Como ele funciona:
- Depois de adicionar os arquivos com `git add` o `git commit` registra as alterações em um novo ponto no histórico do projeto, criando um novo *commit* com a mensagem de descrição.

```bash
git commit -m "mensagem de commit"
```

- `-m`: define a mensagem direto no terminal

##### O que vai no commit?
A única coisa que vai no commit são os arquivos adicionados e alterações realizadas com `git add`. Ou seja, se eu modificar 10 arquivos e só tiver feito penas `git add` 3 vezes, só os esses 3 farão parte do commit.

- `git status`: serve para verificar o que está pronto para ser commitado