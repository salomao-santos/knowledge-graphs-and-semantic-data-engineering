---
title: Wiki Home
page_type: overview
created: 2026-06-01
updated: 2026-06-01

## Interface principal
- Obsidian e a interface recomendada para navegacao humana.
- Use Graph View para identificar hubs, lacunas e paginas orfas.
- Armazene anexos locais em raw/assets/.
status: active
source_count: 1
tags: [overview, wiki, obsidian]
---

# Wiki Home

## Escopo
Esta wiki organiza conhecimento sobre grafos de conhecimento, dados semanticos e engenharia semantica.
- Templates disponiveis em schema/templates/.
- Ja existem fontes e conceitos ingeridos em wiki/sources/, wiki/concepts/ e wiki/analysis/.
1. Use o Obsidian como interface principal de leitura e manutencao.
2. Use o Graph View para verificar topologia, paginas orfas e concentracoes tematicas.
- Ingerir o novo paper de saude publica adicionado em raw/papers/.
- Criar entidades centrais em wiki/entities/ conforme as proximas ingestoes.
- Rodar lint para mapear orfaos e contradicoes.
## Como usar
1. Adicione uma nova fonte em raw/.
2. Rode o fluxo de ingest para criar/atualizar paginas em wiki/.
3. Atualize index.md com links e one-liners.
4. Acrescente uma entrada em log.md.

## Estado atual
- Estrutura inicial criada.
- Primeira fonte ingerida em wiki/sources/2026-06-01-ligacoes-semanticas-utilizando-predicados-skos.md.
- Conceitos iniciais e uma analise comparativa criados.

## Proximas acoes sugeridas
- Criar paginas de entidades para organizacoes e ferramentas citadas (ex.: Silk, Schlumberger, PetroWiki).
- Ingerir uma segunda fonte para triangulacao de resultados.
- Rodar primeiro lint para mapear contradicoes, lacunas e paginas orfas.
