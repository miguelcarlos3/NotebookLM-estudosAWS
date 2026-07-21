# NotebookLM-estudosAWS
# Estudos de AWS (Amazon Web Services) — Cloud Computing & Dados

## Objetivo

Assunto escolhido para o NotebookLM: **Amazon Web Services (AWS)**, com o objetivo de aprofundar os estudos em dados e cloud computing.

## Fontes do conteúdo

- [Playlist do YouTube](https://youtube.com/playlist?list=PLOF5f9_x-OYUaqJar6EKRAonJNSHDFZUm&si=QcD80uxPHAhyKpNF)
- [Vídeo 1](https://youtu.be/nOZTyuhCU2k?is=_l5n0YHE9xz-1orb)
- [Vídeo 2](https://youtu.be/j_StCjwpfmk?is=ik1K9hzTJOobAL6A)

## Prompts

**Prompt de geração de conteúdo**

Em vez de usar prompts genéricos como "faça resumos detalhados, em forma de tópicos" (que já trazia bons resultados), o prompt abaixo melhorou o desempenho dos estudos por diluir melhor a divisão do conteúdo e gerar resumos mais detalhados:

> Crie um conteúdo programático completo para aprender [ASSUNTO], do nível iniciante ao avançado. Organize por módulos e, para cada módulo, liste os tópicos mais importantes em ordem de prioridade. Destaque quais são os fundamentos essenciais que todo iniciante deve dominar primeiro.

**Prompts para revisão**

Para melhorar a capacidade de absorção, fazer exercícios pelo recurso **Studio** do NotebookLM:

> Faça exercícios para estudos com base nas fontes dos resumos.

Para estudo ativo: fazer anotações em um documento Word, depois inserir no notebook e comparar com as fontes estudadas.

> Faça questões somente sobre [CONTEÚDO ESTUDADO] do [FONTE ESTUDADA].

---

## Principais Conceitos

### Fundamentos de Cloud Computing
- **Cloud Computing (Computação em Nuvem):** entrega sob demanda de recursos de TI (como servidores e armazenamento) via internet, com precificação baseada no uso.
- **IaaS (Infraestrutura como Serviço):** fornece os blocos de construção básicos, como servidores virtuais, armazenamento e rede. O usuário gerencia o sistema operacional e as aplicações.
- **PaaS (Plataforma como Serviço):** oferece um ambiente gerenciado para desenvolvimento e implantação, removendo a necessidade de gerenciar a infraestrutura subjacente.
- **SaaS (Software como Serviço):** entrega um produto completo e pronto para uso via navegador ou aplicativo, onde o provedor gerencia toda a pilha tecnológica.
- **Modelo de Responsabilidade Compartilhada:** a AWS é responsável pela segurança *da* nuvem (infraestrutura física), enquanto o cliente é responsável pela segurança *na* nuvem (dados, configurações e SO).

### Infraestrutura Global
- **Região (Region):** localização geográfica física que agrupa vários centros de dados isolados.
- **Zona de Disponibilidade (AZ):** um ou mais centros de dados discretos dentro de uma região, com energia e rede redundantes, projetados para isolamento de falhas.
- **Edge Location (Ponto de Presença):** pequenos centros de dados em grandes cidades usados para cache de conteúdo (via CloudFront) e redução de latência.

### Serviços de Segurança e Identidade
- **IAM (Identity and Access Management):** serviço central para controlar quem pode acessar quais recursos na conta AWS.
- **MFA (Autenticação de Múltiplos Fatores):** camada extra de proteção além da senha.
- **Princípio do Privilégio Mínimo:** conceder apenas as permissões estritamente necessárias.
- **Security Groups:** firewalls virtuais no nível da instância (recurso).
- **NACLs (Network ACLs):** firewalls que controlam o tráfego no nível da sub-rede.

### Serviços de Computação e Armazenamento
- **Amazon EC2:** servidores virtuais escaláveis com controle total sobre o sistema operacional.
- **AWS Lambda:** computação serverless que executa código em resposta a eventos, cobrando por milissegundos de processamento.
- **Amazon S3:** armazenamento de objetos altamente durável, usado para arquivos, backups e hospedagem de sites estáticos.
- **Amazon EBS:** discos virtuais de alta performance anexados a instâncias EC2 para armazenamento persistente.

### Redes e Bancos de Dados
- **Amazon VPC:** rede virtual logicamente isolada onde os recursos AWS são lançados.
- **Subnet:** divisão de uma VPC; subnets públicas têm acesso direto à internet, privadas não.
- **Amazon RDS:** serviço gerenciado para bancos de dados relacionais (SQL).
- **Amazon DynamoDB:** banco de dados NoSQL gerenciado de alta performance, com latência de milissegundos em qualquer escala.

### Monitoramento e Gestão de Custos
- **Amazon CloudWatch:** monitoramento de métricas, logs e alarmes.
- **AWS CloudTrail:** registra todas as chamadas de API na conta, para auditoria e governança.
- **AWS Budgets:** planejamento e monitoramento de custos, com alertas de limites financeiros.
- **Trusted Advisor:** recomendações automatizadas de economia, performance e segurança.

### Tendências de IA (Contexto 2026)
- **Amazon Bedrock:** serviço gerenciado que disponibiliza modelos de fundação (FMs) para construir aplicações de IA Generativa via API.
- **Agentes de IA (Agentic AI):** sistemas autônomos que decompõem pedidos complexos em tarefas e as executam usando ferramentas integradas.

---

## Resumo

### 1. O Paradigma da Computação em Nuvem e o Modelo AWS

A computação em nuvem é a entrega sob demanda de recursos de TI — como poder computacional, armazenamento e bancos de dados — pela internet, com precificação pay-as-you-go. Em vez de investir em infraestrutura física local (On-Premises), as empresas acessam recursos elásticos de provedores como a AWS.

**As Seis Vantagens Principais:**
1. Trocar despesas de capital fixas (CapEx) por despesas operacionais variáveis (OpEx).
2. Beneficiar-se de economias de escala massivas que reduzem custos.
3. Parar de adivinhar a capacidade necessária, eliminando servidores ociosos.
4. Aumentar a velocidade e agilidade para lançar recursos em minutos.
5. Focar no negócio principal em vez da manutenção de data centers.
6. Ganhar alcance global em minutos, implantando aplicações em várias regiões simultaneamente.

**Modelos de serviço:** IaaS (blocos básicos de infraestrutura) → PaaS (remove a gestão de hardware) → SaaS (aplicações prontas para o usuário final).

### 2. Arquitetura de Infraestrutura Global

- **Regiões:** locais físicos ao redor do mundo (atualmente 39 regiões) que agrupam centros de dados isolados. Escolha baseada em latência, conformidade legal e custo.
- **Zonas de Disponibilidade (AZs):** cada região tem três ou mais AZs, com energia e rede redundantes conectadas por fibra óptica de ultra-baixa latência, projetadas para isolamento de falhas.
- **Pontos de Presença (Edge Locations):** mais de 750 locais em 2026, usados pelo Amazon CloudFront para cache de conteúdo e redução de latência.

### 3. Serviços Core: Computação e Armazenamento

- **Amazon EC2:** instâncias configuráveis (SO, CPU, memória, armazenamento). Usa o sistema AWS Nitro para entregar quase 100% dos recursos de hardware ao cliente.
- **AWS Lambda:** serverless orientado a eventos, cobrando por milissegundos de execução — ideal para tarefas rápidas como processamento de imagens.
- **Amazon S3:** armazenamento de objetos com durabilidade de "onze noves" (99,999999999%); em 2026 armazena mais de 350 trilhões de objetos. Classes como Standard e Glacier.

### 4. Redes e Bancos de Dados Gerenciados

- **Amazon VPC:** seção logicamente isolada da nuvem AWS, com sub-redes públicas (Internet Gateway) e privadas (NAT Gateway).
- **Amazon RDS:** bancos relacionais (MySQL, PostgreSQL) com backups, correções de segurança e alta disponibilidade via Multi-AZ automatizados.
- **Amazon DynamoDB:** NoSQL gerenciado, performance consistente de milissegundos em qualquer escala, suportando picos massivos de tráfego.

### 5. Segurança e Conformidade (Prioridade Zero)

Modelo de Responsabilidade Compartilhada: AWS cuida da segurança *da* nuvem (data centers, cabos, hardware); o cliente cuida da segurança *na* nuvem (dados, SO, identidades).

- **IAM:** gerenciamento central de usuários e acessos — Princípio do Privilégio Mínimo e MFA obrigatórios.
- **Proteção de Perímetro:** AWS Shield (DDoS) e AWS WAF (firewall de aplicações web contra exploits como SQL Injection).

### 6. Inteligência Artificial e Tendências de 2026

- **Amazon Bedrock:** disponibiliza modelos de fundação (Claude da Anthropic, Llama da Meta, família Nova da Amazon) via API única, sem gerenciar infraestrutura.
- **Bedrock Agents:** sistemas autônomos que decompõem pedidos complexos, chamam APIs e executam fluxos de tarefas com raciocínio entre cada passo.
- **Custom Silicon:** chips próprios como Trainium3 (treinamento de IA, +40% performance) e Inferentia2 (inferência de baixo custo), reduzindo dependência de GPUs externas.

### 7. Governança Financeira e Aprendizado

- **Gestão de Custos:** AWS Budgets (alertas de gastos), Cost Explorer (tendências), Trusted Advisor (recomendações automatizadas).
- **AWS Free Tier (2026):** até $200 em créditos para novos usuários testarem mais de 90 serviços por até 6 meses, com proteção que fecha a conta se os créditos acabarem.
- **Certificações:** começa com AWS Cloud Practitioner (conceitos de negócios e nuvem), progride para Associado (Arquitetura, Desenvolvimento, SysOps) e Especialista (IA, Segurança, Redes).

---

## Link do Notebook
[NotebookLM — Estudos de AWS](https://notebooklm.google.com/notebook/8c3998ad-d3cc-49f9-bd19-fe60dce84590)


[NotebookLM — Estudos de AWS](https://notebooklm.google.com/notebook/8c3998ad-d3cc-49f9-bd19-fe60dce84590)
