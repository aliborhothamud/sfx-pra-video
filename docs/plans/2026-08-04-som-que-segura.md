# `som-que-segura` — Plano de Implementação

> **For Claude:** REQUIRED SUB-SKILL: Use superpowers:executing-plans to implement this plan task-by-task.

**Goal:** Criar um repositório público open source (PT) que ensina sound design pra vídeo curto — guia em camadas + os sons realmente livres, com filosofia "licença primeiro".

**Architecture:** Repo estático de markdown + áudios livres. O guia reaproveita `README.md` e `TRENDING-SOUNDS.md` já existentes; o catálogo é gerado da database Notion "🔊 Biblioteca de Áudio". Só CC0/sintetizados são redistribuídos; Mixkit/remotion/soundcn viram ponteiro. Igual à filosofia do `claude-melhores-skills`.

**Tech Stack:** Markdown, git, GitHub (público). Fontes: 2 docs locais + database Notion `collection://3973cdf0-8a15-490a-aef5-f64ca70e3c0d`. Skill `stop-slop` no texto final.

**Local de trabalho:** `C:/Users/aliha/som-que-segura/` (novo repo, separado — NÃO dentro de conteudo-videos nem de ~/.claude).

**Fontes de conteúdo (reaproveitar, não reinventar):**
- `C:/Users/aliha/conteudo-videos/public/sfx/README.md` — mapa de retenção, dosagem, licenças, "o que a pesquisa REFUTOU"
- `C:/Users/aliha/conteudo-videos/public/sfx/TRENDING-SOUNDS.md` — os dois mundos, sons virais
- Database Notion (60 linhas curadas) — taxonomia + metadados por som

**Guardrails (inegociáveis):**
- Nenhum arquivo Mixkit, remotion.media, soundcn ou `_copyright-organic-only` vai pro repo. Só Kenney CC0 + sintetizados.
- Checkpoint com o Ali ANTES do push público (outward-facing).
- Provado, não afirmado: cada task tem verificação concreta.

---

## Task 1: Esqueleto do repo

**Files:**
- Create: `som-que-segura/` (pastas: `guia/`, `sons-livres/{sintetizados,kenney-cc0}/`, `fontes/`, `conteudo/roteiros/`, `docs/plans/`)
- Create: `som-que-segura/LICENSE` (CC-BY-4.0)
- Create: `som-que-segura/.gitignore`

**Step 1:** `git init` em `C:/Users/aliha/som-que-segura`; criar a árvore de pastas.
**Step 2:** Gravar `LICENSE` = texto oficial CC-BY-4.0 (a curadoria/aula é do Ali, uso livre com crédito).
**Step 3:** `.gitignore` = `.DS_Store`, `Thumbs.db`, `node_modules/`.
**Step 4:** Copiar este plano pra `docs/plans/2026-08-04-som-que-segura.md` e o design pra `docs/plans/`.
**Step 5 (verificação):** `find som-que-segura -type d` mostra a árvore completa; LICENSE existe.
**Step 6:** Commit `chore: esqueleto do repo + licenca CC-BY-4.0`.

## Task 2: Exportar o catálogo curado do Notion

**Files:** Create: `som-que-segura/.build/catalogo.json` (dados brutos, temporário — no .gitignore)

**Step 1:** Query SQL na database: `SELECT Som, Categoria, "Momento no vídeo", Sentimento, Estilo, Licença, "Uso em ad", Popularidade, Pasta, Uso, Variações` de todas as 60 linhas.
**Step 2:** Salvar como JSON estruturado pra alimentar o catálogo.
**Step 3 (verificação):** JSON tem 60 objetos; campos batem com o schema.
**Step 4:** Commit (ou manter em .build/ ignorado — decidir: manter fora do git).

## Task 3: Renomear + copiar os sons livres

**Files:**
- Create: `sons-livres/kenney-cc0/*.ogg` (de ui-kit, impact-kit, digital-kit, stingers-kenney)
- Create: `sons-livres/sintetizados/*.wav` (risers/ + bass-drop)

**Regra de nome legível:** `categoria__nome__momento.ext`
- Ex.: `riser-tonal.wav` → `riser__tonal__pre-reveal.wav`
- Ex.: `impactGlass_heavy_000.ogg` → `impacto__vidro-pesado__punchline.ogg`
- Momento vem da database quando o som está curado; quando não, inferir da categoria da pasta.

**Step 1:** Montar tabela de-para (nome antigo → nome novo) num `.build/rename-map.tsv`. Priorizar os que estão na database (têm Momento oficial).
**Step 2:** Mostrar o de-para pro Ali revisar (nomes são outward-facing/didáticos). ⏸️ CHECKPOINT curto.
**Step 3:** Copiar+renomear pras subpastas (cópia, não move — não mexer no projeto original).
**Step 4 (verificação):** contagem de arquivos em `sons-livres/` == esperado; nenhum Mixkit/remotion/organic presente (`grep -L` por origem).
**Step 5:** Commit `feat: sons livres (Kenney CC0 + sintetizados) renomeados`.

## Task 4: `guia/1-os-dois-mundos.md`

**Step 1:** Reescrever a partir de `TRENDING-SOUNDS.md` — a tabela app-only vs renderizado, exemplos (Thunderstruck), tradução pro fluxo do leitor.
**Step 2:** Adicionar o **checklist "posso usar esse som aqui?"** (fluxograma simples).
**Step 3 (verificação):** links válidos; selo ✅/🚫 explicado; sem jargão jurídico solto.
**Step 4:** Commit.

## Task 5: `guia/2-mapa-de-retencao.md`

**Step 1:** Reescrever o mapa de colocação do `README.md` sfx (Hook→corte→legenda→pré-reveal→punchline→CTA), cada beat com o porquê.
**Step 2:** Incluir a seção honesta **"o que a pesquisa REFUTOU"** (não existe dado empírico; é convenção de craft).
**Step 3 (verificação):** todos os 6 momentos cobertos; cada um mapeia a uma Categoria da database.
**Step 4:** Commit.

## Task 6: `guia/3-dosagem-e-mix.md`

**Step 1:** 2–5 SFX por vídeo, −6 dB abaixo da voz, sincronia (3–4 frames já soa amador), não repetir até dessensibilizar. Base: seção "Dosagem" do README.
**Step 2 (verificação):** regras concretas e acionáveis, sem enrolação.
**Step 3:** Commit.

## Task 7: `guia/4-catalogo.md` (gerado do Notion)

**Step 1:** Gerar tabela mestra do `.build/catalogo.json`: colunas Som · Categoria · Momento · Sentimento · Licença · **selo ✅/🚫** · Onde pegar (link fonte ou `sons-livres/…`).
**Step 2:** Agrupar por Momento no vídeo (ordem do short). Marcar ⭐/🔥 popularidade.
**Step 3 (verificação):** nº de linhas == 60; todo som redistribuível linka pro arquivo local; todo Mixkit/remotion linka pra fonte.
**Step 4:** Commit.

## Task 8: `guia/5-remotion.md` (camada dev)

**Step 1:** `<Sequence from={N}>` prende som ao frame; `@remotion/media` lê ogg/mp3/wav; render-safe vs strike; como empacotar SFX no projeto. Base: notas do README + conhecimento Remotion.
**Step 2 (verificação):** exemplo de código Remotion correto e mínimo; deixa claro o que NÃO renderizar (viral).
**Step 3:** Commit.

## Task 9: Créditos e Fontes

**Files:** Create `sons-livres/CREDITOS.md`, `fontes/FONTES.md`
**Step 1:** `CREDITOS.md` — Kenney (CC0, crédito por gentileza) + sintetizados (próprios).
**Step 2:** `FONTES.md` — onde baixar Mixkit, remotion.media, soundcn (link + licença + "não re-hospedado aqui"). Estilo tabela igual "Fontes & créditos" do claude-melhores-skills.
**Step 3 (verificação):** todo link resolve; nenhuma promessa de arquivo que não está no repo.
**Step 4:** Commit.

## Task 10: `conteudo/` (fábrica de shorts)

**Files:** `conteudo/README.md`, `conteudo/fila.md`, `conteudo/roteiros/001-clique-de-teclado.md`
**Step 1:** `README.md` — formato do quadro ("pra fazer X, usa esse som") + como um short vira linha do catálogo + template de roteiro.
**Step 2:** `fila.md` — backlog de ideias (teclado, whoosh, riser, vine-boom, cash register, notificação…), cada uma mapeada a Momento×Categoria.
**Step 3:** `roteiros/001-clique-de-teclado.md` — primeiro roteiro completo no template (gancho→som→onde pegar→aplicar→CTA).
**Step 4 (verificação):** roteiro segue o template; aponta pra um som real do catálogo.
**Step 5:** Commit.

## Task 11: `README.md` hub

**Step 1:** Pitch (o que é / pra quem) + a **regra dos 2 mundos** logo no topo + **índice navegável** (âncoras HTML, igual claude-melhores-skills) + "por onde começar" (criador vs dev).
**Step 2:** Badge de licença CC-BY-4.0; link pra cada capítulo do guia.
**Step 3 (verificação):** todos os links do índice batem com âncoras/arquivos (script de validação).
**Step 4:** Commit.

## Task 12: Polir (stop-slop) + revisão

**Step 1:** Rodar a skill `stop-slop` em todos os `.md` do guia + README (tirar cara de IA).
**Step 2 (verificação):** leitura final; tom de aula, PT correto com acentos, sem AI-slop.
**Step 3:** Commit `style: passa stop-slop no guia`.

## Task 13: Checkpoint + publicar

**Step 1:** ⏸️ CHECKPOINT — mostrar ao Ali a árvore final + o README renderizado + confirmar nome do repo e que vai público.
**Step 2:** Criar repo no GitHub (`gh repo create aliborhothamud/som-que-segura --public`).
**Step 3:** `git push`.
**Step 4 (verificação):** repo público no ar; README renderiza; links funcionam.
**Step 5:** (opcional) Atualizar Notion "🎬 Content Creator" com o link do repo; registrar na fila de conteúdo.

---

## Ordem / dependências
- Task 1 → 2 → 3 (checkpoint nomes) em sequência.
- Tasks 4–10 são independentes entre si (podem paralelizar), mas 7 depende de 2, e 10 referencia 7.
- Task 11 depende de 4–10 (índice aponta pra tudo). Task 12 depois de todo texto. Task 13 por último.

## Fora de escopo (YAGNI v1)
- Script de sync Notion↔repo automático. Player web. Redistribuir Mixkit/remotion/soundcn.
- Empacotar os 806 do soundcn (é re-host de projeto MIT que já existe → só linkar).
