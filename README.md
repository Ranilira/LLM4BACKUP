# Capa

## Título do Projeto: Sistema Inteligente de Diagnóstico de Falhas de Backup utilizando IA e Métricas do Zabbix/Veeam
## Nome do Estudante: Raniel Lira
## Curso: Engenharia de Software
## Data de Entrega: Dezembro/2025

# Resumo

Este documento apresenta a especificação detalhada de um sistema inteligente de análise de falhas de backup, baseado em métricas coletadas e processadas pelo Zabbix a partir de ambientes monitorados pelo Veeam. A solução utiliza técnicas modernas de Inteligência Artificial, como ajuste fino de modelos LLM via PEFT/LoRA, para automatizar diagnósticos, gerar relatórios RCA e apoiar decisões técnicas. O projeto aborda arquitetura, requisitos, design, stack tecnológica, normas aplicáveis e roadmap para desenvolvimento nos Portfólios I e II.

## 1. Introdução

### Contexto

Ambientes corporativos que utilizam Veeam Backup & Replication dependem de monitoramento constante para garantir integridade dos dados. O Zabbix, por meio de templates específicos, processa métricas fundamentais desses jobs, porém a análise de falhas ainda depende de intervenção humana e conhecimento especializado.

### Justificativa

A crescente complexidade das infraestruturas de backup demanda ferramentas que automatizem análises técnicas, identifiquem padrões de falha e ofereçam insights rápidos e confiáveis. Integrar IA aos dados já processados pelo Zabbix permite otimizar tempo, padronizar RCA e reduzir erros.

### Objetivos

- Objetivo Geral: Desenvolver um sistema de análise inteligente que utilize IA para diagnosticar falhas em jobs de backup do Veeam monitorados pelo Zabbix.

Objetivos Específicos:

- Coletar e armazenar métricas processadas via API do Zabbix.

- Criar microserviços para IA, coleta, API Gateway e banco.

- Treinar um modelo LLM com PEFT/LoRA para ambientes com poucos dados.

- Gerar relatórios automáticos de RCA.

- Criar dashboard web para visualização de falhas e insights.

## 2. Descrição do Projeto

### Linha de Projeto: Projetos com IA (Inteligência Artificial)

### Tema do Projeto

Sistema inteligente para diagnóstico de falhas de backup utilizando dados do Zabbix/Veeam e modelos LLM.

### Propósito e Uso Prático

Automatizar análises de falhas, reduzir tempo de diagnóstico, identificar padrões recorrentes e padronizar relatórios técnicos no departamento de TI.

### Público-Alvo

- Equipes de infraestrutura e backup

- Analistas de TI

- Empresas que utilizam Veeam + Zabbix

- Departamentos de monitoramento NOC/SOC

### Problemas a Resolver

- Diagnósticos manuais demorados

- Falta de padronização nos RCA

- Baixa previsibilidade de falhas

- Necessidade de conhecimento especializado

### Diferenciação / Ineditismo

- Ao contrário de integrações convencionais com GPT, o projeto:

- Usa dados processados pelo Zabbix, já filtrados e estruturados.

- Treina modelo próprio, local, ajustado ao ambiente real.

- Funciona com poucos dados utilizando PEFT/LoRA.

- É independente de nuvem e de custos de API.

- Opera em microserviços com escalabilidade real.

### Limitações

- O sistema não executará ações automáticas no Veeam (apenas diagnósticos).

- IA não substituirá especialistas; serve como apoio.

- Modelo LLM inicial será um mock durante o MVP.

### Normas e Legislações Aplicáveis

- LGPD (Lei 13.709/2018) – Garantia de privacidade dos dados monitorados.

- OWASP Top 10 – Aplicado à API e autenticação.

- ISO/IEC 27001 – Boas práticas de segurança.

- UNESCO – Ética em IA – Tratamento responsável de modelos e vieses.

### Métricas de Sucesso

- 90% de diagnósticos coerentes com análises humanas.

- Redução de 40% no tempo de investigação por analista.

- Dashboard responsivo com tempo de resposta < 500ms.

- Taxa de disponibilidade do sistema ≥ 99%.

# 3. Especificação Técnica
## 3.1 Requisitos de Software
### Requisitos Funcionais (RF)

RF01: Coletar dados via API do Zabbix.

RF02: Armazenar métricas em banco SQLite.

RF03: Gerar diagnóstico de IA para cada job.

RF04: Exibir dashboard com lista de jobs.

RF05: Exibir tela detalhada do job.

RF06: Gerar relatório RCA automático.

RF07: Login com autenticação JWT.

RF08: API Gateway para integração entre serviços.

RF09: Microserviço de IA modular.

Requisitos Não Funcionais (RNF)

RNF01: Arquitetura de microserviços.

RNF02: Sistema deve rodar via Docker Compose.

RNF03: Suporte a escalabilidade horizontal.

RNF04: Testes automatizados (pytest).

RNF05: Segurança OWASP Top 10.

RNF06: Interface Web responsiva.

RNF07: Tempo de resposta < 1s.

- Representação em Diagrama (Casos de Uso)

### Aderência aos Requisitos da Linha de Projeto (IA)

- O sistema atende os requisitos obrigatórios:

- Uso de modelo de IA → LLM treinada via PEFT/LoRA

- Uso de pipelines automatizados → microserviço IA

- Evidência de inferência e aprendizado

- Dashboards com dados analisados

### 3.2 Considerações de Design
Visão Inicial da Arquitetura

- API Gateway (JWT)
- Microserviço Coleta Zabbix
- Microserviço Banco SQLite
- Microserviço IA
- Frontend Web
- Padrões de Arquitetura
- Microserviços
- MVC no frontend
- Arquitetura limpa no backend

### Modelos C4

Níveis recomendados:

Contexto

Contêineres

Componentes

Código
(Posso gerar os diagramas para você.)

Mockups

Dashboard

Tela do Job

Tela de RCA
(Posso gerar no Figma para você agora.)

### Decisões e Alternativas

- Microserviços ao invés de monolito → facilita escalar IA e coleta.
- SQLite por simplicidade e portabilidade no MVP.
- LLaMA/Mistral por serem open source e leves para PEFT/LoRA.

### Critérios de Escalabilidade, Resiliência e Segurança

- Load balancing no API Gateway.
- Tolerância a falhas via containers independentes.
- Segurança via JWT e HTTPS.
- Mínimo de privilégios por serviço.

## 3.3 Stack Tecnológica
### Linguagens

- Python 3.12.3
- HTML/CSS/JS

### Frameworks

- Flask / FastAPI
- PEFT
- HuggingFace
- Tailwind/Bootstrap

### Ferramentas

- Docker Compose
- Git e GitHub
- VSCode
- pytest

### Licenciamento

- Python: PSF
- Tailwind: MIT
- HuggingFace Transformers: Apache 2.0
- LLaMA/Mistral: licenças open source proporcionais

# 3.4 Considerações de Segurança
## Riscos

- Vazamento de credenciais Zabbix
- Falhas de autenticação
- Injeção via API
- Logs com dados sensíveis

## Mitigação

- JWT
- Sanitização de entradas
- Política de mínimos privilégios
- Proteção contra brute force

## Normas e Boas Práticas

- OWASP Top 10
- LGPD
- ISO 27001

## Responsabilidade Ética

- Não armazenar informações sensíveis dos hosts
- Evitar vieses no modelo de IA
- Transparência no diagnóstico
- Consentimento do uso dos dados

# 3.5 Conformidade e Normas Aplicáveis

- LGPD — proteção e tratamento ético dos dados
- OWASP — segurança da aplicação
- UNESCO Ética em IA
- ISO/IEC 27001

# 4. Próximos Passos
## Portfólio I

- Implementar microserviços
- Configurar Docker Compose
- Criar dashboard
- Criar mock de IA
- Desenvolver coleta Zabbix

## Portfólio II

- Integrar IA real com PEFT/LoRA
- Criar previsões de falha
- Automatizar RCA
- Criar relatórios PDF
- Colocar em produção

# Marcos

- M1: Arquitetura
- M2: Coleta e BD
- M3: Dashboard
- M4: IA mock
- M5: IA real

# 5. Referências

- Documentação Zabbix
- Documentação Veeam
- PEFT / LoRA
- HuggingFace
- OpenAI – práticas recomendadas
- LGPD
- ISO/IEC 27001
- OWASP Top 10

# 6. Apêndices (Opcionais)


# 7. Avaliações de Professores
## Considerações Professor/a:

(Página 1)

## Considerações Professor/a:

(Página 2)

Considerações Professor/a:

(Página 3)
