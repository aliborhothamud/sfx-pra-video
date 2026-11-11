---
tipo: decisao
slug: conteudo
status: ativo
descricao: O repo só redistribui sons Kenney CC0 e sintetizados próprios; o resto vira link, e o guia sai em CC BY 4.0
autor: ali
created: 2026-08-04
atualizado: 2026-11-11
substitui:
---

# Licença primeiro: só redistribuir o que a licença permite

## Contexto
O guia nasceu de uma biblioteca de áudio particular com centenas de sons de origens diferentes (Mixkit,
remotion.media, soundcn, sons virais). Um repo público que re-hospedasse esses arquivos violaria as licenças
de parte deles e passaria adiante um risco de copyright para quem usa o guia.

## Decisão
- Só entram em `sons-livres/` os sons **Kenney (CC0)** e os **sintetizados aqui**.
- Mixkit, remotion.media, soundcn e sons virais **nunca entram**: viram link em `fontes/FONTES.md`.
- Todo som citado leva selo: ✅ pode ir em anúncio renderizado · 🚫 só orgânico, postado pelo app da plataforma.
  Na dúvida, 🚫.
- O guia e a curadoria saem em **CC BY 4.0** (crédito ao autor).

## Consequências
- O repo fica pequeno e sem risco jurídico; o valor está na aula, não no acervo.
- O catálogo (`guia/4-catalogo.md`) é gerado do catálogo do mantenedor; mudar só o `.md` cria duas verdades.

## Alternativas
- **Re-hospedar tudo com crédito:** descartada; crédito não substitui licença de redistribuição.

## Fonte
`docs/plans/2026-08-04-som-que-segura-design.md` ("Filosofia: licença primeiro" e "Decisões travadas"), validado
no brainstorming de 04/08/2026; regra repetida no `CLAUDE.md` deste repo. ADR escrito na consolidação de 11/11/2026.
