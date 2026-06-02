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
