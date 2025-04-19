# GIT
O Git é um sistema de controle de versão distribuído, rápido e escalável, com vários comandos que permitem realizar operações avançadas e controle total de repositório
## Configuração git
As configurações `user.name` e  `user.email` **definem o autor dos commits no Git**. Elas funcionam localmente (computador do usuário)
Toda vez que realizar um commit o Git vai salvar o conteúdo o commit, o autor do commit e a data/hora.

1. Definir nome do autor:
```bash
git config --global user.name "Nome do autor"
```

2. Definir e-mail do autor:
```bash
git config --global user.email emaildousuário@exemplo.com #e-mail do github
```

#### Por que `--global`?
O comando `--global` faz com que essa configuração funcione em **todos os repositórios Git no computador do usuário**.
- Obs: Para usar um nome/e-mail diferente para um projeto, basta rodar os mesmos comandos sem o `--global` na pasta do projeto
```bash
git config user.name "Nome local"
git config user.emaik email-local@exemplo.com
```

#### Verificar configurações
- Use o comando `--list` para verificar o que já está configurado:
```bash
git config --list
```

### Git X GitHub
- Git - Sistema de controle de versão
- GitHub - Plataforma de hospedagem de repositórios Git

Quando o usuário:
- Faz um commit com o Git, ele assina com o nome e e-mail configurado
- Envia (`push`) o commit pro GitHub, ele usa o e-mail do commit para associar ele a uma conta

## Comandos
- [GIT HELP](https://github.com/palomaflores/cyber-notes/blob/main/LINUX/GIT/GIT%20COMANDOS/GIT%20HELP.md)
- [GIT INIT](https://github.com/palomaflores/cyber-notes/blob/main/LINUX/GIT/GIT%20COMANDOS/GIT%20INIT.md)
- [GIT ADD](https://github.com/palomaflores/cyber-notes/blob/main/LINUX/GIT/GIT%20COMANDOS/GIT%20ADD.md)
- [GIT COMMIT](https://github.com/palomaflores/cyber-notes/blob/main/LINUX/GIT/GIT%20COMANDOS/GIT%20COMMIT.md)
- [GIT REMOTE](https://github.com/palomaflores/cyber-notes/blob/main/LINUX/GIT/GIT%20COMANDOS/GIT%20REMOTE.md)
- [[GIT PUSH]]
- 