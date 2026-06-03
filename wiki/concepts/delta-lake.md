---
title: Delta Lake
page_type: concept
created: 2026-06-02
updated: 2026-06-02
status: active
source_count: 1
tags: [delta-lake, acid, data-lakehouse, storage-framework, tabelas-delta, versionamento]
---

# Delta Lake

## Definição

Delta Lake é um **framework de armazenamento open-source** que permite a criação de Delta Tables sobre object stores na nuvem, proporcionando capacidades transacionais e de qualidade de dados tradicionalmente encontradas apenas em data warehouses. É a tecnologia fundamental para implementar arquiteturas [[data-lakehouse|Data Lakehouse]].

## Características Principais

### 1. Transações ACID
- **Atomicidade**: Operações completas ou totalmente revertidas
- **Consistência**: Dados sempre em estado válido
- **Isolamento**: Transações concorrentes não interferem entre si
- **Durabilidade**: Mudanças confirmadas persistem permanentemente

Assegura operações de leitura e escrita confiáveis e consistentes, mesmo em ambientes de alta concorrência.

### 2. Data History (Time Travel)
- Versionamento automático de dados
- Capacidade de consultar estado histórico
- Auditoria completa de mudanças
- Rollback para versões anteriores

### 3. Change Data Feed
- Rastreamento de mudanças incrementais
- Captura de inserções, atualizações e deleções
- Facilita pipelines de streaming
- Suporta análise de evolução temporal

### 4. Otimização Automática
- Compactação de arquivos pequenos
- Reorganização de dados para melhor performance
- Z-ordering para co-localização de dados relacionados
- Data skipping para acelerar consultas

### 5. Schema Evolution
- Adição de colunas sem reescrever dados
- Modificação de tipos de dados compatíveis
- Schema enforcement para garantir qualidade
- Schema validation na escrita

### 6. Gerenciamento de Dados Não Estruturados
- Suporte a formatos diversos (JSON, Parquet, CSV)
- Armazenamento eficiente de dados semi-estruturados
- Integração com dados estruturados

## Delta Tables

As **Delta Tables** são a unidade fundamental de armazenamento no Delta Lake:

- Armazenadas em formato Parquet otimizado
- Transaction log que registra todas as mudanças
- Metadados para otimização de queries
- APIs para leitura/escrita em Spark, pandas, etc.

## Integração com Arquitetura Medallion

Delta Lake implementa nativamente a [[arquitetura-medallion|Arquitetura Medallion]]:

```
Delta Tables Bronze → Delta Tables Silver → Delta Tables Gold
    (Raw data)         (Curated data)        (Aggregated data)
```

Cada camada é implementada como conjunto de Delta Tables com diferentes níveis de refinamento.

## Vantagens sobre Data Lakes Tradicionais

| Aspecto | Data Lake Tradicional | Delta Lake |
|---------|----------------------|------------|
| Consistência | Sem garantias | ACID completo |
| Versionamento | Manual | Automático |
| Mutabilidade | Append-only | Update/Delete |
| Performance | Degradação com crescimento | Otimização automática |
| Schema | Schema-on-read | Schema enforcement |
| Qualidade | Responsabilidade do usuário | Built-in |

## Caso de Uso: Dataset CNPJ

No [[2026-06-02-construcao-do-dataset-semantico-de-pessoas-juridicas|Dataset Semântico de Pessoas Jurídicas]]:

### Camada Bronze
- Tabelas delta para dados brutos: `empresa`, `estabelecimento`, `socio`, `simples`
- 60M+ registros em múltiplas tabelas
- Preservação da estrutura original CSV

### Camada Silver
- Tabelas normalizadas: `RFB_EMPRESA`, `RFB_ESTABELECIMENTO`, `RFB_ENDERECO`, `RFB_SOCIEDADE`
- Transformações SQL aplicadas
- Identificadores homogêneos criados
- Schema alinhado com ontologia

### Camada Gold
- 4 tabelas analíticas (TG1-TG4)
- Agregações específicas para casos de uso
- Utilizando Change Data Feed para TG3 (evolução temporal)

## Workflow de Processamento

### Ingestão (Bronze)
```python
# Script Python para download e carga
# - Download de .zip
# - Extração para data/<concept>/
# - Renomeação com extensão .csv
# - Criação de Delta Tables mantendo schema original
```

### Transformação (Silver)
```sql
-- Consultas SQL sobre tabelas bronze
-- - Validação de consistência
-- - Normalização de dados
-- - Enriquecimento com joins
-- - Armazenamento em Delta Tables Silver
```

### Agregação (Gold)
```sql
-- Agregações específicas
-- - Group by dimensões de negócio
-- - Cálculos de métricas
-- - Tabelas otimizadas para análise
```

## Integração com Semântica

Delta Lake facilita a geração de datasets semânticos:

1. **Schema Semanticamente Coerente**: Tabelas Silver seguem ontologia
2. **Mapeamentos Diretos**: R2RML mapeia Delta Tables → RDF
3. **Consultas SQL**: Desenvolvedores sem conhecimento de SPARQL podem trabalhar
4. **Dupla Interface**: SQL (tabelas) ou SPARQL (grafo RDF)

## Tecnologias Complementares

- **Apache Spark**: Engine de processamento preferencial
- **Databricks**: Plataforma gerenciada com Delta Lake nativo
- **Python/PySpark**: APIs para programação
- **SQL**: Linguagem de query padrão

## Limitações e Desafios

### Armazenamento
- Dados brutos podem ser volumosos (30GB+ compactados)
- Necessita espaço para múltiplas versões (time travel)
- Requer capacidade para tabelas Bronze + Silver + Gold

### Performance
- Consultas em 60M+ registros demandam otimização
- Necessidade de tuning (Z-order, compaction)

### Complexidade
- Curva de aprendizado para desenvolvedores
- Necessidade de entender conceitos de versionamento
- Gerenciamento de ciclo de vida de versões antigas

## Evidências

> "O uso de Delta Lake apresenta-se como uma solução robusta para muitos dos desafios enfrentados pelos Data Lakes tradicionais. Nesse sentido, Delta Lake é uma framework de armazenamento que permite a criação de Delta Tables, proporcionando Transações ACID, Data History, Change Data Feed, Otimização Automática, Schema Evolution e Gerenciamento de Dados Não Estruturados."
> 
> Fonte: [[2026-06-02-construcao-do-dataset-semantico-de-pessoas-juridicas|Construção do Dataset Semântico de Pessoas Jurídicas]]

## Referências

- Armbrust et al. (2020) - "Delta lake: high-performance acid table storage over cloud object stores"
- Haelen & Davis (2023) - "Delta Lake: Up and Running"

## Links Relacionados

- [[data-lakehouse|Data Lakehouse]]
- [[arquitetura-medallion|Arquitetura Medallion]]
- [[2026-06-02-construcao-do-dataset-semantico-de-pessoas-juridicas|Source - Dataset Semântico PJ]]
