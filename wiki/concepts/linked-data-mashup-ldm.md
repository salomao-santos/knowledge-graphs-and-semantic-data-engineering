---
title: Concept - Linked Data Mashup (LDM)
page_type: concept
created: 2026-06-01
updated: 2026-06-01
status: active
source_count: 1
tags: [concept, linked-data, integration, rdf, ontology]
---

# Concept - Linked Data Mashup (LDM)

## Definicao
Abordagem de integracao de fontes heterogeneas na Web de Dados por meio de modelos semanticos (OD/OF), links RDF e mecanismos de publicacao/consulta.

## Papel no artigo
- O trabalho usa LDM para integrar glossarios de E&P de petroleo.
- A opcao adotada e materializada: consolidacao em base central de conhecimento.
- A ontologia de dominio e as ontologias-fonte orientam o mapeamento de termos e a geracao de triplas.

## Evidencias
- A fonte descreve etapas de modelagem OD/OF, captura por crawlers, persistencia em MongoDB e triplificacao para RDF.
- O uso de LDM e posicionado como mecanismo para interoperabilidade semantica e inferencia.

## Relacoes
- Relacionado a: [SKOS Mapping Predicates](skos-mapping-predicates.md)
- Evidenciado por: [Source - Ligacoes Semanticas Utilizando Predicados SKOS](../sources/2026-06-01-ligacoes-semanticas-utilizando-predicados-skos.md)
- Sintese aplicada: [Analysis - Avaliacao da Metodologia SPARQL + SKOS](../analysis/avaliacao-da-metodologia-sparql-skos.md)

## Contradicoes/Tensoes
- Nao ha contradicao explicita com outras fontes na wiki.
- Tensao de engenharia: custo de modelagem e qualidade dos dados de origem continuam sendo fatores limitantes.
