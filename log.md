# Log

Registro cronologico append-only das operacoes na wiki.

Formato recomendado para cada entrada:
## [YYYY-MM-DD] tipo | titulo curto
- Objetivo:
- Arquivos lidos:
- Arquivos criados/atualizados:
- Resumo da mudanca:
- Proximos passos:

## [2026-06-01] bootstrap | inicializacao da estrutura
- Objetivo: Criar base operacional da LLM Wiki neste repositorio.
- Arquivos lidos: README.md, Bem-vindo.md.
- Arquivos criados/atualizados: index.md, log.md, AGENTS.md, wiki/Home.md, templates em schema/templates/.
- Resumo da mudanca: Estrutura inicial pronta para ingest, query e lint.
- Proximos passos: Ingerir a primeira fonte em raw/ e gerar primeira pagina em wiki/sources/.

## [2026-06-01] ingest | ligacoes-semanticas-utilizando-predicados-skos

## [2026-06-01] setup | execucao do prompt EN e configuracao MCP
- Objetivo: Executar o setup solicitado em .github/prompts/prompt-ia-setup-en.md e configurar o servidor MCP document loader.
- Arquivos lidos: .github/prompts/prompt-ia-setup-en.md; .vscode/settings.json.
- Arquivos criados/atualizados: CLAUDE.md; copilot-instructions.md; AGENTS.md; schema/templates/concept-page.md; schema/templates/analysis-page.md; wiki/Home.md; .vscode/mcp.json; raw/papers/2023-sbbd-paper-24319.pdf.
- Resumo da mudanca: Setup operacional alinhado ao prompt EN, com QA gates e modo Obsidian explicitos, e MCP configurado para awslabs.document-loader-mcp-server via uvx.
- Proximos passos: Ingerir o novo paper de saude publica em wiki/sources/, atualizar conceitos relacionados e indexar os artefatos.

## [2026-06-01] maintenance | rename dos PDFs em raw/papers
- Objetivo: Renomear os arquivos PDF em raw/papers para slugs baseados no titulo de cada artigo.
- Arquivos lidos: PDFs em raw/papers/ via metadados e primeira pagina; wiki/sources/2026-06-01-ligacoes-semanticas-utilizando-predicados-skos.md.
- Arquivos criados/atualizados: nomes dos PDFs em raw/papers/; wiki/sources/2026-06-01-ligacoes-semanticas-utilizando-predicados-skos.md; log.md.
- Resumo da mudanca: Todos os PDFs foram renomeados para lowercase-kebab-case com base no titulo do artigo; colisões de nome foram resolvidas com sufixo numerico; a referencia viva ao arquivo de SKOS foi atualizada.
- Proximos passos: Atualizar futuras paginas de source para referenciar os novos slugs em raw/papers/ quando novos papers forem ingeridos.

## [2026-06-02] maintenance | rename dos PDFs em raw/papers/LLM
- Objetivo: Renomear PDFs da pasta raw/papers/LLM para slugs baseados no titulo dos artigos.
- Arquivos lidos: PDFs em raw/papers/LLM via metadados e primeira pagina; index.md; log.md.
- Arquivos criados/atualizados: nomes dos PDFs em raw/papers/LLM; index.md; log.md.
- Resumo da mudanca: Seis arquivos PDF existentes foram renomeados para lowercase-kebab-case; uma colisao de titulo foi resolvida com sufixo numerico (-2).
- Proximos passos: Ao ingerir essas fontes, usar os novos nomes canônicos nas paginas de wiki/sources.

## [2026-06-02] ingest | construcao-de-linked-data-mashup-para-integracao-de-dados-da-saude-publica
- Objetivo: Extrair todo o conteudo do artigo em PDF para um arquivo Markdown sem traducao.
- Arquivos lidos: raw/papers/ptbr/construcao-de-linked-data-mashup-para-integracao-de-dados-da-saude-publica/construcao-de-linked-data-mashup-para-integracao-de-dados-da-saude-publica.pdf.
- Arquivos criados/atualizados: wiki/sources/2026-06-02-construcao-de-linked-data-mashup-para-integracao-de-dados-da-saude-publica.md; index.md; log.md.
- Resumo da mudanca: Conteudo textual integral do PDF extraido para Markdown em wiki/sources com frontmatter minimo.
- Proximos passos: Revisar qualidade de OCR/extracao (acentos e hifenizacao) e, se necessario, gerar versao alternativa com outra ferramenta de extração.

## [2026-06-02] ingest | construcao-do-dataset-semantico-de-pessoas-juridicas
- Objetivo: Extrair todo o conteudo do artigo em PDF para um arquivo Markdown sem traducao.
- Arquivos lidos: raw/papers/ptbr/construcao-do-dataset-semantico-de-pessoas-juridicas.pdf.
- Arquivos criados/atualizados: wiki/sources/2026-06-02-construcao-do-dataset-semantico-de-pessoas-juridicas.md; index.md; log.md.
- Resumo da mudanca: Conteudo textual integral do PDF extraido para Markdown em wiki/sources com frontmatter minimo.
- Proximos passos: Revisar qualidade de OCR/extracao (acentos, hifenizacao e quebras de pagina) e inserir figuras em raw/assets quando necessario.

## [2026-06-02] maintenance | limpeza-de-artefatos-pdf-nos-artigos-extraidos
- Objetivo: Remover cabecalhos e rodapes de pagina do PDF que tornavam a leitura desorganizada.
- Arquivos lidos: wiki/sources/2026-06-02-construcao-de-linked-data-mashup-para-integracao-de-dados-da-saude-publica.md; wiki/sources/2026-06-02-construcao-do-dataset-semantico-de-pessoas-juridicas.md.
- Arquivos criados/atualizados: wiki/sources/2026-06-02-construcao-de-linked-data-mashup-para-integracao-de-dados-da-saude-publica.md (312→286 linhas); wiki/sources/2026-06-02-construcao-do-dataset-semantico-de-pessoas-juridicas.md (633→580 linhas); log.md.
- Resumo da mudanca: Removidos cabecalhos repetitivos ("31th SBBD – SBBD Proceedings" e "Proceedings of the VI Dataset Showcase Workshop") e numeros de pagina isolados que apareciam intercalados no texto. Mantidos apenas os cabecalhos originais apos o frontmatter. Reduzidas linhas vazias excessivas. Total: 79 linhas removidas (26 do artigo 1, 53 do artigo 2). Conteudo textual dos artigos preservado integralmente sem alteracoes ou traducoes.
- Proximos passos: Artigos prontos para uso e criacao de paginas derivadas em wiki/concepts/ e wiki/entities/.

## [2026-06-02] maintenance | correcao-de-paths-das-imagens
- Objetivo: Corrigir caminhos relativos das imagens nos artigos extraidos para que apontem corretamente para raw/assets/.
- Arquivos lidos: raw/papers/ptbr/construcao-de-linked-data-mashup-para-integracao-de-dados-da-saude-publica/construcao-de-linked-data-mashup-para-integracao-de-dados-da-saude-publica.md; raw/papers/ptbr/construcao-do-dataset-semantico-de-pessoas-juridicas/construcao-do-dataset-semantico-de-pessoas-juridicas.md; raw/assets/ptbr/.
- Arquivos criados/atualizados: raw/papers/ptbr/construcao-de-linked-data-mashup-para-integracao-de-dados-da-saude-publica/construcao-de-linked-data-mashup-para-integracao-de-dados-da-saude-publica.md; raw/papers/ptbr/construcao-do-dataset-semantico-de-pessoas-juridicas/construcao-do-dataset-semantico-de-pessoas-juridicas.md; log.md.
- Resumo da mudanca: Alterados todos os paths de imagens de ../../raw/assets/ para ../../../assets/ (8 imagens no total: 2 do artigo de mashup, 6 do artigo de dataset semantico). Removidos separadores horizontais (---) que estavam causando quebras visuais indesejadas nos paragrafos apos as figuras.
- Proximos passos: Imagens acessiveis corretamente; artigos prontos para processamento derivado na wiki.

## [2026-06-02] ingest-derivado | processamento-completo-dataset-semantico-pj
- Objetivo: Processar completamente o artigo sobre dataset semantico de pessoas juridicas, gerando paginas derivadas de conceitos, entidades e analise conforme workflow de ingest.
- Arquivos lidos: raw/papers/ptbr/construcao-do-dataset-semantico-de-pessoas-juridicas/construcao-do-dataset-semantico-de-pessoas-juridicas.md; index.md; log.md; AGENTS.md; CLAUDE.md.
- Arquivos criados/atualizados: wiki/concepts/data-lakehouse.md; wiki/concepts/arquitetura-medallion.md; wiki/concepts/delta-lake.md; wiki/entities/receita-federal-brasil.md; wiki/analysis/metodologia-data-lakehouse-datasets-semanticos.md; index.md; log.md.
- Resumo da mudanca: Criadas 5 paginas derivadas do artigo fonte: (1) Conceito Data Lakehouse - arquitetura hibrida inovadora; (2) Conceito Arquitetura Medallion - pattern Bronze/Silver/Gold com 3 camadas; (3) Conceito Delta Lake - framework com ACID e versionamento; (4) Entidade RFB - orgao governamental fonte dos dados CNPJ; (5) Analise comparativa - avaliacao da metodologia proposta vs abordagens tradicionais. Todas as paginas seguem templates com frontmatter completo, pelo menos 2 links internos, evidencias rastreadas ao artigo fonte. Index.md atualizado com 3 conceitos novos, 1 entidade, 1 analise. Total de paginas wiki: 3 sources, 1 entidade, 5 conceitos, 2 analises.
- Proximos passos: Processar artigo de Linked Data Mashup para Saude Publica de forma similar; criar possiveis paginas de entidades adicionais (SINASC, e-SUS); lint para verificar consistencia e links ausentes.
