# 001 — O riser que segura antes do reveal

**Som:** `riser__tonal` · **Selo:** ✅ Pode gravar ad · **Onde:** 📦 `sons-livres/sintetizados/riser__tonal.wav`

## Gancho (0–3s)
"Sabe aquele som que sobe *bem* antes do momento importante do vídeo? Ó por que ele
prende a sua atenção 👇"

## O ponto (o que ensinar)
- **Que som:** um *riser* — um som que sobe de intensidade — que entra nos ~2 segundos
  **antes** do reveal/punchline.
- **Momento:** pré-reveal. O pico do riser tem que cair **exatamente** no reveal.
- **Por que funciona:** o riser é pura antecipação. O cérebro sente que algo vem aí e não
  desgruda esperando o payoff.

## Demo
- **Antes:** o reveal aparece seco → passa batido.
- **Depois:** o mesmo reveal com o riser subindo antes → o olho fica preso até o pico.
- Mostra os dois lado a lado, mesmo corte.

## Como fazer
- **CapCut:** joga o `riser__tonal` na trilha ~2s antes do reveal; alinha o fim do riser
  com o frame do reveal.
- **Remotion:**
  ```tsx
  <Sequence from={70} durationInFrames={20}>
    <Audio src={staticFile("sfx/riser__tonal.wav")} volume={0.7} />
  </Sequence>
  ```
  (o pico cai no frame 90, onde está o reveal)

## Detalhe que separa amador
O erro nº1: riser **sem** payoff no pico. Se o som sobe e não acontece nada, frustra.
Sobe → **paga**.

## CTA
"Esse riser é nosso, livre pra usar até em ad — tá no repo. Catálogo completo de sons no
link da bio 🔊"
