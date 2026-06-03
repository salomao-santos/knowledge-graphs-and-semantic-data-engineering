---
title: Arquitetura Medallion
page_type: concept
created: 2026-06-02
updated: 2026-06-02
status: active
source_count: 1
tags: [arquitetura, medallion, bronze-silver-gold, data-lakehouse, delta-lake, processamento-de-dados]
---

# Arquitetura Medallion

## Definição

Arquitetura Medallion, também conhecida como **arquitetura de camadas**, é um design pattern adotado pelo [[delta-lake|Delta Lake]] para organizar dados de forma hierárquica e incremental, visando melhorar a qualidade dos dados e a eficiência das consultas. É uma abordagem amplamente utilizada em arquiteturas de [[data-lakehouse|Data Lakehouse]].

## Estrutura em Três Camadas

A arquitetura organiza os dados em três camadas progressivas, cada uma com um nível crescente de refinamento e qualidade:

### 1. Camada Bronze (Raw/Bruta)

**Características:**
- Dados brutos ingeridos diretamente das fontes
- Mínimo ou nenhum processamento
- Preservação da estrutura original dos dados
- Foco em ingestão rápida e confiável

**Processo:**
- Download e extração de arquivos (.zip, .csv)
- Renomeação e organização por conceito
- Classificação inicial por categorias (Empresas, Estabelecimentos, Sócios)
- Conformidade com esquema original da fonte

**Exemplo (Dataset CNPJ):**
- Arquivos CSV extraídos diretamente da RFB
- Mais de 60 milhões de registros
- Estrutura: EMPRE.CSV, SOCIO.CSV, ESTABELE.CSV, etc.

### 2. Camada Silver (Refinada/Curada)

**Características:**
- Dados limpos e normalizados
- Transformações aplicadas para facilitar uso
- Integração entre diferentes tabelas
- Esquema semanticamente coerente

**Transformações Aplicadas:**
1. **Criação de identificadores homogêneos**
   - Exemplo: concatenação de CNPJ_BASICO + CNPJ_ORDEM + CNPJ_DIV → CNPJ único

2. **Padronização de formatos**
   - Datas e números uniformizados
   - Valores textuais para campos flag (ex: 02 → 'ATIVA')

3. **Integração de dados**
   - Junção de empresa com estabelecimento, sócio, qualificação
   - Criação de visão completa da estrutura empresarial

4. **Inclusão de conceitos derivados**
   - Novas tabelas: RFB_SOCIEDADE_COM_PESSOA_FISICA
   - Simplificação de relações complexas

5. **Normalização guiada por ontologia**
   - Matching entre esquema das tabelas e classes/propriedades da ontologia
   - Redução do gap semântico

### 3. Camada Gold (Agregada/Analítica)

**Características:**
- Dados agregados para casos de uso específicos
- Insights prontos para stakeholders
- Otimizados para análise e reporting
- Alto valor de negócio

**Exemplos de Tabelas Gold (Dataset CNPJ):**

| Tabela                        | Descrição                        | Conteúdo                                        |
| ----------------------------- | -------------------------------- | ----------------------------------------------- |
| TG1 - Empresas e Atividades   | Consolidação por setor econômico | Número de empresas, receitas, funcionários      |
| TG2 - Distribuição Geográfica | Agregação por estado             | Densidade empresarial, atividades predominantes |
| TG3 - Evolução Temporal       | Histórico de mudanças            | Novos registros, encerramentos, mudanças        |
| TG4 - Quadro Societário       | Categorização de sócios          | Qualificações, participações, relações          |

## Fluxo de Dados

```
Fonte de Dados → Bronze → Silver → Gold → Consumo
     ↓              ↓         ↓        ↓         ↓
  Bruto       Ingestão  Limpeza  Agregação  Análise
                        Transform  Insights  Decisão
```

## Benefícios

1. **Rastreabilidade**: Dados brutos sempre preservados na camada Bronze
2. **Qualidade Progressiva**: Cada camada adiciona refinamento
3. **Flexibilidade**: Diferentes níveis para diferentes necessidades
4. **Reprocessamento**: Possibilidade de reconstruir Silver/Gold a partir de Bronze
5. **Governança**: Clara separação de responsabilidades

## Integração com Ontologias

Na camada Silver, a arquitetura Medallion pode ser enriquecida com semântica através de:

- **Matching ontológico**: Classes → Tabelas, Properties → Atributos
- **Mapeamentos diretos**: Redução de complexidade
- **URIs como identificadores**: Recursos identificáveis semanticamente

## Heurísticas de Mapeamento (Bronze → Silver)

1. **Classe**: Mapeada como uma tabela
2. **Data Type Property**: Atributo da tabela pivot
3. **Object Type Property**: Chave estrangeira na tabela pivot
4. **URIs**: Identificadores dos recursos

## Ferramentas Comuns

- [[delta-lake|Delta Lake]]: Framework que implementa nativamente Medallion
- Apache Spark: Processamento e transformações
- Databricks: Plataforma com suporte nativo

## Caso de Uso Real

No [[2026-06-02-construcao-do-dataset-semantico-de-pessoas-juridicas|Dataset Semântico CNPJ]]:
- **Bronze**: 30GB+ de dados brutos CSV da RFB
- **Silver**: 60M+ registros normalizados em tabelas relacionais
- **Gold**: 4 tabelas analíticas para casos específicos
- **Semântico**: Dataset RDF gerado a partir de Silver com R2RML

## Evidências

> "O uso de Delta Lake apresenta-se como uma solução robusta para muitos dos desafios enfrentados pelos Data Lakes tradicionais. [...] Essa solução trata o fluxo dos dados e organiza-o na arquitetura Medallion, também conhecida como arquitetura de camadas, um design adotado pelo Delta Lake para organizar dados de forma hierárquica e incremental."
> 
> Fonte: [[2026-06-02-construcao-do-dataset-semantico-de-pessoas-juridicas|Construção do Dataset Semântico de Pessoas Jurídicas]]

## Referências

- Databricks (2021) - "What is a medallion architecture"
- Haelen & Davis (2023) - "Delta Lake: Up and Running"

## Links Relacionados

- [[data-lakehouse|Data Lakehouse]]
- [[delta-lake|Delta Lake]]
- [[2026-06-02-construcao-do-dataset-semantico-de-pessoas-juridicas|Source - Dataset Semântico PJ]]
