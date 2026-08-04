# 🔊 sfx-pra-video

**Guia aberto, em português, de _sound design_ pra vídeo curto** — quando usar qual som
pra segurar a atenção, e o que é seguro juridicamente. Reels, Shorts, TikTok, ads.

> [!IMPORTANT]
> A regra que decide tudo: **som viral famoso** só vale postando **orgânico, pelo app**.
> **Som royalty-free** vale em qualquer lugar, inclusive ad renderizado. Confundir os dois
> = strike de copyright. Isso está explicado no [capítulo 1](guia/1-os-dois-mundos.md), e
> todo som carrega um selo ✅ (pode ad) / 🚫 (só orgânico).

Este repo é **guia + os sons que realmente são livres**. Não re-hospeda áudio de terceiros
que a licença não permite — aponta a fonte. O valor está no conhecimento e nos sons
livres, não numa pilha de arquivos protegidos.

---

## 🚀 Como usar (baixar os sons)

Não tem instalador — é um guia + arquivos. Você **lê** os capítulos e **baixa** os sons.

**Baixar tudo (jeito mais fácil):** no topo desta página do GitHub, clique em
**`Code` → `Download ZIP`**. Descompacte e os sons estão na pasta `sons-livres/`.

**Ou via git:**
```bash
git clone https://github.com/aliborhothamud/sfx-pra-video.git
```

**Um som só:** abra o [catálogo](guia/4-catalogo.md), ache o que quer, e clique no arquivo
dentro de [`sons-livres/`](sons-livres/) → botão **`Download`**.

**Usar no seu vídeo:**
- **CapCut / Premiere / DaVinci:** arraste o `.wav`/`.ogg` da pasta `sons-livres/` pra
  timeline, no frame do corte/legenda/reveal. (Dosagem e volume: [capítulo 3](guia/3-dosagem-e-mix.md).)
- **Remotion:** copie o som pra `public/sfx/` do seu projeto e prenda ao frame:
  ```tsx
  <Sequence from={30}><Audio src={staticFile("sfx/riser__tonal.wav")} /></Sequence>
  ```
  Detalhes na [camada dev](guia/5-remotion.md).

> Os sons de `sons-livres/` (Kenney CC0 + sintetizados) são ✅ livres até pra ad. Os que
> **não** estão aqui (Mixkit, memes virais) você pega na fonte — ver [FONTES](fontes/FONTES.md).

---

## 🗺️ Por onde começar

**É criador / editor (CapCut, Premiere)?**
1. [Os dois mundos](guia/1-os-dois-mundos.md) — a regra jurídica (leia primeiro)
2. [O mapa de retenção](guia/2-mapa-de-retencao.md) — onde colocar cada som
3. [Dosagem e mixagem](guia/3-dosagem-e-mix.md) — quanto e como
4. [Catálogo](guia/4-catalogo.md) — a tabela de consulta

**Renderiza vídeo por código (Remotion)?** → tudo acima + [a camada dev](guia/5-remotion.md).

**Só quer os sons livres?** → [`sons-livres/`](sons-livres/) (Kenney CC0 + sintetizados,
✅ livres até pra ad). Créditos em [CREDITOS](sons-livres/CREDITOS.md).

---

## 📚 O guia

| Capítulo | Sobre |
|---|---|
| [1 · Os dois mundos](guia/1-os-dois-mundos.md) | A regra de licença que decide se você pode usar um som (app vs render) |
| [2 · O mapa de retenção](guia/2-mapa-de-retencao.md) | Onde colocar cada som no short — e o que a pesquisa REFUTOU |
| [3 · Dosagem e mixagem](guia/3-dosagem-e-mix.md) | 2–5 SFX por vídeo, −6 dB, sincronia por frame |
| [4 · Catálogo](guia/4-catalogo.md) | 60 sons curados por momento × categoria × licença × selo |
| [5 · A camada dev (Remotion)](guia/5-remotion.md) | Sincronia por frame, render-safe vs strike |

## 🎁 O que tem no repo

- **[`sons-livres/`](sons-livres/)** — 83 sons livres, renomeados pra nomes legíveis:
  - `sintetizados/` (4) — nossos, uso livre
  - `kenney-cc0/` (79) — Kenney, domínio público (ui · impacto · digital · stingers)
- **[`fontes/FONTES.md`](fontes/FONTES.md)** — onde baixar o que não pode ser
  redistribuído (Mixkit, remotion.media, soundcn, virais)
- **[`conteudo/`](conteudo/)** — a fábrica de shorts: o quadro "pra fazer X, usa esse
  som", a fila de ideias e os roteiros

---

## 🧭 Filosofia

Catálogo, não depósito. Cada som de terceiros aponta pro autor original — crédito e
licença são de quem criou. Aqui mora a **curadoria** (o que usar, quando, e sem tomar
strike) + os sons **realmente livres**.

## 📄 Licença

O guia, os textos e a curadoria: **[CC BY 4.0](LICENSE)** — use e adapte com atribuição.
Os áudios têm licenças próprias (ver [CREDITOS](sons-livres/CREDITOS.md) e
[FONTES](fontes/FONTES.md)).

Achou um som bom que não está aqui, ou um erro de licença? Manda um PR ou abre uma issue.
