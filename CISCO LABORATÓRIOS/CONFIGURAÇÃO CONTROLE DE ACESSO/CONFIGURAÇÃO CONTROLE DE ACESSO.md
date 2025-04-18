# Documentação Técnica - Laboratório CONFIGURAÇÃO CONTROLE DE ACESSO
## Segurança de Rede com AAA, E-mail e FTP
##### Objetivo Geral
Configurar e validar mecanismos de autenticação (AAA), comunicação via e-mail (SMTP/POP3) e transferência de arquivos (FTP), implementando autenticação de usuários e controle de privilégios.

# Parte 1 - Configuração e uso de credenciais de autenticação AAA
### 1.1. Configuração do servidor AAA (RADIUS)
**Local:** Sede → Armário de conexões → Servidor AAA-RADIUS

**Ações:**
- Acessar a aba `Services` > `AAA`.
- Ativar o serviço AAA.
- Criar os usuários:
    - `user1` / `PASSuser1!`
    - `user2` / `PASSuser2!`
 ![[Pasted image 20250418020319.png]]
### 1.2. Configurar autenticação sem fio HQ-Laptop-1
**Dispositivo:** HQ-Laptop-1
**Procedimentos:**
- Acessar aba `Config` > Interface `Wireless0`
- SSID: `HQ-INT`
- Autenticação: WPA2
- Usuário: `user1`
- Senha: `PASSuser1!`
- Obter IP via DHCP 
    **Validação:** IP deve estar na rede `169.254.226.110`
    
### 1.3. Configurar autenticação sem fio HQ-Laptop-2
**Dispositivo:** HQ-Laptop-2
**Procedimentos:**
- Acessar `Config` > Interface `Wireless0`
- SSID: `HQ-INT`
- Autenticação: WPA2
- Usuário: `user2`
- Senha: `PASSuser2!`
- Obter IP via DHCP
	 **Validação:** IP deve estar na rede `169.168.50.4`

![[Pasted image 20250418020430.png]]

# Parte 2 - Configuração e uso de serviços de e-mail
### 2.1. Ativar serviços de e-mail
**Local:** Sede → Armário de conexões → Servidor MAIL

**Ações:**
- Aba `Services` > `EMAIL`
- Ativar SMTP e POP3
- Domínio: `mail.cyberhq.com`
- Criar usuários:

| Usuário | Senha     |
| ------- | --------- |
| HQuser1 | Cisco123! |
| HQuser2 | Cisco123~ |
| BRuser1 | Cisco123- |
| BRuser2 | Cisco123+ |


![[Pasted image 20250418020515.png]]
### 2.2 Configuração dos clientes de e-mail

| PC/Laptop   | Nome   | E-mail                   | Usuário   | Senha       |
| ----------- | ------ | ------------------------ | --------- | ----------- |
| PC 1-1      | Suk-Yi | HQuser1@mail.cyberhq.com | `HQuser1` | `Cisco123!` |
| PC 2-3      | Ajulo  | BRuser1@mail.cyberhq.com | `BRuser1` | `Cisco123-` |
| HQ-Laptop-1 | Malia  | BRuser2@mail.cyberhq.com | `BRuser2` | `Cisco123+` |
| NetAdmin    | Cisco  | HQuser2@mail.cyberhq.com | `HQuser2` | `Cisco123~` |

**Procedimentos:**
- Acessar aba `Desktop` > `Email`
- Servidor SMTP/POP3: `mail.cyberhq.com`

![[Pasted image 20250418020608.png]]
### 2.3. Enviar e verificar e-mails
**Origem:** PC 1-1 (Suk-Yi)
**Destino:** PC 2-3 (Ajulo)
- Aba `Desktop` > `Email` > `Compose`
- Escrever e enviar uma mensagem de teste
-  Ir até PC 2-3 > `Desktop` > `Email` > `Receive`

![[Pasted image 20250418020648.png]]

# Parte 3 - Configuração e uso de serviços FTP
### 3.1. Ativar serviço FTP
**Local:** Sede → Armário de conexões → Servidor FTP
**Ações:**
- Acessar a aba `Services` > `FTP`
- Ativar o serviço FTP
**Procedimentos:**
- Acessar aba `Desktop` > `Email`
- Nome: Suk-Yi
- E-mail: HQuser1@mail.cyberhq.com
- Servidor: `mail.cyberhq.com`
- Usuário: `HQuser1`
- Senha: `Cisco123!

### 3.2. Criar usuários FTP

| Nome de usuário | Senha    | Privilégios             |
| --------------- | -------- | ----------------------- |
| cisco           | cisco    | acesso total            |
| sukyi           | cisco123 | acesso total            |
| ajulo           | cisco321 | acesso total            |
| malia           | cisco123 | todos, exceto `Excluir` |
![[Pasted image 20250418020726.png]]
### 3.3. Transferência arquivos viaFTP
**Dispositivo:** Net-Admin PC
**Comandos:**
````bash
ftp 192.16875.2
Username: sukyi
Password: cisco 132
dir
get aMessage.txt
````


**Após baixar:**
- `Editor de texto` > `Arquivo` > `Abrir` aMessage.txt
- Acessar `Arquivo` > `Novo`
- Digite uma mensagem qualquer
- Clique em `Arquivo` > `Salvar`

**Criar e carregar novo arquivo:**
- Novo arquivo: `aMessage_new.txt`
- Upload via:
````bash
ftp 192.168.75.2
Username: sukyi
Password: cisco123
put aMessage_new.txt #Carrega a mensagem aMessage_new.txt
quit #sair
````

![[Pasted image 20250418014823.png]]
### 3.4. Verificação de privilégios FTP
**Dispositivo:** HQ-Laptop-1
**Login como Malia:**
```bash
ftp 192.168.75.2
Username: malia
Password: cisco122
delete aMessage_new.txt
rename aMessage_new.txt aMessage_rename.txt
```

Comandos
- Delete: Negado 
- Rename: Aprovado

![[Pasted image 20250418020853.png]]

---
## Conclusão
Este laboratório permite compreender e aplicar conceitos práticos de autenticação, autorização, envio de e-mails e transferência de arquivos com controle de acesso. Todos os serviços foram testados e validados conforme o comportamento esperado no Packet Tracer.

