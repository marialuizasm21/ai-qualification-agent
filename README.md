# Agente de IA para Qualificação de Leads com Integração Metabase

Agente de inteligência artificial que automatiza a qualificação de leads com conexão direta ao banco de dados, validação multicamadas e exportação automática de 24 campos validados para a planilha de nutrição.

---

## O Problema

O processo de qualificação de leads era 100% manual e extremamente trabalhoso:

### Coleta de Dados Fragmentada
- Qualificadores precisavam abrir **múltiplas ferramentas**: Metabase, Google, HubSpot, redes sociais
- Busca manual de informações demorava entre 25 a 40 minutos por lead
- Dados históricos do Metabase exigiam conhecimento técnico para consultar
- Estimativas de GMV substituíam dados reais do banco por falta de acesso fácil

### Digitação Manual e Erros
- **24 campos diferentes** preenchidos manualmente, um por um
- Erros de digitação frequentes (CNPJ, telefone, email)
- Campos obrigatórios deixados vazios geravam falhas na importação
- Inconsistências de formatação quebravam integração com HubSpot

### Falta de Padronização
- Cada qualificador escrevia dossiês de forma diferente
- Nomes em MAIÚSCULAS, estados sem padrão "Nome (UF)"
- Uso incorreto de menus fechados (plataforma concorrente, segmento)
- Sem rastreabilidade das fontes de informação

### Sem Validação Prévia
- Leads eram enviados para importação sem verificação
- Erros só descobertos depois no HubSpot
- Retrabalho constante de correção pós-importação
- Qualidade da base de dados comprometida

**Impacto:** 40 minutos por lead, alto índice de erros, retrabalho constante, dados estimados ao invés de reais, falta de padronização.

---

## A Solução

Desenvolvi um **agente de IA completo** baseado em **Claude (Anthropic)** com arquitetura de prompt estruturado de alta complexidade.

### Integração Direta com Banco de Dados

**Conexão via API Metabase:**
- Sistema se conecta diretamente ao banco de dados através da API do Metabase
- Executa queries SQL em tempo real durante a qualificação
- Extrai automaticamente dados históricos reais do produtor

**Dados Extraídos Automaticamente:**
- GMV histórico total e por período
- User IDs ativos na plataforma
- Quantidade de eventos publicados
- Último mês com GMV registrado
- Ticket médio e público médio
- Segmento dominante
- Status comercial provável (Cliente ativo, Churn, Inativo)

**Benefício:** Substituição de estimativas por **dados reais do banco**, eliminando necessidade de abrir Metabase manualmente.

### Pesquisa Ativa na Web

Além do Metabase, o agente executa:
- Pesquisa em Google sobre empresa e decisores
- Consulta em redes sociais (LinkedIn, Instagram)
- Identificação de plataformas concorrentes
- Mapeamento de eventos e histórico comercial

**Política de Zero Alucinação:**
- Se não há dado confiável, campo fica vazio
- Toda informação deve ser verificável
- Nunca inventa dados ou estimativas

### Estrutura Hierárquica de Informações

O agente organiza dados em camadas com funções específicas:

**1. Resumo Metabase (Informativo - não exportado)**
- Campo exclusivo para leitura rápida
- 4-5 linhas com dados do banco
- Aceita "não identificado" quando faltar dado
- Serve para contexto, não vai para planilha

**2. Histórico Sympla (Exportável - Coluna W)**
- Síntese objetiva de 2-4 linhas
- User IDs, status atual, negociações principais
- Modelo padronizado obrigatório
- Só preenche se tiver dado real, senão fica vazio

**3. Histórico Comercial (Exportável - Coluna AA)**
- Cronologia completa de negociações
- Formato: Data | Negociação | Responsável | Resultado | Registro | Próximo passo
- Uma linha por negociação
- Rastreabilidade total

**4. Contexto Adicional (Exportável - Coluna BJ)**
- Inteligência estratégica para abordagem comercial
- 3-4 linhas máximo
- Posicionamento, público-alvo, timing ideal
- Gatilhos para retomada de contato

### Sistema de Validação Dupla

**Primeiro Checkpoint - Pré-exportação:**
- Verifica formatação de CNPJ (só números)
- Valida telefone no padrão (XX) XXXXX-XXXX
- Confirma estado no formato "Nome (UF)"
- Checa menus fechados obrigatórios
- Valida campos críticos preenchidos

**Segundo Checkout - Confirmação:**
- Busca automática da empresa na planilha (Nome + Data de hoje)
- Mostra resultado da busca para confirmação
- Aguarda comando explícito "Aprovar" ou "Ajustar"
- Só exporta após aprovação do usuário

**Se validação falhar:**
- Lista TODOS os problemas encontrados
- NÃO exporta
- Explica o que precisa ser corrigido

### Rastreabilidade Obrigatória

Toda observação comercial deve responder:
- **Quem** trouxe a informação (nome completo do responsável)
- **Onde** estava registrada (negociação, tarefa, Slack, HubSpot)
- **Quando** foi registrada (data quando disponível)
- **Qual ID** relacionado (Deal ID, Task ID, User ID)
- **Qual interpretação** comercial objetiva

**Padrão:**
"Segundo observação registrada por [Nome Completo] em [local/fonte/data]..."

### Exportação Automática

Após validação e aprovação:
- Exporta **24 campos** diretamente para planilha
- Mapeamento preciso (coluna W, AA, AB, AC... até BJ)
- Campos não preenchidos: GMV (AQ), Status Sympla (V), Identificação HubSpot (X)
- Execução em uma única operação
- Zero digitação manual

### Dossiês Profissionais Estruturados

Gera relatórios investigativos seguindo estrutura narrativa padronizada:
- Resumo Metabase (contexto)
- Identificação completa do lead
- Histórico e relacionamento Sympla
- Histórico de negociações comerciais
- Perfil do produtor e operação
- Detalhes de concorrência
- Contexto adicional estratégico
- Demandas ferramentais identificadas

---

## Tecnologias

**Inteligência Artificial:**
- Claude AI (Anthropic)
- Prompt engineering avançado (arquitetura multicamadas)
- Zero-hallucination policy

**Integração de Dados:**
- Metabase API (conexão direta com banco)
- Queries SQL em tempo real
- Google Sheets API (exportação automática)

**Validação e Automação:**
- Sistema de validação dupla (2 checkouts)
- Normalização de dados (CNPJ, telefone, estado)
- Mapeamento de 50 campos entre sistemas

**Pesquisa e Coleta:**
- Web search integration
- Scraping estruturado de informações públicas
- Cross-reference de múltiplas fontes

---

## Resultados

### Quantitativos
- **50% de redução** no tempo de qualificação (40min → 20min)
- **24 campos** exportados automaticamente
- **Zero erros** de importação após validação dupla
- **100% precisão** nos dados do Metabase (dados reais vs estimativas)
- **Múltiplos leads** qualificados com sucesso em produção

### Qualitativos
- Qualificadores não precisam mais abrir Metabase manualmente
- Substituição total de estimativas por dados reais do banco
- Eliminação de digitação manual dos 24 campos
- Padronização completa de dossiês com estrutura consistente
- Rastreabilidade total de todas as informações comerciais
- Democratização do acesso à inteligência de banco de dados
- Liberação de tempo para análise estratégica ao invés de trabalho operacional

### Em Produção
Sistema entregue para toda a equipe de qualificação, democratizando acesso a dados do banco sem necessidade de conhecimento técnico do Metabase.

---

## Fluxo de Trabalho

### 1. Início da Qualificação
Qualificador fornece ao agente:
- Nome da empresa
- Data de nutrição (hoje)

### 2. Coleta Automática de Dados

**Metabase (via API):**
- Consulta banco de dados em tempo real
- Extrai GMV histórico, User IDs, eventos, segmentos
- Compila status comercial atual

**Web Search:**
- Pesquisa empresa, decisores, eventos
- Identifica plataforma concorrente
- Mapeia histórico comercial e contexto

### 3. Geração do Dossiê
- Organiza informações na estrutura hierárquica
- Aplica rastreabilidade a todas as observações
- Segue modelo narrativo padronizado
- Preenche apenas campos com dados verificáveis

### 4. Primeira Validação
Verifica:
- Formatação (CNPJ, telefone, estado)
- Menus fechados
- Campos obrigatórios
- Dados críticos

### 5. Busca na Planilha
- Procura empresa por Nome (col. T) + Data (col. R)
- Exibe resultado encontrado
- Aguarda confirmação

### 6. Segunda Validação
Usuário revisa e:
- Aprova → exportação automática
- Ajusta → corrige e valida novamente

### 7. Exportação
- 24 campos preenchidos automaticamente
- Linha correta identificada
- Execução em uma única operação
- Confirmação de sucesso

---

## Arquitetura do Prompt

O prompt foi estruturado em camadas funcionais:

### Identidade e Regras
- Definição clara do papel (Especialista de Inteligência LDR)
- Regras críticas (zero alucinação, campos vazios, rastreabilidade)
- Output obrigatório (lista formatada)

### Validação e Exportação
- Painel de validação completo
- Fluxo de busca e confirmação
- Mapeamento dos 24 campos
- Campos que nunca devem ser preenchidos

### Menus Fechados
- Plataforma Concorrente (200+ opções mapeadas)
- Frequência, Segmento, Tema, Subtema, Sazonalidade, Formatos
- Demandas Ferramentais
- Status e Identificação (informativos)

### Hierarquia de Campos
- Diferenciação clara entre informativo e exportável
- Resumo Metabase vs Histórico Sympla
- Histórico Comercial vs Contexto Adicional
- Regras específicas de preenchimento para cada campo

### Rastreabilidade
- Padrões de citação obrigatórios
- Nomes completos de responsáveis
- IDs e datas quando disponíveis
- Fonte e interpretação comercial

---

## Diferenciais

### 1. Integração Real com Banco de Dados
Não é só pesquisa na web - o agente **consulta dados operacionais reais** via API Metabase, algo raro em agentes de qualificação.

### 2. Validação Multicamadas
Sistema de duplo checkpoint garante qualidade antes da exportação, eliminando erros de importação no HubSpot.

### 3. Estrutura Hierárquica Inteligente
Separação clara entre dados informativos e exportáveis evita poluição da base e mantém informações úteis e padronizadas.

### 4. Rastreabilidade Total
Toda informação tem fonte identificável, permitindo auditorias e validação de contexto comercial.

### 5. Zero Alucinação
Política rigorosa de apenas dados verificáveis - se não tem fonte confiável, campo fica vazio.

### 6. Democratização de Dados
Qualquer membro da equipe acessa inteligência do banco de dados sem precisar conhecer SQL ou Metabase.

---

## Aprendizados

### Prompt Engineering
- Arquitetura em camadas facilita manutenção e evolução
- Regras explícitas e exemplos concretos reduzem ambiguidade
- Validação programática complementa capacidade da IA

### Integração de Sistemas
- API Metabase permite acesso estruturado ao banco
- Queries SQL em tempo real viabilizam dados sempre atualizados
- Normalização é crítica para exportação sem erros

### Gestão de Qualidade
- Validação dupla elimina praticamente todos os erros
- Rastreabilidade cria confiança nos dados
- Padronização facilita treinamento e escalabilidade

### Adoção
- Democratização de dados complexos aumenta uso
- Eliminação de trabalho manual aumenta engajamento
- Feedback rápido (20min vs 40min) melhora experiência

---

## Limitações & Próximos Passos

### Limitações Atuais
- Dependente de qualidade dos dados no Metabase
- Requer aprovação manual antes de exportar (segurança vs velocidade)
- Plataformas concorrentes não mapeadas caem em "Outra não mapeada"

### Melhorias Futuras
- Integração direta com HubSpot para puxar histórico de deals automaticamente
- Machine learning para sugerir melhores abordagens baseado em leads similares
- Expansão do mapeamento de plataformas concorrentes
- Trigger automático para atualizar dossiês quando novos dados aparecem no Metabase

---

## Autor

**Maria Luiza Moraes**  
Estagiária • Estratégia, Gestão e M&A @ Sympla

[LinkedIn](https://www.linkedin.com/in/maria-luiza-moraes-98a6b22a8/) • [GitHub](https://github.com/marialuizasm21)

---

**Nota:** O prompt completo e lógica de negócio não estão disponíveis publicamente por conterem informações proprietárias. Este repositório serve como documentação do projeto para fins de portfólio.
