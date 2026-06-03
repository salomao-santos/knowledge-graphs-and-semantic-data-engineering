---
title: Receita Federal do Brasil (RFB)
page_type: entity
created: 2026-06-02
updated: 2026-06-02
status: active
source_count: 1
tags: [entidade, governo, brasil, dados-abertos, cnpj, tributos, fiscalizacao]
---

# Receita Federal do Brasil (RFB)

## Identificação

- **Nome oficial**: Secretaria Especial da Receita Federal do Brasil
- **Tipo**: Órgão governamental federal
- **País**: Brasil
- **Domínio**: Administração tributária e aduaneira

## Descrição

A Receita Federal do Brasil (RFB), ou Secretaria Especial da Receita Federal do Brasil, é um órgão que tem como responsabilidade a administração dos tributos federais e o controle aduaneiro, além de atuar no combate a diversas atividades ilícitas.

## Atribuições

### Principais Responsabilidades

1. **Administração Tributária**
   - Gestão de tributos federais
   - Arrecadação fiscal
   - Fiscalização tributária

2. **Controle Aduaneiro**
   - Fiscalização de importações e exportações
   - Controle de fronteiras

3. **Combate a Ilícitos**
   - Evasão fiscal (sonegação)
   - Contrabando
   - Descaminho
   - Contrafação (pirataria)
   - Tráfico de drogas, armas e animais

## Dados Abertos Disponibilizados

### Cadastro Nacional de Pessoas Jurídicas (CNPJ)

A RFB é a **fonte de dados primária** responsável por fornecer informação fidedigna de CPFs e CNPJs no Brasil.

**Importância Legal:**
- Uma empresa que não tem CNPJ cadastrado na RFB é uma empresa de fato, mas não de direito
- Exercício sem CNPJ constitui atividade ilegal

#### Dados Disponibilizados

| Conjunto de Dados | Descrição | Formato | Acesso |
|-------------------|-----------|---------|--------|
| **Empresas** | Dados cadastrais de pessoas jurídicas | 10 arquivos .zip | Público |
| **Estabelecimentos** | Informações de estabelecimentos comerciais | 10 arquivos .zip | Público |
| **Sócios** | Quadro societário das empresas | 10 arquivos .zip | Público |
| **Simples/MEI** | Cadastro do Simples Nacional e MEI | 1 arquivo .zip | Público |
| **CNAEs** | Classificação de Atividades Econômicas | 1 arquivo .zip | Público |
| **Naturezas Legais** | Naturezas jurídicas das empresas | 1 arquivo .zip | Público |
| **Países** | Tabela de países | 1 arquivo .zip | Público |
| **Municípios** | Tabela de municípios brasileiros | 1 arquivo .zip | Público |
| **Razões de Situação Cadastral** | Motivos de situação cadastral | 1 arquivo .zip | Público |
| **Qualificações** | Qualificações de sócios | 1 arquivo .zip | Público |

#### Características dos Dados

- **Volume**: Mais de 30GB compactados
- **Formato**: CSV dentro de arquivos .zip
- **Registros**: 60+ milhões (empresas e estabelecimentos)
- **Atualização**: Periódica (aproximadamente mensal)
- **Nomenclatura**: Arquivos sem extensão adequada originalmente (ex: `F.K03200$Z.D40608.MOTICSV`)

#### Links Oficiais

- **Dados CNPJ**: https://tinyurl.com/44z6xkk9
- **Layout/Metadados**: https://www.gov.br/receitafederal/dados/cnpj-metadados.pdf
- **Simples Nacional**: http://200.152.38.155/CNPJ/Simples.zip
- **Motivos**: http://200.152.38.155/CNPJ/Motivos.zip

## Desafios dos Dados

### 1. Volume e Armazenamento
- Mais de 30GB compactados, expandindo significativamente após extração
- Mais de 60 milhões de registros apenas em empresas e estabelecimentos

### 2. Estrutura Complexa
- Alguns arquivos contêm mais de 20 atributos
- Alto acoplamento entre diferentes conjuntos de dados
- Necessidade de múltiplas junções para consultas completas

### 3. Identidade Fraca
- CNPJ de estabelecimento composto por 3 campos: `CNPJ_BASICO` + `CNPJ_ORDEM` + `CNPJ_DIV`
- Necessidade de concatenação constante
- CPF de sócios anonimizado (apenas 6 dígitos centrais)

### 4. Qualidade dos Dados
- Nomenclatura original sem extensões adequadas
- Necessidade de limpeza e normalização extensiva
- Alguns conceitos não explícitos no layout

## Uso em Pesquisas

A RFB e seus dados são utilizados em diversos trabalhos acadêmicos e práticos:

### Dataset Semântico CNPJ
Descrito em [[2026-06-02-construcao-do-dataset-semantico-de-pessoas-juridicas|Construção do Dataset Semântico de Pessoas Jurídicas]]:
- Primeira iniciativa de dataset semântico baseado em CNPJ
- Arquitetura [[data-lakehouse|Data Lakehouse]] com [[delta-lake|Delta Lake]]
- Ontologia modelada a partir do layout oficial
- Mais de 177M+ de triplas RDF geradas

### Casos de Uso Identificados

1. **Monitoramento de Conformidade Fiscal**
   - Verificação de empresas no Simples Nacional/MEI
   - Validação de atividades econômicas (CNAE)

2. **Detecção de Inconsistências**
   - Empresas com informações de contato duplicadas
   - Empresas sem sócios ativos
   - Sócios falecidos

3. **Monitoramento de Atividades**
   - Empresas com atividades econômicas incompatíveis
   - Riscos à segurança pública

4. **Validação Cadastral**
   - Estabelecimentos sem endereços válidos
   - Verificação de localização física

5. **Análise de Capital Social**
   - Capital declarado vs porte/atividade
   - Detecção de fraudes financeiras

## Integração com Outros Sistemas

### Potenciais Integrações Futuras
Mencionadas como trabalhos futuros:
- CNAE do IBGE (mais detalhado)
- Cadastro de Inidôneos e Suspensos (CEIS)
- Tribunal de Contas da União (TCU)
- Portal de Compras Governamentais

## Evidências

> "A RFB é fonte de dados primária responsável por fornecer a informação fidedigna de CPFs e CNPJs. Logo, uma empresa que não tem CNPJ cadastrado na RFB é, então, uma empresa de fato, mas não de direito, já que estará fazendo exercício ilegal das suas atividades."
> 
> Fonte: [[2026-06-02-construcao-do-dataset-semantico-de-pessoas-juridicas|Construção do Dataset Semântico de Pessoas Jurídicas]]

## Relevância para Dados Abertos

A RFB representa um caso exemplar de:
- **Transparência governamental**: Dados públicos acessíveis
- **Volume significativo**: Datasets de grande escala
- **Valor estratégico**: Informações essenciais para fiscalização
- **Desafio técnico**: Complexidade que motiva pesquisa em processamento de dados

## Links Relacionados

- [[2026-06-02-construcao-do-dataset-semantico-de-pessoas-juridicas|Source - Dataset Semântico PJ]]
- [[data-lakehouse|Data Lakehouse]]
- [[delta-lake|Delta Lake]]
- [[arquitetura-medallion|Arquitetura Medallion]]
