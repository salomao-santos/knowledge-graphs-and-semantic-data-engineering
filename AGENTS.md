# AGENTS.md

Operational schema para manter uma wiki de conhecimento incremental neste repositorio.

## 1. Objetivo
Manter uma wiki persistente, interligada e cumulativa em markdown, usando fontes imutaveis em raw/ e artefatos derivados em wiki/.

## 2. Estrutura do repositorio
- raw/: fontes originais (imutaveis).
- wiki/: paginas geradas e mantidas pelo agente.
- schema/templates/: templates para padronizar paginas.
- index.md: catalogo orientado a conteudo.
- log.md: historico cronologico append-only.

## 3. Regras globais
1. Nao editar arquivos em raw/ apos ingestao.
2. Toda ingestao deve atualizar index.md e log.md.
3. Toda pagina nova deve conter links internos relevantes (>= 2 quando possivel).
4. Ao detectar contradicao, registrar explicitamente em secao "Contradicoes/Tensoes" nas paginas afetadas.
5. Evitar duplicacao: preferir atualizar paginas existentes antes de criar novas.
6. Preservar rastreabilidade: toda afirmacao substantiva deve apontar para fontes (arquivo de source page e/ou raw).

## 4. Convencoes de caminhos
- Paginas de fonte: wiki/sources/YYYY-MM-DD-slug.md
- Entidades: wiki/entities/slug.md
- Conceitos: wiki/concepts/slug.md
- Analises: wiki/analysis/slug.md
- Relatorios: wiki/reports/lint-YYYY-MM-DD.md

Use slug em minusculo com hifens.

## 5. Frontmatter recomendado
Toda pagina em wiki/ deve incluir:
- title
- page_type (source|entity|concept|analysis|report|overview)
- created
- updated
- status (draft|active|deprecated)
- source_count
- tags

## 6. Workflow: Ingest
Quando uma nova fonte chega em raw/:
1. Ler a fonte.
2. Criar/atualizar pagina em wiki/sources/ usando o template source-summary.
3. Atualizar paginas relacionadas (entities/concepts/analysis) com novos achados.
4. Registrar contradicoes e mudancas de confianca quando houver.
5. Atualizar index.md com links e one-liners.
6. Acrescentar entrada em log.md no formato padrao.

## 7. Workflow: Query
Ao responder perguntas do usuario:
1. Ler index.md para roteamento inicial.
2. Ler paginas relevantes em wiki/.
3. Produzir resposta sintetica com citacoes de paginas.
4. Se o resultado for reutilizavel, salvar em wiki/analysis/ e indexar.
5. Registrar em log.md quando gerar artefato persistente.

## 8. Workflow: Lint
Em revisoes periodicas, verificar:
- Contradicoes entre paginas.
- Afirmacoes sem evidencia.
- Paginas orfas (sem links de entrada, quando detectavel).
- Conceitos citados sem pagina propria.
- Conteudo desatualizado por fontes mais novas.

Gerar relatorio em wiki/reports/lint-YYYY-MM-DD.md e registrar no log.

## 9. Politica de escrita
- Texto claro, objetivo, sem hype.
- Diferenciar fato, inferencia e hipotese.
- Explicitar nivel de confianca (alto|medio|baixo) quando relevante.
- Priorizar manutencao incremental sobre reescrita total.

## 10. Definicao de pronto (DoD)
Uma operacao e considerada completa quando:
- Arquivos alvo foram atualizados.
- index.md foi atualizado.
- log.md recebeu entrada.
- Links internos foram revisados.
- Nao ha inconsistencias obvias introduzidas na wiki.
