# Documentação Técnica - Laboratório AUTENTICAÇÃO SERVIDOR TACACS E RADIUS

## Autenticação AAA com TACACS+ e RADIUS
##### Objetivo Geral
Configurar e validar mecanismos de autenticação (AAA) baseados em servidores TACACS+ e RADIUS.
## Tabelas de endereçamento
#### Roteadores
- Dispositivo: R1

| Interface    | Endereço IP<br><br> | Máscara de Sub-Rede<br><br> | Gateway padrão<br><br> | Porta do Switch<br><br> |
| ------------ | ------------------- | --------------------------- | ---------------------- | ----------------------- |
| G0/1         | 192.168.1.1         | 255.255.255.0<br><br>       | N/D                    | S1 F0/1<br><br>         |
| S0/0/0 (DCE) | 10.1.1.2            | 255.255.255.252<br><br>     | N/D                    | N/D                     |

- Dispositivo: R2

| Interface    | Endereço IP         | Máscara de Sub-Rede     | Gateway padrão | Porta do Switch |
| ------------ | ------------------- | ----------------------- | -------------- | --------------- |
| G0/0         | 192.168.2.1<br><br> | 255.255.255.0           | N/D<br><br>    | S2 F0/2<br><br> |
| S0/0/0       | 10.1.1.1<br><br>    | 255.255.255.252<br><br> | N/D<br><br>    | N/D<br><br>     |
| S0/0/1 (DCE) | 10.2.2.1<br><br>    | 255.255.255.252<br><br> | N/D<br><br>    | N/D<br><br>     |

- Dispositivo: R3

| Interface    | Endereço IP | Máscara de Sub-Rede | Gateway padrão | Porta do Switch |
| ------------ | ----------- | ------------------- | -------------- | --------------- |
| G0/1<br><br> | 192.168.3.1 | 255.255.255.0       | N/D            | S3 F0/5         |
| S0/0/1       | 10.2.2.2    | 255.255.255.252     | N/D            | N/D             |

#### Servidores

| Dispositivo | Interface             | Endereço IP         | Máscara de Sub-Rede | Gateway padrão      | Porta do Switch |
| ----------- | --------------------- | ------------------- | ------------------- | ------------------- | --------------- |
| TACACS+     | Placa de rede<br><br> | 192.168.2.2<br><br> | 255.255.255.0       | 192.168.2.1<br><br> | S2 F0/6<br><br> |
| RADIUS      | Placa de rede<br><br> | 192.168.3.2<br><br> | 255.255.255.0       | 192.168.3.1<br>     | S3 F0/1<br><br> |

#### PCs

| Dispositivo | Interface | Endereço IP         | Máscara de Sub-Rede   | Gateway padrão | Porta do Switch |
| ----------- | --------- | ------------------- | --------------------- | -------------- | --------------- |
| PC-A        | NIC       | 192.168.1.3<br><br> | 255.255.255.0<br><br> | 192.168.1.1    | S1 F0/2<br><br> |
| PC-B        | NIC       | 192.168.2.3<br><br> | 255.255.255.0<br><br> | 192.168.2.1    | S2 F0/1<br><br> |
| PC-C        | NIC       | 192.168.3.3<br><br> | 255.255.255.0<br><br> | 192.168.3.1    | S3 F0/18        |

---

# Parte 1 - Configuração AAA usando TACACS+ no R2
### 1.1. Testar conectividade
### 1.2. Configuração de entrada de banco de dados de backup Admin
### 1.3. Configuração TACACS+
### 1.4. Configuração TACACS+ no R2
### 1.5. Autenticação de login AAA para acesso no R2
### 1.6. Configuração das linhas vty para usar  autenticação AAA definido
### 1.7. Verificar autenticação AAA


# Parte 2 - Configuração AAA usando RADIUS no R3
### 1.1. Configuração da base de dados de backup Admin
### 1.2. Configuração do servidor RADIUS
### 1.3. Configuração RADIUS no R2
### 1.4.  Autenticação de login AAA para o acesso no R2.
### 1.5. Configuração as linhas vty para usar autenticação AAA
### 1.6. Verificação de autenticação AAA


# Conclusão