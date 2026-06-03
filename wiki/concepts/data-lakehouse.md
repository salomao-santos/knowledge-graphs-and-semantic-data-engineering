---
title: Data Lakehouse
page_type: concept
created: 2026-06-02
updated: 2026-06-02
status: active
source_count: 1
tags: [arquitetura-de-dados, data-lakehouse, data-lake, data-warehouse, acid, delta-lake]
---

# Data Lakehouse

## Definição

Data Lakehouse é uma arquitetura de dados inovadora que combina as vantagens dos **data lakes** e **data warehouses** para fornecer uma camada de armazenamento unificada, eficiente e gerenciável. Esta abordagem híbrida busca resolver as limitações de ambas as arquiteturas tradicionais.

## Motivação

O conceito de Data Lakehouse foi introduzido para abordar limitações específicas:

### Limitações dos Data Lakes
- Altamente escaláveis e capazes de armazenar dados em qualquer formato
- Sofrem com falta de governança e qualidade de dados
- Ausência de garantias transacionais

### Limitações dos Data Warehouses
- Fornecem estrutura rígida e eficiente para consultas
- Não conseguem lidar com a variedade e volume de dados modernos
- Custos elevados de armazenamento

## Características Principais

### 1. Transações ACID
Um dos principais benefícios do Data Lakehouse é o suporte a transações ACID (Atomicidade, Consistência, Isolamento e Durabilidade), que assegura operações de leitura e escrita confiáveis e consistentes, mesmo em ambientes de alta concorrência.

### 2. Camada Unificada
Permite que desenvolvedores realizem consultas em SQL ou desenvolvam aplicações diretamente através das tabelas, mesmo sem familiaridade com tecnologias semânticas.

### 3. Governança e Qualidade
Combina a escalabilidade dos data lakes com a governança e qualidade dos data warehouses.

## Integração com Tecnologias Semânticas

Utilizar dados do Data Lakehouse em conjunto com tecnologias semânticas e grafos de conhecimento:
- Facilita o tratamento de grandes conjuntos de dados
- Proporciona uma visão unificada
- Permite integrações com outras fontes e datasets
- Possibilita a criação de conhecimento explícito a partir de dados implícitos
- Habilita o uso de reasoners para inferir novos fatos

## Implementações

A principal implementação mencionada é através do [[delta-lake|Delta Lake]], que fornece a infraestrutura necessária para criar um Data Lakehouse funcional com suporte à [[arquitetura-medallion|Arquitetura Medallion]].

## Casos de Uso

Aplicado com sucesso na construção de:
- [[2026-06-02-construcao-do-dataset-semantico-de-pessoas-juridicas|Dataset Semântico de Pessoas Jurídicas]] baseado no CNPJ da RFB

## Comparação com Arquiteturas Tradicionais

| Característica | Data Lake | Data Warehouse | Data Lakehouse |
|---------------|-----------|----------------|----------------|
| Escalabilidade | Alta | Média | Alta |
| Governança | Baixa | Alta | Alta |
| Suporte ACID | Não | Sim | Sim |
| Variedade de Dados | Alta | Baixa | Alta |
| Custo | Baixo | Alto | Médio |

## Evidências

> "O Data Lakehouse emerge como uma arquitetura de dados inovadora, combinando as vantagens dos data lakes e data warehouses para fornecer uma camada de armazenamento unificada, eficiente e gerenciável."
> 
> Fonte: [[2026-06-02-construcao-do-dataset-semantico-de-pessoas-juridicas|Construção do Dataset Semântico de Pessoas Jurídicas]]

## Referências

- Armbrust et al. (2021) - "Lakehouse: a new generation of open platforms that unify data warehousing and advanced analytics"
- Cherradi (2024) - "Data lakehouse: Next generation information system"

## Links Relacionados

- [[delta-lake|Delta Lake]]
- [[arquitetura-medallion|Arquitetura Medallion]]
- [[2026-06-02-construcao-do-dataset-semantico-de-pessoas-juridicas|Source - Dataset Semântico PJ]]
