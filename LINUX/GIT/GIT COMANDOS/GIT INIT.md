# GIT INIT
O comando `git init` é usado para iniciar um novo repositório Git.
Ao executar `git init` dentro de um repositório, o Git cria uma subpasta oculta `.git` que tem todos os arquivos e estruturas de dados que o Git precisa para acompanhar o histórico de versões do projeto.

```bash
mkdir nome-do-projeto
cd nome-do-projeto
git init
```

![[git init.png]]

Obs: É importante lembrar que o repositório está vazio até que sejam feitos e adicionados commits de arquivos
```bash
git add .
git commit -m "mensagem de commit"
```

**Para iniciar um repositório Git já conectado a um repositório remoto:**
```bash
git remote add origin [link do prepositório].git
```

