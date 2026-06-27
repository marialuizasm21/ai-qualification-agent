# Agente de Inteligência de Mercado (Integração LLM & Banco de Dados)

Sistema avançado de inteligência artificial desenvolvido via **Prompt Engineering de alta complexidade** e integrado ao banco de dados via **MCP Server**. O agente atua como um Especialista de Inteligência de Mercado (LDR), transformando dados brutos e caóticos em dossiês comerciais estruturados e validados.

[![LinkedIn](https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/maria-luiza-moraes-98a6b22a8/)
[![GitHub](https://img.shields.io/badge/GitHub-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/marialuizasm21)

---

## Skills Técnicas Aplicadas

<div align="center">

![Prompt Engineering](https://img.shields.io/badge/Prompt_Engineering-FF69B4?style=for-the-badge&logo=openai&logoColor=white)
![SQL](https://img.shields.io/badge/SQL-4479A1?style=for-the-badge&logo=mysql&logoColor=white)
![Metabase](https://img.shields.io/badge/Metabase-509EE3?style=for-the-badge&logo=metabase&logoColor=white)
![Integração API/MCP](https://img.shields.io/badge/API_/_MCP_Server-000000?style=for-the-badge)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black)
![Regex](https://img.shields.io/badge/Regex-000000?style=for-the-badge)

</div>

---

## O Desafio vs. A Solução

**O Problema:** O processo de qualificação de leads era 100% manual e fragmentado. O time de vendas precisava cruzar dados de CRMs (HubSpot), redes sociais e consultas complexas no Metabase (SQL) — ID por ID —, o que consumia de 25 a 40 minutos por lead. Além disso, a digitação manual em planilhas gerava erros de formatação e quebrava a integração com o CRM.

**A Solução:** Desenvolvimento de um **Agente Conversacional Integrado**. O usuário envia um "dump" de texto bruto (logs, links de Instagram, notas do CRM) para o chat. A IA processa o texto, conecta-se ao Metabase via API (MCP Server) para puxar o histórico transacional em tempo real, estrutura a narrativa estratégica e exporta 24 campos de dados estritamente validados direto para o banco.

---

## 🛠️ Arquitetura e Inteligência do Agente

O "cérebro" do agente foi construído com diretrizes rigorosas de Prompt Engineering para garantir comportamento determinístico, foco comercial e zero alucinação.

### 1. Ingestão e Processamento Anti-Ruído
* **Parsing de Texto Bruto:** A IA é programada para limpar lixo de sistema (ex: "Adicionar arquivo", "Nenhum proprietário") copiado de CRMs.
* **Proteção de Stakeholders:** Lógica condicional que preserva o contato original do lead mapeado, movendo decisores secundários encontrados em logs para a seção de contexto.

### 2. Integração de Dados Avançada (MCP Server + SQL)
A IA não apenas gera texto, ela atua como analista de dados autônoma:
* **Consultas em Tempo Real:** Conecta-se ao banco de dados via API para extrair GMV histórico, ticket médio, volume de eventos e status de *churn*.
* **Agrupamento de Múltiplos IDs:** A IA foi instruída a consolidar múltiplos User IDs de um mesmo cliente, somando o GMV acumulado e calculando médias ponderadas de público, gerando um raio-X consolidado ao invés de análises fragmentadas.

### 3. Matriz de Inteligência de Produto (Classificação Automática)
Ao identificar a dor do lead no texto bruto, o agente classifica a demanda ferramental internamente:
* 🟢 **Atendida Nativamente:** Recursos de prateleira (ex: *Afiliados, Cortesia*).
* 🟡 **Condicional:** Funcionalidades que exigem setup ou contratos específicos (*Smart POS*).
* 🔴 **Não Atendida:** Limitações sistêmicas (*White Label total*), mapeadas de forma transparente para evitar falsas promessas comerciais.

---

## 🔒 Pipeline de Exportação e Validação ("Gatekeeper")

Para erradicar falhas de importação no HubSpot, o agente atua como um validador estrito antes de qualquer escrita no banco de dados. 

**O Fluxo de Execução:**
1. O agente localiza a linha exata cruzando `Nome da Empresa` + `Data de Nutrição`.
2. Exibe o resultado e exige confirmação humana (`"Aprovar"`).
3. Roda um **Painel de Validação Interno**. Se houver um único erro (❌), a exportação é bloqueada e a IA devolve o log de erros.

**Critérios de Sanitização (24 Campos):**

| Tipo de Dado | Regra de Validação Aplicada (Regex/Lógica) |
| :--- | :--- |
| **CNPJ** | Extração de número puro (remoção de pontos e traços). |
| **Telefone** | Máscara obrigatória de DDD e dígitos: `(XX) XXXXX-XXXX`. |
| **Estado (UF)** | Formatação exata: `Nome do Estado (UF)`. |
| **Métricas** | Ticket, Taxas e Público extraídos como *Integer/Float* puro (sem `R$` ou `%`). |
| **Menus Fechados** | Categorias (Segmento, Frequência, Plataforma Concorrente) restritas a um dicionário de dados pré-definido. |
| **Zero Alucinação** | Se não há dado no texto de origem = Campo vazio. Proibido inventar dados. |

---

## 📖 Estrutura do Dossiê Estratégico

O output final do agente não é um resumo genérico, mas um documento auditável estruturado em blocos de exclusividade (Anti-Repetição):

1. **W — Histórico Técnico:** Síntese do banco de dados (IDs, GMV, status de churn).
2. **AA — Histórico Comercial:** Cronologia das 2 negociações principais (marcos antigos e recentes).
3. **AY — Plataforma Concorrente:** Mapeamento de lotes, taxas e dores com a ferramenta atual.
4. **BJ — Contexto Adicional:** 3 subseções engessadas: Contexto Estratégico, Demanda Ferramental classificada e Links/Contatos auditados.
5. **Rastreabilidade (Regra Crítica):** Todo insight gerado exige carimbo de origem (ex: *"Segundo observação registrada por [Nome] no HubSpot em [Data]..."*).

---

## 🚀 Resultados e Impacto do Projeto

* **Fim do Trabalho Manual:** Substituição de dezenas de cliques, abas abertas e digitação célula a célula por uma única interação via chat.
* **Redução de 50% no SLA de Qualificação:** O tempo de pesquisa e preenchimento caiu de **40 para 20 minutos** por lead.
* **Democratização de Dados:** Vendedores acessam consultas complexas de banco de dados (SQL/Metabase) em linguagem natural, sem precisar dominar ferramentas de BI.
* **Dados 100% Sanitizados:** A barreira de dupla validação do agente reduziu a zero os erros de formatação na importação para o CRM (HubSpot).

---

## Autor

**Maria Luiza Moraes**
Estagiária • Estratégia, Gestão e M&A @ Sympla

[![LinkedIn](https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/maria-luiza-moraes-98a6b22a8/)
[![GitHub](https://img.shields.io/badge/GitHub-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/marialuizasm21)

---
> **Nota de Confidencialidade:** Este repositório documenta a lógica de negócio, engenharia de prompt e arquitetura de integração de dados para fins de portfólio profissional. Dados confidenciais, queries de banco de dados e chaves de API foram intencionalmente omitidos ou generalizados.
