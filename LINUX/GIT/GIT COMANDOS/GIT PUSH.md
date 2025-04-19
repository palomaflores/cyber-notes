# GIT PUSH
O comando `git push` envia as alterações locais para o repositório remoto (ex: GitHub)
Depois de fazer os commits no repositório local, as alterações ficam só no computador do autor, para compartilhar elas com o repositório local é preciso usar o comando `git push`

```bash
git push -u origin main
```

- `origin`: nome  padrão do repositório remoto 
- `main`: nome da branch que o autor quer enviar
- `-u`: configura o rastreamento automático entre a branch local e a remota

**Comando completo:**
```bash
# Adicionar arquivos
git add .

# Criar commit 
git commit -m "mensagem de commit"

# Enviar commit para repositório remoto
git push -u origin main
```

