# Consolidação e Padronização de Base de Dados Histórica

## 🎯 Problema
Gerenciar 3 lojas de lavanderia self-service significa coletar dados diários de faturamento, mas ao longo de 7 anos (jul/2019 a jun/2026), os registros foram acumulados em **150+ arquivos Excel com estruturas inconsistentes**:
- Nomes de colunas diferentes
- Formatos variáveis
- Códigos de cliente duplicados ou em branco
- Dados espalhados, impossíveis de analisar em conjunto

## 💡 Solução
Consolidação e padronização completa em uma única base de dados estruturada:
- **86.134 linhas** de dados históricos
- **10 colunas** padronizadas: Loja, IdCliente, Cliente, Data/Hora, FormaDePagamento, Valor, ArquivoOrigem, PeriodoArquivo, NSU, Origem
- Preenchimento seguro de 8.400+ códigos de cliente em branco com auditoria completa (evitando mistura de histórico entre clientes homônimos)
- Estruturada em lote único (`.zip`) para uso com IA generativa sem perda de contexto

## 📊 Resultado

**Dados consolidados:** 86.134 linhas de transações (jan/2020 a jun/2026)
- 3 lojas (CE01, CE05, CE17)
- 10 colunas padronizadas: Loja, IdCliente, Cliente, Data/Hora, FormaDePagamento, Valor, ArquivoOrigem, PeriodoArquivo, NSU, Origem
- Rastreabilidade completa de origem (colunas ArquivoOrigem, PeriodoArquivo)
- Algumas colunas (NSU, Origem) contêm valores em branco para registros históricos que não tinham essa informação

**Sample dos dados:**

Veja o arquivo [`sample_dados_consolidados.csv`](sample_dados_consolidados.csv) para a estrutura completa com 30 linhas de exemplo cobrindo o período inteiro (2020-2026).

## 🛠️ Tecnologias
- Python (Pandas, data cleaning)
- Excel
- Data Auditing & Validation

## ⚙️ Como funciona
1. **Leitura**: Lê todos os 150+ arquivos Excel das 3 lojas
2. **Limpeza**: Padroniza nomes de colunas, tipos de dados e formatos
3. **Preenchimento**: Auditado de códigos de cliente em branco (mantendo rastreabilidade)
4. **Consolidação**: Merge em uma única tabela de 86.134 linhas
5. **Validação**: Verificação de integridade e consistência

## 📈 Impacto
- Base histórica consolidada pronta para análise
- Fundação sólida para um dashboard contínuo em Power BI
- Estrutura preparada para automação recorrente

## 📌 Próximos passos
- Automação da consolidação recorrente (atualizar mensalmente)
- Integração com Power BI para análise contínua
- Alertas de anomalias nos dados

---
⚠️ Este repositório contém apenas o código e scripts de consolidação. Nenhum arquivo de dados real (.xlsx, .csv) é versionado — dados são carregados e salvos localmente via scripts.
