# Documentação Técnica - Laboratório CONFIGURAÇÃO AAA com TACACS+ e RADIUS

## Autenticação AAA com TACACS+ e RADIUS
##### Objetivo Geral
- Configurar a autenticação AAA baseada no servidor usando o **TACACS+** no R2.
- Verificar a autenticação AAA baseada em servidor no cliente **PC-B**.
- Configurar a autenticação AAA baseada no servidor usando o **RADIUS** no R3.
- Verificar a autenticação AAA baseada em servidor no cliente **PC-B**.
## Tabelas de endereçamento

| Dispositivo | Interface     | Endereço IP | Máscara de Sub-rede | Gateway Padrão | Porta do Switch |
| ----------- | ------------- | ----------- | ------------------- | -------------- | --------------- |
| R1          | G0/1          | 192.168.1.1 | 255.255.255.0       | N/D            | S1 F0/1         |
| R1          | S0/0/0 (DCE)  | 10.1.1.2    | 255.255.255.252     | N/D            | N/D             |
| R2          | G0/0          | 192.168.2.1 | 255.255.255.0       | N/D            | S2 F0/2         |
| R2          | S0/0/0        | 10.1.1.1    | 255.255.255.252     | N/D            | N/D             |
| R2          | S0/0/1 (DCE)  | 10.2.2.1    | 255.255.255.252     | N/D            | N/D             |
| R3          | G0/1          | 192.168.3.1 | 255.255.255.0       | N/D            | S3 F0/5         |
| R3          | S0/0/1        | 10.2.2.2    | 255.255.255.252     | N/D            | N/D             |
| TACACS+     | Placa de rede | 192.168.2.2 | 255.255.255.0       | 192.168.2.1    | S2 F0/6         |
| RADIUS      | Placa de rede | 192.168.3.2 | 255.255.255.0       | 192.168.3.1    | S3 F0/1         |
| PC-A        | NIC           | 192.168.1.3 | 255.255.255.0       | 192.168.1.1    | S1 F0/2         |
| PC-B        | NIC           | 192.168.2.3 | 255.255.255.0       | 192.168.2.1    | S2 F0/1         |
| PC-C        | NIC           | 192.168.3.3 | 255.255.255.0       | 192.168.3.1    | S3 F0/18        |


# Parte 1 - Configuração AAA usando TACACS+ no R2
### 1.1. Testar conectividade
- **Verificar se a rede está funcionando:**
	- Em PC-A > Desktop > Prompt de Comando
	- Comando `ping` com IP do PC-B e PC-C
	- Em PC-B > Desktop > Prompt de Comando
	- Comando `ping` com IP do PC-C

```bash
# Em PC-A
ping 192.168.2.3 # IP PC-B
ping 192.168.3.3 # IP PC-C

# Em PC-B
ping 192.168.3.3 # IP PC-C
```
![[Pasted image 20250418215524.png]]
![[Pasted image 20250418215556.png]]

### 1.2. Configuração de entrada de banco de dados de backup Admin
- **Criar usuário local de backup no R2:**
	- Va em R2 > CLI > Tecla `Enter`
	- Senha: `ciscoenpa55`
	- Entrar no modo de configuração: `configure terminal`
	- Criar usuário e senha: `username Admin2 secret admin2pa55`
	- Comando: `end` (Para finalizar)

```hash
R2>enable
Password:ciscoenpa55
R2#configure terminal
R2(config)#username Admin2 secret admin2pa55
R2(config)#end
```

![[Pasted image 20250418220422.png]]

### 1.3. Configuração TACACS+
- **Verificar a configuração do servidor TACACS+:**
	- Va em Servidor TACACS+ > Serviços > AAA
	- Verificar se:
		- O cliente R2 está listado com a chave `tacacspa55`
		- O usuário `Admin2` está criado com a senha `admin2pa55`

![[Pasted image 20250418220741.png]]

### 1.4. Configuração TACACS+ no R2
- **Configurar servidor TACACS+ no R2:**
	- Ir em R2 > CLI > `Enter`
	- Entrar no modo privilegiado: `enable`
	- Entrar no modo de configuração global: `configure terminal`
	- Configurar IP TACACS+: `tacacs-server host 192.168.2.2`
	- Configurar chave secreta TACACS+: `tacacs-server key tacacspa55`
	- Comando: `end`

```hash
R2#enable
R2#configure terminal
R2(config)#tattacacs-server host 192.168.2.2
R2(config)#tacacs-server key tacacspa55
R2(config)#end
```

![[Pasted image 20250418221415.png]]
### 1.5. Autenticação de login AAA para acesso no R2
- **Configurar autenticação de login AAA para o acesso de console no R2:**
	- Ir em R2 > CLI
	- Entrar no modo privilegiado: `enable`
	- Entrar no modo de configuração global: `configure terminal`
	- Ativar AAA: `aaa new-model`
	- Configurar autenticação padrão: `aaa authentication login default group tacacs+ local`
	- Aplicar à linha de console:
		- `line console 0`
		- `login authentication default`
	- Finalizar: `end`

```hash
R2>enable
R2#configure terminal
R2#aaa new-model
R2(config)#aaa authentication login default group tacacs+ local
R2(config)#line console 0
R2(config-line)#login authentication default
R2(config-line)#exit
```

![[Pasted image 20250418222326.png]]

### 1.6. Configuração das linhas vty para usar  autenticação AAA definido
- **Configurar as linhas vty com AAA:**
	- Ir em R2 > CLI
	- Entrar no modo privilegiado: `enable`
	- Entrar no modo de configuração global: `configure terminal`
	- Entrar na configuração das linhas VTY: `line vty 0 4
	- Aplicar o método de autenticação AAA que eu defini como **default**: `login authentication default`
	- Finalizar: `exit` > `end` 

```hash
R2#enable
R2#configure terminal
R2(config)#aaa new-model
R2(config)#aaa authentication login default group tacacs+ local
R2(config)#line vty 0 4
R2(config-line)#login authentication default
R2(config-line)#exit
R2(config)#end
```

![[Pasted image 20250418222950.png]]

### 1.7. Verificar autenticação AAA
- **Verificar login EXEC usando servidor TACACS+:**
	- Entrar no modo privilegiado: `enable`
	- Entrar no modo de configuração global: `configure terminal`
	- Criar AAA: `aaa new-model`
	- Configurar servidor TACACS+:
		- Host: `tacacs-server host 192.168.2.2`
		- Senha: `tacacs-server key tacacspa55`
	- Criar método de autenticação: `aaa authentication login default group tacacs+ local`
	- Configurar usuário local: `username Admin2 secret admin2pa55`
	- Aplicar método nas interfaces de acesso:
		- Console: `line console 0` > `login authentication default` > `exit`
		- VTY: `line vty 0 4` > `login authentication default` > `exit

```hash
R2#enable
R2#configure terminal
R2(config)#aaa new-model
R2(config)#tacacs-server host 192.168.2.2
R2(config)#tacacs-server key tacacspa55
R2(config)#aaa authentication login default group tacacs+ local
R2(config)#username Admin2 secret admin2pa55
R2(config)#line console 0
R2(config-line)#login authentication default
R2(config-line)#exit
R2(config)#line vty 0 4
R2(config-line)#login authentication default
R2(config-line)#exit
```

![[Pasted image 20250418224512.png]]
# Parte 2 - Configuração AAA usando RADIUS no R3
### 1.1. Configuração da base de dados de backup Admin
- **Configurar base de dados de backup local Admin:**
	- Ir em R3 > CLI
	- Senha: `ciscoenpa55`
	- Entrar no modo privilegiado: `enable`
	- Entrar no modo de configuração global: `configure terminal`
	- Criar usuário e senha: `username Admin3 secret admin3pa55`
	- Finalizar: `exit`

```hash
R3>enable
Password:ciscoenpa55
R3#configure terminal
R3(config)#username Admin3 secret admin3pa55
R3(config)#exit
```
![[Pasted image 20250418231740.png]]
### 1.2. Configuração do servidor RADIUS
- **Verificar a configuração do servidor RADIUS:**
	- Ir em servidor RADIUS > Serviços > AAA
	- Verificar se:
		-  O cliente R3 está listado com a chave `radiuspa55`
		- O usuário `Admin3` está criado com a senha `admin3pa55`

![[Pasted image 20250418232041.png]]
### 1.3. Configuração RADIUS no R3
- **Configurar servidor RADIUS no R3:**
	- Ir em R3 > CLI
	- Entrar no modo privilegiado: `enable`
	- Entrar no modo de configuração global: `configure terminal`
	- Configurar IP e chave secreta do servidor AAA RADIUS no R3:
		- Host: `radius-server host 192.168.3.2`
		- Senha: `radius-server key radiuspa55`
	- Finalizar: `end`

![[Pasted image 20250418232510.png]]
### 1.4.  Autenticação de login AAA para o acesso no R2
- **Configurar autenticação de login AAA para acesso de controle do R3:**
	- Ir em R3 > CLI
	- Entrar no modo privilegiado: `enable`
	- Entrar no modo de configuração global: `configure terminal`
	- Ativar AAA no R3: `aaa new-model`
	- Autenticação padrão: `aaa authentication login default group radius local`
	- Configurar login: `username Admin3 secret admin3pa55`	
	- Aplicar à linha de console:
		- `line console 0`
		- `login authentication default`
	- Finalizar: `end`

```hash
R3#enable
R3#configure terminal
Enter configuration commands, one per line. End with CNTL/Z.
R3(config)#aaa new-model
R3(config)#aaa authentication login default group radius local
R3(config)#username Admin3 secret admin3pa55
R3(config)#line console 0
R3(config-line)#login authentication default
R3(config-line)#end
```
![[Pasted image 20250418233429.png]]
### 1.5. Configuração as linhas vty para usar autenticação AAA
- **Configurar as linhas vty com AAA:**
	- Ir em R3 > CLI
	- Entrar no modo privilegiado: `enable`
	- Entrar no modo de configuração global: `configure terminal`
	- Criar AAA: `aaa new-model`
	- Criar método de autenticação: `aaa authentication login default group radius local`
	- Entrar na configuração das linhas VTY: `line vty 0 4
	- Aplicar o método de autenticação AAA que eu defini como **default**: `login authentication default`
	- Finalizar: `exit` > `end` 

```hash
R3#enable
R3#configure terminal
R3(config)#aaa new-model
R3(config)#aaa authentication login default group radius local
R3(config)#line vty 0 4
R3(config-line)#login authentication default
R3(config-line)#exit
R3(config)#end
````
![[Pasted image 20250418234625.png]]
### 1.6. Verificação de autenticação AAA
- **Verificar login EXEC usando servidor AAA RADIUS:**
	- Entrar no modo privilegiado: `enable`
	- Entrar no modo de configuração global: `configure terminal`
	- Criar AAA: `aaa new-model`
	- Configurar servidor AAA RADIUS:
		- Host: `radius-server host 192.168.3.2`
		- Senha: `radius-server key radiuspa55`
	- Criar método de autenticação: `aaa authentication login default group radius local`
	- Configurar usuário local: `username Admin3 secret admin3pa55`
	- Aplicar método nas interfaces de acesso:
		- Console: `line console 0` > `login authentication default` > `exit`
		- VTY: `line vty 0 4` > `login authentication default` > `exit

```hash
R2#enable
R2#configure terminal
R2(config)#aaa new-model
R2(config)#radius-server host 192.168.3.2
R2(config)#radius-server key tacacspa55
R2(config)#aaa authentication login default group radius local
R2(config)#username Admin3 secret admin3pa55
R2(config)#line console 0
R2(config-line)#login authentication default
R2(config-line)#exit
R2(config)#line vty 0 4
R2(config-line)#login authentication default
R2(config-line)#exit
2(config)#end
```
![[Pasted image 20250418235645.png]]

# Conclusão
![[Pasted image 20250419000111.png]]