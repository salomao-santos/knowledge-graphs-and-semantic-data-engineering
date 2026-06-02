---
title: Source - 2026-06-01 - Ligacoes Semanticas Utilizando Predicados SKOS
page_type: source
created: 2026-06-01
updated: 2026-06-01
status: active
source_count: 1
tags: [source, skos, sparql, oil-and-gas, terminological-mapping]
---

# Source - Ligacoes Semanticas Utilizando Predicados SKOS

## Metadados
- Data da fonte: 2017
- Tipo: artigo de conferencia (SBBD 2017)
- Referencia: Ricardo Avila; Salomao Santos; David Araujo; Vania Vidal; Jose Macedo
- Caminho em raw/: raw/papers/ligacoes-semanticas-utilizando-predicados-skos.pdf

## Resumo executivo
- O artigo propoe enriquecimento semantico entre glossarios de E&P de petroleo usando SKOS + consultas SPARQL com CONSTRUCT.
- A abordagem gera automaticamente ou semiautomaticamente ligacoes skos:exactMatch, skos:broader, skos:narrower e skos:related.
- A avaliacao com especialista do dominio indica desempenho alto em exactMatch e desempenho moderado nos demais predicados.
- Os autores destacam limites da abordagem baseada em comparacao de strings e sugerem sinonimos, ML e mapeamento de classes/subclasses como evolucao.

## Principais afirmacoes
- SKOS ajuda a mapear relacoes semanticas entre terminologias distintas e permite inferencias a partir de regras e hierarquias.
- Consultas SPARQL com CONSTRUCT podem materializar novos links semanticos em RDF/N-Triples.
- O predicado skos:exactMatch atingiu 98,63% de acerto na amostra avaliada.
- O desempenho de skos:broader, skos:narrower e skos:related foi menor (aprox. 72%-86%), mas considerado util para apoiar mapeamento terminologico.

## Evidencias e trechos relevantes
- Trecho: "consulta SPARQL com CONSTRUCT ... eficaz para a geracao semiautomatica de predicados skos:exactMatch".
- Trecho: coleta de 5373 termos do Schlumberger Oilfield Glossary para os experimentos.
- Trecho: avaliacao por geologo especialista com amostra de 341 exemplos de predicados gerados.
- Trecho: resultado agregado de 82,35% de ligacoes SKOS corretas.

## Entidades e conceitos mencionados
- Entidades: [Schlumberger Oilfield Glossary](../analysis/avaliacao-da-metodologia-sparql-skos.md), [PetroWiki - SPE E&P](../analysis/avaliacao-da-metodologia-sparql-skos.md), [Silk](../analysis/avaliacao-da-metodologia-sparql-skos.md)
- Conceitos: [SKOS Mapping Predicates](../concepts/skos-mapping-predicates.md), [Linked Data Mashup (LDM)](../concepts/linked-data-mashup-ldm.md)

## Contradicoes/Tensoes
- Nao foram identificadas contradicoes internas com outras fontes da wiki nesta ingestao inicial.
- Tensao metodologica: o artigo reporta eficacia geral, mas reconhece queda relevante em predicados dependentes de matching lexical.

## Impacto na wiki
- Paginas criadas:
  - wiki/sources/2026-06-01-ligacoes-semanticas-utilizando-predicados-skos.md
  - wiki/concepts/skos-mapping-predicates.md
  - wiki/concepts/linked-data-mashup-ldm.md
  - wiki/analysis/avaliacao-da-metodologia-sparql-skos.md
- Paginas atualizadas:
  - wiki/Home.md
  - index.md
  - log.md
- Hipoteses reforcadas/enfraquecidas:
  - Reforcada: mapeamento semantico assistido por regras e viavel para bootstrap.
  - Enfraquecida: comparacao lexical pura e suficiente para todos os tipos de relacao semantica.

## Perguntas em aberto
- Como combinar regras SPARQL com embeddings ou ML para reduzir falso positivo/negativo em broader/narrower/related?
- Qual metrica de cobertura entre vocabularios pode ser derivada da distribuicao de predicados gerados?

## Citacoes internas
- [Wiki Home](../Home.md)
- [Index](../../index.md)
- [SKOS Mapping Predicates](../concepts/skos-mapping-predicates.md)
- [Linked Data Mashup (LDM)](../concepts/linked-data-mashup-ldm.md)
- [Analysis - Avaliacao da Metodologia SPARQL + SKOS](../analysis/avaliacao-da-metodologia-sparql-skos.md)
