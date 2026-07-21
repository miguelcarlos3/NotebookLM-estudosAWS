# Caderno Temático — AWS (Amazon Web Services) no NotebookLM

Projeto desenvolvido como parte do desafio da DIO: uso de Inteligência Artificial (NotebookLM) como ferramenta de aprendizagem ativa para construir um Caderno Temático sobre um assunto de interesse.

---

## 1. Contexto e Objetivos

**Assunto escolhido:** Amazon Web Services (AWS) — fundamentos de Cloud Computing e Dados.

**Objetivos de estudo:**
- Aprofundar o conhecimento em computação em nuvem (cloud computing), com foco em serviços AWS voltados a dados.
- Construir uma base sólida do nível iniciante ao avançado, organizada por módulos, para orientar uma trilha de certificação futura.
- Praticar estudo ativo: gerar exercícios, tirar dúvidas e comparar anotações próprias com as fontes originais usando o NotebookLM.

---

## 2. Curadoria de Fontes

Fontes utilizadas e carregadas no NotebookLM:

1. [Playlist do YouTube sobre AWS](https://youtube.com/playlist?list=PLOF5f9_x-OYUaqJar6EKRAonJNSHDFZUm&si=QcD80uxPHAhyKpNF)
2. [Vídeo — introdução/conceitos AWS](https://youtu.be/nOZTyuhCU2k?is=_l5n0YHE9xz-1orb)
3. [Vídeo — aprofundamento em serviços AWS](https://youtu.be/j_StCjwpfmk?is=ik1K9hzTJOobAL6A)

> **Nota:** as fontes atuais são em formato de vídeo (YouTube). O desafio recomenda fontes abertas em texto ou PDF (ex: documentação oficial da AWS, whitepapers); esse é um ponto de melhoria para uma próxima iteração deste caderno.

---

## 3. Engenharia de Prompts e "Cicatrizes" (Troubleshooting)

### Prompt inicial (menos eficaz)
```
Faça resumos detalhados, em forma de tópicos.
```
**Resultado:** gerava resumos razoáveis, mas pouco estruturados — misturava níveis de dificuldade e não priorizava o que era fundamental para quem está começando.

### Prompt refinado (usado na versão final)
```
Crie um conteúdo programático completo para aprender [ASSUNTO], do nível
iniciante ao avançado. Organize por módulos e, para cada módulo, liste os
tópicos mais importantes em ordem de prioridade. Destaque quais são os
fundamentos essenciais que todo iniciante deve dominar primeiro.
```
**Por que funcionou melhor:** diluiu melhor a divisão do conteúdo em módulos, forçou a IA a hierarquizar os tópicos por prioridade e deixou claro o que é essencial vs. avançado — resultando em resumos mais completos e didáticos.

### Prompts de revisão e estudo ativo
```
Faça exercícios para estudos com base nas fontes dos resumos.
```
```
Faça questões somente sobre [CONTEÚDO ESTUDADO] do [FONTE ESTUDADA].
```
**Dificuldade encontrada:** pedir exercícios de forma genérica ("faça exercícios sobre AWS") gerava questões muito abrangentes ou repetidas. A solução foi restringir sempre o escopo a um conteúdo e uma fonte específicos, o que exigiu ir testando o prompt aos poucos até chegar nessa formulação mais restrita.

**Prática de validação:** as anotações próprias eram registradas em um documento Word e depois inseridas de volta no NotebookLM para comparação direta com as fontes originais, funcionando como uma checagem de precisão do próprio entendimento.

---

## 4. Miniguia de Estudo (Entrega Final)

### 4.1 Resumo Estruturado

#### Módulo 1 — O Paradigma da Computação em Nuvem e o Modelo AWS
A computação em nuvem é a entrega sob demanda de recursos de TI — poder computacional, armazenamento e bancos de dados — pela internet, com precificação pay-as-you-go. Em vez de investir em infraestrutura física local (On-Premises), as empresas acessam recursos elásticos de provedores como a AWS.

**As Seis Vantagens Principais:**
1. Trocar despesas de capital fixas (CapEx) por despesas operacionais variáveis (OpEx).
2. Beneficiar-se de economias de escala massivas que reduzem custos.
3. Parar de adivinhar a capacidade necessária, eliminando servidores ociosos.
4. Aumentar a velocidade e agilidade para lançar recursos em minutos.
5. Focar no negócio principal em vez da manutenção de data centers.
6. Ganhar alcance global em minutos, implantando aplicações em várias regiões simultaneamente.

**Modelos de serviço:** IaaS (blocos básicos de infraestrutura) → PaaS (remove a gestão de hardware) → SaaS (aplicações prontas para o usuário final).

#### Módulo 2 — Arquitetura de Infraestrutura Global
- **Regiões:** locais físicos ao redor do mundo (atualmente 39 regiões) que agrupam centros de dados isolados. Escolha baseada em latência, conformidade legal e custo.
- **Zonas de Disponibilidade (AZs):** cada região tem três ou mais AZs, com energia e rede redundantes conectadas por fibra óptica de ultra-baixa latência, projetadas para isolamento de falhas.
- **Pontos de Presença (Edge Locations):** mais de 750 locais em 2026, usados pelo Amazon CloudFront para cache de conteúdo e redução de latência.

#### Módulo 3 — Computação e Armazenamento
- **Amazon EC2:** instâncias configuráveis (SO, CPU, memória, armazenamento). Usa o sistema AWS Nitro para entregar quase 100% dos recursos de hardware ao cliente.
- **AWS Lambda:** serverless orientado a eventos, cobrando por milissegundos de execução — ideal para tarefas rápidas como processamento de imagens.
- **Amazon S3:** armazenamento de objetos com durabilidade de "onze noves" (99,999999999%); em 2026 armazena mais de 350 trilhões de objetos. Classes como Standard e Glacier.
- **Amazon EBS:** discos virtuais de alta performance anexados a instâncias EC2 para armazenamento persistente.

#### Módulo 4 — Redes e Bancos de Dados Gerenciados
- **Amazon VPC:** seção logicamente isolada da nuvem AWS, com sub-redes públicas (Internet Gateway) e privadas (NAT Gateway).
- **Amazon RDS:** bancos relacionais (MySQL, PostgreSQL) com backups, correções de segurança e alta disponibilidade via Multi-AZ automatizados.
- **Amazon DynamoDB:** NoSQL gerenciado, performance consistente de milissegundos em qualquer escala, suportando picos massivos de tráfego.

#### Módulo 5 — Segurança e Conformidade (Prioridade Zero)
Modelo de Responsabilidade Compartilhada: a AWS cuida da segurança *da* nuvem (data centers, cabos, hardware); o cliente cuida da segurança *na* nuvem (dados, SO, identidades).
- **IAM:** gerenciamento central de usuários e acessos — Princípio do Privilégio Mínimo e MFA obrigatórios.
- **Proteção de Perímetro:** AWS Shield (DDoS) e AWS WAF (firewall de aplicações web contra exploits como SQL Injection).

#### Módulo 6 — Inteligência Artificial e Tendências de 2026
- **Amazon Bedrock:** disponibiliza modelos de fundação (Claude da Anthropic, Llama da Meta, família Nova da Amazon) via API única, sem gerenciar infraestrutura.
- **Bedrock Agents:** sistemas autônomos que decompõem pedidos complexos, chamam APIs e executam fluxos de tarefas com raciocínio entre cada passo.
- **Custom Silicon:** chips próprios como Trainium3 (treinamento de IA, +40% performance) e Inferentia2 (inferência de baixo custo), reduzindo dependência de GPUs externas.

#### Módulo 7 — Governança Financeira e Certificações
- **Gestão de Custos:** AWS Budgets (alertas de gastos), Cost Explorer (tendências), Trusted Advisor (recomendações automatizadas).
- **AWS Free Tier (2026):** até $200 em créditos para novos usuários testarem mais de 90 serviços por até 6 meses, com proteção que fecha a conta se os créditos acabarem.
- **Certificações:** começa com AWS Cloud Practitioner (conceitos de negócios e nuvem), progride para Associado (Arquitetura, Desenvolvimento, SysOps) e Especialista (IA, Segurança, Redes).

---

### 4.2 Glossário

| Termo | Definição |
|---|---|
| **Cloud Computing** | Entrega sob demanda de recursos de TI (servidores, armazenamento) via internet, com precificação baseada no uso. |
| **IaaS** | Infraestrutura como Serviço — blocos básicos (servidores, storage, rede); usuário gerencia SO e aplicações. |
| **PaaS** | Plataforma como Serviço — ambiente gerenciado para desenvolvimento, sem gerenciar infraestrutura subjacente. |
| **SaaS** | Software como Serviço — produto pronto para uso, provedor gerencia toda a pilha tecnológica. |
| **Modelo de Responsabilidade Compartilhada** | AWS cuida da segurança da nuvem (infraestrutura física); cliente cuida da segurança na nuvem (dados, configurações, SO). |
| **Região (Region)** | Localização geográfica física que agrupa vários centros de dados isolados. |
| **Zona de Disponibilidade (AZ)** | Um ou mais centros de dados discretos dentro de uma região, com energia e rede redundantes. |
| **Edge Location** | Pequenos centros de dados em grandes cidades, usados para cache de conteúdo (CloudFront) e redução de latência. |
| **IAM** | Identity and Access Management — controla quem acessa quais recursos na conta AWS. |
| **MFA** | Autenticação de Múltiplos Fatores — camada extra de proteção além da senha. |
| **Princípio do Privilégio Mínimo** | Conceder apenas as permissões estritamente necessárias para uma tarefa. |
| **Security Groups** | Firewalls virtuais no nível da instância (recurso). |
| **NACLs** | Firewalls que controlam o tráfego no nível da sub-rede. |
| **Amazon EC2** | Servidores virtuais escaláveis, com controle total sobre o sistema operacional. |
| **AWS Lambda** | Computação serverless que executa código em resposta a eventos, cobrando por milissegundos. |
| **Amazon S3** | Armazenamento de objetos altamente durável, usado para arquivos, backups e sites estáticos. |
| **Amazon EBS** | Discos virtuais de alta performance anexados a instâncias EC2. |
| **Amazon VPC** | Rede virtual logicamente isolada onde os recursos AWS são lançados. |
| **Subnet** | Divisão de uma VPC; pública (acesso à internet) ou privada (sem acesso direto). |
| **Amazon RDS** | Serviço gerenciado para bancos de dados relacionais (SQL). |
| **Amazon DynamoDB** | Banco de dados NoSQL gerenciado, de alta performance e baixa latência em qualquer escala. |
| **Amazon CloudWatch** | Monitoramento de métricas, logs e alarmes. |
| **AWS CloudTrail** | Registro de todas as chamadas de API na conta, para auditoria e governança. |
| **AWS Budgets** | Ferramenta de planejamento e monitoramento de custos, com alertas de limites. |
| **Trusted Advisor** | Consultor automatizado com recomendações de economia, performance e segurança. |
| **Amazon Bedrock** | Serviço gerenciado que disponibiliza modelos de fundação (FMs) para IA Generativa via API. |
| **Agentic AI (Agentes de IA)** | Sistemas autônomos que decompõem pedidos complexos em tarefas e as executam com ferramentas integradas. |

---

### 4.3 Prompts Reutilizáveis (para futuras revisões)

**Gerar conteúdo programático sobre um novo assunto:**
```
Crie um conteúdo programático completo para aprender [ASSUNTO], do nível
iniciante ao avançado. Organize por módulos e, para cada módulo, liste os
tópicos mais importantes em ordem de prioridade. Destaque quais são os
fundamentos essenciais que todo iniciante deve dominar primeiro.
```

**Gerar exercícios de fixação a partir das fontes:**
```
Faça exercícios para estudos com base nas fontes dos resumos.
```

**Restringir o escopo das questões (evita perguntas genéricas demais):**
```
Faça questões somente sobre [CONTEÚDO ESTUDADO] do [FONTE ESTUDADA].
```

**Fluxo de estudo ativo recomendado:**
1. Gerar o conteúdo programático com o prompt de módulos.
2. Fazer anotações próprias em um documento Word enquanto estuda.
3. Inserir as anotações de volta no NotebookLM e comparar com as fontes originais.
4. Gerar exercícios restritos ao conteúdo/fonte específicos para validar o aprendizado.

---

## Link do Notebook
[NotebookLM — Caderno Temático AWS](https://notebooklm.google.com/notebook/8c3998ad-d3cc-49f9-bd19-fe60dce84590)

[NotebookLM — Caderno Temático AWS](https://notebooklm.google.com/notebook/8c3998ad-d3cc-49f9-bd19-fe60dce84590)
