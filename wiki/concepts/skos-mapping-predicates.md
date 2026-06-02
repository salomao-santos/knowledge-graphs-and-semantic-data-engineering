---
title: Concept - SKOS Mapping Predicates
page_type: concept
created: 2026-06-01
updated: 2026-06-01
status: active
source_count: 1
tags: [concept, skos, mapping, rdf, sparql]
---

# Concept - SKOS Mapping Predicates

## Definicao
Conjunto de predicados SKOS usados para alinhar e relacionar termos entre vocabularios, com foco em mapeamento terminologico e descoberta de ligacoes semanticas.

## Predicados centrais
- skos:exactMatch: equivalencia forte entre termos em diferentes fontes.
- skos:broader: termo mais geral em relacao a outro.
- skos:narrower: termo mais especifico em relacao a outro.
- skos:related: associacao sem hierarquia estrita.

## Evidencias
- A fonte ingerida reporta geracao desses quatro predicados via consultas SPARQL CONSTRUCT.
- O melhor desempenho observado foi em skos:exactMatch (98,63%), enquanto broader/narrower/related ficaram em patamar inferior.

## Limites e riscos
- Regras baseadas em similaridade lexical podem falhar em sinonimia e variacoes sem alinhamento de string.
- A qualidade das terminologias de origem impacta diretamente a qualidade do mapeamento.

## Relacoes
- Relacionado a: [Linked Data Mashup (LDM)](linked-data-mashup-ldm.md)
- Evidenciado por: [Source - Ligacoes Semanticas Utilizando Predicados SKOS](../sources/2026-06-01-ligacoes-semanticas-utilizando-predicados-skos.md)
- Sintese aplicada: [Analysis - Avaliacao da Metodologia SPARQL + SKOS](../analysis/avaliacao-da-metodologia-sparql-skos.md)

## Contradicoes/Tensoes
- Tensao recorrente: alto desempenho para exactMatch nao se traduz automaticamente em desempenho equivalente para relacoes hierarquicas e associativas.
