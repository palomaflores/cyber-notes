# GIT REMOTE
O comando `git remote` é usado para gerenciar repositórios remotos, ou seja, versões do repositório hospedadas em outro lugar (ex: github)

##### Como funciona o repositório remoto?
O repositório remoto é uma cópia do projeto armazenada em um servidor, usado para compartilhar com outras pessoas ou fazer backup.

- **Para listar os remotos configurados:**
```bash
git remote
```

- **Adicionar repositório remoto**
```bash
git remote add origin https://github.com/usuario/repositorio.git
```

Obs:
- `origin`: nome padrão do git para repositório remoto
- O link é a URL do repositório remoto (**HTTPS** ou **SSH**)

##### Exemplo completo
```bash
git init
git remote add origin https://github.com/nome-de-usuario/nome-do-repositorio.git
git add .
git commit -m "mensagem de commit"
git push -u origin main
```

##### Outros comandos úteis
- **Ver os remotos configurados:**
```bash
git remote -v
```

- **Remover um remoto:**
```bash
git remote remove origin
```

- **Renomear um remoto:**
```bash
git remote rename origin github
```