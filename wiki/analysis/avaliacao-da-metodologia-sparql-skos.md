---
title: Analysis - Avaliacao da Metodologia SPARQL + SKOS
page_type: analysis
created: 2026-06-01
updated: 2026-06-01
status: active
source_count: 1
tags: [analysis, skos, sparql, evaluation, terminological-mapping]
---

# Analysis - Avaliacao da Metodologia SPARQL + SKOS

## Objetivo
Consolidar os principais resultados do artigo sobre geracao de ligacoes semanticas com SKOS para uso reutilizavel em futuras ingestoes e comparacoes.

## Setup resumido do estudo
- Dominio: exploracao e producao de petroleo (E&P).
- Base observada: 5373 termos (Schlumberger Oilfield Glossary).
- Validacao: amostra de 341 links avaliados por especialista do dominio.
- Ferramentas/metodos: SPARQL CONSTRUCT, SKOS, Silk para exactMatch com Levenshtein (limiar 0.95).

## Resultado sintetico
- skos:exactMatch: 98,63% de acerto (alto).
- skos:related: 85,87% de acerto (bom, com excecoes).
- skos:broader e skos:narrower: ~72,4% (moderado).
- Acerto agregado reportado: 82,35%.

## Leitura critica
- A metodologia e forte para bootstrap de mapeamento terminologico, especialmente em equivalencia lexical proxima.
- O desempenho cai em relacoes hierarquicas/associativas quando depende apenas de matching de strings.
- O proprio artigo indica caminhos de melhoria: sinonimos, conhecimento de dominio, ML e mapeamento de classes/subclasses.

## Implicacoes para esta wiki
- Priorizar uso de regras para gerar candidatos, com revisao humana em predicados nao equivalentes.
- Registrar qualidade por tipo de predicado em futuras ingestoes para comparabilidade longitudinal.
- Evitar inferencias fortes de broader/narrower sem evidencia adicional alem de string matching.

## Contradicoes/Tensoes
- Tensao principal: eficacia global e alta para exactMatch, mas limitada para predicados dependentes de estrutura semantica nao capturada lexicalmente.

## Citacoes internas
- [Source - Ligacoes Semanticas Utilizando Predicados SKOS](../sources/2026-06-01-ligacoes-semanticas-utilizando-predicados-skos.md)
- [SKOS Mapping Predicates](../concepts/skos-mapping-predicates.md)
- [Linked Data Mashup (LDM)](../concepts/linked-data-mashup-ldm.md)
- [Wiki Home](../Home.md)
- [Index](../../index.md)
