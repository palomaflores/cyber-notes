# Tríade CIA
**Cibersegurança** é a prática de proteger redes, dispositivos e dados contra acesso não autorizado ou exploração criminosa, garantindo **confidencialidade, integridade e disponibilidade** das informações.
Ex: Usar senhas fortes ajuda a garantir a confidencialidade.

- **Confidencialidade** - Só as pessoas autorizadas podem acessar as informações.
- **Integridade** - Garante que a informação não seja alterada sem permissão.
- **Disponibilidade** - Garante que as informações, sistemas e recursos estejam disponíveis quando necessário. 

## Como a integridade funciona na prática?
- Hash - É uma "impressão digital" única para cada informação. Se algo for mudar, o hash também muda, revelando que houve uma alteração.
- Assinatura digital - É como uma assinatura física, mas digital. Ela usa criptografia para verificar a autenticidade da informação e do remetente, garantindo que não houve falsificação.
- MAC (Código de Autenticação de Mensagem) - É como um selo inviolável que, ao ser rompido, indica que a mensagem foi alterada.
- Cerificado Digital - Funciona como uma identidade online para as pessoas, sites ou empresas. Garante que eu estou interagindo com quem realmente diz ser, protegendo contra fraudes e garantindo a integridade da comunicação.

Ex: Ao baixar um software, a integridade garante que o arquivo baixado é o mesmo disponibilizado pelo desenvolvedor, sem nenhuma alteração maliciosa.

## Como se aplica a integridade em um sistema real?
##### Cenário
Em uma escola o sistema de notas armazena as notas dos alunos durante o semestre. É crucial que elas não sejam alteradas indevidamente.

##### Aplicando a integridade
1. Hashing: Ao inserir uma nota no sistema, um "hash" **ÚNICO** é gerado para ela, funcionando como uma impressão digital da nota.
2. Armazenamento do hash: O hash da nota é armazenado junto com a nota em um local separado e seguro.
3. Verificação: Ao acessar a nota depois, o sistema gera um novo hash e compara com o primeiro hash armazenado. Se eles não forem idênticos, significa que a nota foi alterada.

##### Benefícios
- Confiabilidade: A escola garante que as notas dos alunos são confiáveis e não foram adulteradas.
- Responsabilidade: Qualquer alteração nas notas será detectada, permitindo identificar o responsável pela alteração. 

## Tipos de ameaças
**Agente de ameaças** é qualquer pessoa ou grupo que represente um risco à segurança. As ameaças podem ser internas ou externas:
- **Ameaças internas** - São pessoas de dentro da organização (funcionários, ex-funcionários, fornecedores ou parceiros de negócios). Elas podem ser acidentais ou intencionais.

Ex: Um funcionário acessando um link malicioso

- **Ameaças externas** - São pessoas de fora da organização tentando obter acesso a ativos privados.

Ex: Phishing; Hackers; Ransomware

Os analistas de segurança protegem a organização e seus usuários contra diversos tipos de ameaças (internas e externas). E quando um ameaça passa, eles atuam para remediar a situação e reduzir os danos.
As equipes de segurança:
- Protegem contra ameaças externas e internas;
- Garantem o cumprimento de **normas regulatórias**, evitando multas e auditorias;
- Mantêm a **continuidade dos negócios**, mesmo após incidentes;
- Ajudam a **reduzir custos** com recuperação de danos;
- **Preservam a confiança na marca**, essencial para a reputação e receita.

## Responsabilidades de um analista de cibersegurança
1. **Proteger computadores e redes**
    - Monitorar a rede interna da organização
    - Identificar e responder rapidamente a ameaças
    - Participar de testes de invasão para encontrar e corrigir vulnerabilidades

2. **Prevenir ameaças proativamente**
    - Trabalhar com equipes de TI para instalar softwares de proteção
    - Apoiar o desenvolvimento seguro de software e hardware, garantindo que produtos atendam aos requisitos de segurança

3. **Realizar auditorias de segurança**
    - Verificar registros e práticas de segurança
    - Garantir que informações sensíveis, como senhas, estejam protegidas e acessíveis apenas a quem precisa

# Habilidades técnicas
Algumas habilidades técnicas essenciais para profissionais de segurança cibernética:
- **Linguagens de programação**
	- Automatizar tarefas repetitivas
	- Pesquisar dados para encontrar ameaças
	- Identificar padrões de segurança

- **Ferramentas SIEM (Gerenciamento de eventos e informações de segurança)**
	- Coletar e analisar logs de eventos (como logins incomuns)
	- Monitorar e detectar ameaças com eficiência

- **IDS (Sistemas de Detecção de Intrusão)**
	- Monitorar redes e sistemas
	- Emitir alertas de possíveis intrusões ou comportamentos suspeitos

- **Conhecimento do cenário de ameaças**
	- Se manter atualizado permite criar defesas mais eficazes e reagir a novas ameaças

- **Resposta a incidentes**
	- Seguir procedimentos definidos para investigar, conter e corrigir ataques em andamento


## Porque a segurança é importante?
1. A proteção de ativos físicos e digitais é essencial para organizações e governos.

2.  A segurança garante a continuidade dos negócios, protege a reputação da organização e reforça a confiança do usuário.

3. Violações de dados afetam todos: empresas, clientes, fornecedores e usuários.

4. Informações sensíveis como **PII** (informações pessoais) e **SPII** (informações altamente confidenciais, como dados financeiros, médicos e biométricos) são alvos principais de ataques.

5. Um vazamento de SPII pode levar a roubo de identidade e fraude financeira.

6. Profissionais da área ajudam a garantir a confidencialidade, integridade e acesso seguro às informações.

#CYBER 