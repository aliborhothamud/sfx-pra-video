# 5 · A camada dev (Remotion)

> Este capítulo é pra quem **renderiza vídeo por código** (Remotion). Se você edita no
> CapCut/Premiere, pode pular — mas a ideia de "prender o som ao frame" vale pra qualquer
> editor.

Renderizar vídeo por código muda o jogo do áudio em duas frentes: a **sincronia fica
perfeita e de graça**, e a **regra de licença fica ainda mais crítica** (porque tudo vira
um MP4 seu).

## Sincronia por frame — o `<Sequence from>`

No Remotion, o vídeo é determinístico: o frame N é sempre o frame N. Então você prende o
som ao frame exato do evento visual, e ele **nunca** sai do lugar — nem no preview, nem no
render final.

```tsx
import { Audio, Sequence, staticFile } from "remotion";

// o whoosh começa exatamente no frame 30 (onde o corte acontece)
<Sequence from={30}>
  <Audio src={staticFile("sfx/whoosh.wav")} />
</Sequence>

// o riser sobe por 20 frames e o pico cai no reveal (frame 90)
<Sequence from={70} durationInFrames={20}>
  <Audio src={staticFile("sfx/riser__tonal.wav")} volume={0.7} />
</Sequence>
```

Aqueles "3–4 frames de atraso que soam amador" ([capítulo 3](3-dosagem-e-mix.md)) somem:
o `from={N}` é o frame, ponto. Ajuste o volume com `volume={0.5}` pra manter os SFX
~6 dB abaixo da voz.

## Formatos — o `@remotion/media` lê todos

Os três formatos deste repo funcionam direto:

- `.ogg` (Kenney) · `.wav` (sintetizados) · `.mp3` (Mixkit/remotion, baixados da fonte)

Coloque os arquivos em `public/` e referencie com `staticFile("sfx/...")`.

## Render-safe vs strike — a regra que não muda

Como o Remotion **renderiza** o áudio dentro do MP4, você está sempre no "mundo do
arquivo seu" ([capítulo 1](1-os-dois-mundos.md)). Ou seja:

- ✅ **Pode entrar no render:** Sintetizado, CC0 (Kenney), Mixkit, remotion.media — tudo
  que tem selo ✅ no catálogo.
- 🚫 **NÃO pode entrar no render:** qualquer som viral/música famosa (selo 🚫). Se você
  precisa daquele meme de áudio, o vídeo tem que ser **orgânico, montado pelo app** — não
  renderizado.

Não existe meio-termo: um vine-boom da biblioteca `remotion.media` (✅) é seguro; o mesmo
efeito baixado de um vídeo viral (🚫) é strike. Sempre pelo catálogo.

## Empacotar os SFX no projeto

Copie os sons que vai usar pra `public/sfx/` do seu projeto Remotion. Os deste repo já
vêm com nome legível (`categoria__nome.ext`), então o código fica auto-explicativo:

```tsx
<Audio src={staticFile("sfx/impacto__vidro-pesado.ogg")} />
```

---

Anterior: **[4 · Catálogo](4-catalogo.md)** · Volta pro **[índice](../README.md)**
