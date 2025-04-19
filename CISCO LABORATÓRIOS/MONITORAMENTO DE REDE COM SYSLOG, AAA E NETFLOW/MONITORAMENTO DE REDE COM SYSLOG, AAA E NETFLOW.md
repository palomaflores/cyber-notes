# Documentação Técnica – Laboratório Cisco: Monitoramento de Rede com Syslog, AAA e NetFlow
##### Objetivo Geral
Este laboratório tem como objetivos principais:
-  Utilizar o **Syslog** para capturar arquivos de log de múltiplos dispositivos de rede.
- Observar os registros de **acesso de usuários AAA** (Autenticação, Autorização e Contabilidade).
- Analisar informações de tráfego coletadas através do **NetFlow**.

# Parte 1 - Usar Syslog para capturar arquivos de log

| Níveis  | Eventos      |
| ------- | ------------ |
| Nível 0 | Emergências  |
| Nível 1 | Alertas      |
| Nível 2 | Críticos     |
| Nível 3 | Erros        |
| Nível 4 | Avisos       |
| Nível 5 | Notificações |
| Nível 6 | Informativos |
| Nível 7 | Depuração    |
- **Obs: Níveis mais baixos representam eventos mais graves.**
### 1.1. Ativar Syslog no servidor
- Ir em Syslog Server > Services > SYSLOG
- Ativar o Syslog

### 1.2. Gerar logs de depuração (Nível 7)
- **Gerar mensagens de nível de depuração (nível 7) para serem enviados ao servidor syslog:**
	- Ir em R1 > CLI
	- Entrar no modo privilegiado: `enable`
	- Habilitar depuração EIGRP: `debug eigrp packets`
	- Verificar entradas de log no servidor syslog
	- Desligar syslog
	- Sair de R1

```hash
R1>enable
R1#degub eirgp packets
R1#exit
```

![[Pasted image 20250419012947.png]]
![[Pasted image 20250419013231.png]]
# Parte 2 - Observar registro de acesso do usuário
- **Fazer login no R2 e exibir entradas de log relacionadas a esse login:**
	- Ir em Syslog Server > Desktop > AAA Accounting
	- Ir em R2 > CLI
	- Username: `analyste cyberops`
	- Password: `analyste cyberops`
	- Comando: `logout`

```bash
Username: analyste cyberops
Password: analyste cyberops
```

![[Pasted image 20250419014304.png]]
![[Pasted image 20250419014343.png]]
# Parte 3 - Visualizar informações do NetFlow
- **Configurar firewall como um NetFlow exporter:**
	- Ir em Syslog Server > Fechar Registros Contábeis AAA
	- Aba Desktop > Selecionar Netflow Colletor > Ativar serviço Netflow Colletor

![[Pasted image 20250419014715.png]]

- **Usar qualquer PC:**
	- PC1.1 > Desktop > Prompt de Comando
	- Comando: `ping 209.165.200.194` (IP do Corp Web Server)

![[Pasted image 20250419015234.png]]

- **Voltar ao NetFlow Collector:**
	- O gráfico de pizza será atualizado automaticamente
	- O gráfico mostrará os novos fluxos de tráfego, como tráfego ICMP gerado pelo comando ping

![[Pasted image 20250419015413.png]]

![[Pasted image 20250419015503.png]]