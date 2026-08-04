# Design — `som-que-segura` (guia SFX open source)

**Data:** 2026-08-04
**Autor:** Ali (Breja Uva Brain / Montaha Labs) + Claude
**Status:** design validado no brainstorming; pronto pra implementar

---

## Propósito

Repositório **público, em português, open source** que ensina **sound design para vídeo
curto** — quando usar qual som pra segurar retenção, e o que é seguro juridicamente.

- **Coração = o guia/aula** (know-how). Os sons livres entram como apêndice tocável.
- **Público em camadas:** craft + jurídico pra todo criador na frente; camada dev
  (Remotion, render-safe) pra quem coda no fim.
- Alimenta um **quadro de shorts** ("pra fazer X, usa esse som") cujo CTA aponta pro repo.

## Filosofia — "licença primeiro" (igual `claude-melhores-skills`)

- Abre com a **regra dos dois mundos**: som viral = só orgânico pelo app · royalty-free =
  renderiza à vontade. Todo som citado carrega selo **✅ ad / 🚫 só orgânico**.
- **Não re-hospeda** o que a licença proíbe (Mixkit, remotion.media) — linka a fonte.
  Re-hospeda só **Kenney (CC0)** + **sintetizados (próprios)**.

## Estrutura de arquivos

```
som-que-segura/
├── README.md                 # hub: pitch + os 2 mundos + índice navegável + "por onde começar"
├── LICENSE                   # CC-BY-4.0 (a aula/curadoria é do Ali, com crédito)
├── guia/
│   ├── 1-os-dois-mundos.md   # regra jurídica (base: TRENDING-SOUNDS.md) + checklist
│   ├── 2-mapa-de-retencao.md # onde colocar cada som (base: README sfx) + "o que a pesquisa REFUTOU"
│   ├── 3-dosagem-e-mix.md     # 2–5 SFX, −6 dB, sincronia, não repetir
│   ├── 4-catalogo.md         # tabela mestra GERADA da database Notion (Momento×Categoria×Licença×selo)
│   └── 5-remotion.md         # camada dev: <Sequence from>, render-safe vs strike, empacotar SFX
├── sons-livres/              # SÓ redistribuível
│   ├── sintetizados/         # próprios (risers, bass-drop)
│   ├── kenney-cc0/           # ui, impact, digital, stingers (CC0)
│   └── CREDITOS.md
├── fontes/
│   └── FONTES.md             # onde baixar Mixkit / remotion.media / soundcn (não re-hospedado)
└── conteudo/                 # fábrica de shorts
    ├── README.md             # formato do quadro + como um short vira linha do catálogo
    ├── fila.md               # backlog "1 som por vídeo" mapeado ao catálogo
    └── roteiros/
        └── 001-clique-de-teclado.md
```

## Decisões travadas

1. **Nome:** `som-que-segura` (a confirmar no ato de criar).
2. **Camada Remotion** = arquivo próprio `guia/5-remotion.md`.
3. **Kenney entra de fato** (~80 `.ogg` leves) em `sons-livres/kenney-cc0/`.
4. **`conteudo/` já nasce** no repo (sinaliza que vira aula).
5. **Fonte da verdade da taxonomia = database Notion "🔊 Biblioteca de Áudio"**
   (collection `3973cdf0-8a15-490a-aef5-f64ca70e3c0d`). Catálogo v1 **gerado do Notion**.
   Taxonomia: Categoria · Estilo · Licença · Momento no vídeo · Sentimento · Popularidade ·
   Uso em ad (✅/🚫) · Pasta · Uso · Variações.
6. **Renomear todos** os arquivos livres pro padrão legível `categoria__nome__momento.ext`
   (ex.: `riser__tonal__pre-reveal.wav`).

## Template de roteiro de short (`conteudo/roteiros/NNN-*.md`)

- **Gancho (0–3s):** "Sabe esse som de [X] nos vídeos? Ó como faz 👇"
- **O som:** qual + pasta no catálogo + selo ✅/🚫
- **Onde pegar:** link da fonte OU `sons-livres/…`
- **Como aplicar:** 1 linha CapCut + 1 linha Remotion
- **CTA:** "catálogo completo no link"

## Fontes de conteúdo já existentes (reaproveitar)

- `conteudo-videos/public/sfx/README.md` — mapa de retenção, dosagem, licenças, inventário
- `conteudo-videos/public/sfx/TRENDING-SOUNDS.md` — os dois mundos, sons virais
- Database Notion "🔊 Biblioteca de Áudio" — taxonomia + linhas populadas
- Escrita final passa pela skill `stop-slop` (tirar cara de IA)

## Fora de escopo (v1 — YAGNI)

- Script de sync Notion↔repo automático (v1 é geração única; virar script se pedir).
- Player web / site. Redistribuir Mixkit/remotion/soundcn.

## Próximos passos

1. Criar repo `som-que-segura` (local + GitHub público).
2. `writing-plans` → plano de implementação detalhado.
3. Executar: reescrever guia, exportar catálogo do Notion, renomear+copiar sons livres,
   escrever FONTES/CREDITOS, primeiro roteiro, README hub.
4. Checkpoint antes do push público (outward-facing).
