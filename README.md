# Agente de Inteligência de Mercado Toqan

Sistema avançado de inteligência de mercado e qualificação desenvolvido com **engenharia de prompts, automação assistida por IA (Toqan, IA do Grupo Prosus) e integração direta de dados via API**, criado para transformar o processo de qualificação de leads em um fluxo investigativo estruturado, auditável e altamente comercial.

[![LinkedIn](https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/maria-luiza-moraes-98a6b22a8/)
[![GitHub](https://img.shields.io/badge/GitHub-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/marialuizasm21)

---

## Skills Técnicas Aplicadas

<div align="center">

![SQL](https://img.shields.io/badge/SQL-4479A1?style=for-the-badge&logo=mysql&logoColor=white)
![Metabase](https://img.shields.io/badge/Metabase-509EE3?style=for-the-badge&logo=metabase&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black)
![Google Sheets](https://img.shields.io/badge/Google_Sheets-34A853?style=for-the-badge&logo=googlesheets&logoColor=white)
![HubSpot](https://img.shields.io/badge/HubSpot-FF7A59?style=for-the-badge&logo=hubspot&logoColor=white)
![OpenAI](https://img.shields.io/badge/OpenAI-412991?style=for-the-badge&logo=openai&logoColor=white)
![Regex](https://img.shields.io/badge/Regex-000000?style=for-the-badge)
![GitHub Repo](https://img.shields.io/badge/GitHub-181717?style=for-the-badge&logo=github&logoColor=white)

</div>

---

## O Desafio vs. A Solução

**O Problema:** O processo de qualificação era 100% manual, repetitivo e fragmentado. Qualificadores precisavam abrir Metabase, HubSpot, Google e redes sociais para investigar um único lead, levando de 25 a 40 minutos. No Metabase, a análise exigia conhecimento de filtros complexos e muito tempo. Além disso, o preenchimento manual campo por campo na planilha gerava erros de formatação e falhas na importação para o CRM.

**A Solução:** Para acabar com o trabalho manual e repetitivo, construí um agente de inteligência utilizando o **Toqan (plataforma de IA do Grupo Prosus)**. O agente se conecta diretamente ao Metabase via API, extrai dados reais em tempo real de acordo com as informações do produtor (o que contextualiza o histórico e a maturidade comercial) e exporta automaticamente 24 campos higienizados e validados.

---

## 🛠️ Arquitetura e Engenharia do Agente

### 1. Integração de Dados Avançada: API, SQL e Metabase
A verdadeira inteligência transacional do agente não vem apenas do LLM, mas da ponte técnica construída com o banco de dados.
* **Orquestração via API (Toqan):** O agente utiliza a infraestrutura de IA do Grupo Prosus para acessar diretamente os dados do Metabase. Ele recebe a intenção no chat, aciona as consultas parametrizadas e devolve os dados brutos para interpretação.
* **Construção de Queries Otimizadas (SQL):** Desenvolvimento de lógicas em SQL para buscar, cruzar e somar dados de volume transacional (GMV), ingressos vendidos e ticket médio.
* **Visão Panorâmica do Lead:** A IA varre, identifica e agrupa o histórico de todos os IDs de um mesmo produtor simultaneamente, traduzindo dados brutos de banco de dados em um resumo narrativo claro.

### 2. Ingestão e Processamento Anti-Ruído
* **Sanitização Base:** O agente faz o parsing do texto bruto de CRMs, eliminando automaticamente marcadores de sistema inúteis.
* **Proteção de Contatos Original:** Algoritmos garantem que o contato estratégico mapeado não seja sobrescrito por decisores secundários identificados nos logs.

### 3. Matriz de Inteligência de Produto (Classificação de Demandas)
O agente mapeia as dores do lead e classifica a demanda internamente para direcionar a abordagem:
* **Atendida Nativamente:** Destaca soluções prontas (ex: *Afiliados, Cortesia em Massa*) para gerar valor sem custo extra.
* **Condicional / Alternativa:** Identifica cenários que exigem contratos específicos (*ex: Smart POS, Assento Marcado*).
* **Não Atendida:** Registra limitações de escopo de forma transparente no dossiê técnico.

### 4. Modelo Preditivo e Regras de Negócio Críticas
* **Cálculo Ponderado:** Estimativa ponderada de Ticket e Público caso o produtor gerencie eventos de portes muito diferentes.
* **Zero Alucinação:** Tolerância zero para dados fictícios. A orientação do prompt bloqueia inferências; campo sem dado validado é igual a campo vazio.

---

## 🔒 Painel de Validação e Mapeamento de Dados

O processo de exportação conta com um ciclo rigoroso de auditoria. Após a IA extrair e estruturar os dados em tempo real, o agente busca a linha do lead, aguarda a aprovação e analisa 24 campos. Se houver um único erro de formatação, **a exportação é travada**.

### Critérios de Sanitização (Regex & Menus Fixos)
* **CNPJ:** Conversão para número puro (sem pontuação).
* **Telefone:** Máscara estrita no padrão `(XX) XXXXX-XXXX`.
* **Estado:** Formato obrigatório `Nome do Estado (UF)`.
* **Métricas Financeiras/Volumétricas:** Extração numérica pura.
* **Menus Fechados:** Trava de opções exatas para *Segmento*, *Frequência*, *Demandas Ferramentais* e *Plataforma Concorrente*.

---

## 🚀 Resultados e Impacto

* **Zero Digitação Manual:** Fim absoluto do trabalho repetitivo de preencher planilhas campo a campo.
* **Redução de 50% no Tempo de Qualificação:** O SLA do processo caiu de ~40 para ~20 minutos por lead, impulsionado pela automação e busca de dados em tempo real via API.
* **Democratização do Acesso a Dados:** A equipe de LDR agora acessa insights complexos de SQL e Metabase em linguagem natural, sem precisar dominar ferramentas de banco de dados.
* **Falhas de Importação Zeradas:** O ciclo de dupla validação no preenchimento dos 24 campos garante que apenas dados perfeitos cheguem ao HubSpot.

---

## Autor

**Maria Luiza Moraes**
Estagiária • Estratégia, Gestão e M&A @ Sympla

[![LinkedIn](https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/maria-luiza-moraes-98a6b22a8/)
[![GitHub](https://img.shields.io/badge/GitHub-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/marialuizasm21)

---
> **Nota de Confidencialidade:** Este repositório documenta a lógica de negócio, engenharia de dados e arquitetura de automação para fins de portfólio profissional. Códigos-fonte internos, queries originais em SQL, endpoints de API e esquemas privados de bancos de dados foram intencionalmente omitidos.
