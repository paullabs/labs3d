---
name: menu
description: Abre o menu da biblioteca labs3d com os estilos de vídeo feitos em código (espaço, atleta, narrador 3D, trânsito 3D e edição), mostra quais estão instalados, deixa a pessoa escolher e começa pelo estilo escolhido. Use quando a pessoa disser "labs3d", "biblioteca", "menu", "estilos", "quais estilos tem", "trocar de estilo" ou "usar um estilo".
---

# Menu da biblioteca labs3d

A labs3d é uma biblioteca de **estilos** de vídeo feitos em código. Cada estilo é um plugin com o seu próprio método, motor e regras. Aqui a pessoa escolhe um e você começa por ele. Para trocar de estilo, é só chamar este menu de novo.

## 1. Veja o que está instalado

Sem instalar nada ainda:

- **Claude Code:** rode `claude plugin list --json` e procure os itens `ID@labs3d` com `"enabled": true` (o `ID` está na tabela abaixo). Confira também o próprio `labs3d@labs3d`: se aparecer só com `"scope": "project"` ou `"local"`, a biblioteca **não está global** (some em outra pasta). Diga isso numa frase e ofereça `claude plugin install labs3d@labs3d --scope user`, que só roda com o sim da pessoa.
- **Codex:** rode `codex plugin list` e procure `ID@labs3d` com `installed, enabled`.
- Se o comando `claude` ou `codex` não existir, ignore aquele item. Se nenhum dos dois existir, mostre o menu sem o estado de instalação.

## 2. Os estilos

| ID do plugin | Estilo | O que faz | Por onde começa |
|---|---|---|---|
| `espaco-em-codigo` | **Espaço** | Shorts e Reels 9:16 de espaço e ciência em 3D feito em código: planetas, órbitas, explosões, marés, câmera de cinema, legenda palavra por palavra, voz e mixagem. | skill `espaco-em-codigo:novo-video` (cria o projeto antes, se preciso) |
| `atleta-em-codigo` | **Atleta (luta)** | Vídeos de luta com um atleta 3D sem rosto: boxe calibrado, aula completa, Reels de curiosidade e raio X. | skill `atleta-em-codigo:novo-projeto` |
| `3d-animation` | **Narrador 3D** | Reels narrados em animação 3D, com Blender por script: "Você acabou de entrar no…", bonecos em salas 3D, voz de teste grátis, som e render. | **a pessoa digita** `/3d-animation:iniciar` e depois `/3d-animation:novo-video` (essas duas só ela pode chamar) |
| `transito-3d` | **Trânsito 3D** | Animações de trânsito em mapa 3D real (OpenStreetMap), vistas de cima, com simulação de tráfego e câmera planejada, no Blender. | skill `transito-3d:transito-3d` |
| `edit-labs-ai` | **Edição** | Do vídeo longo ao vertical pronto: cortes de podcast, motion Vox, colagem em camadas, curiosidade histórica, documentário de arquivo e decupagem. Exige o Higgsfield conectado. | skill `edit-labs-ai:edit-labs-ai` |

**Em preparo** (ainda não instalam; cite só se a pessoa perguntar por mais estilos): Bob Construtor, estilo de explicador 3D realista, vetor vivo, 3D toon, episódios dramáticos, desenho narrado, anúncios de produto, sites cinematográficos, UGC para TikTok Shop, biblioteca de motion e cineasta de curtas com IA.

## 3. Mostre o menu

- **Com uma ferramenta de perguntas com opções clicáveis** (no Claude Code, `AskUserQuestion`, no máximo 4 opções por pergunta): faça duas perguntas curtas.
  1. "O que você quer fazer?" com duas opções: "Criar um vídeo 3D feito em código" e "Editar um vídeo que já tenho".
  2. Se escolheu criar: "Qual estilo?" com Espaço, Atleta (luta), Narrador 3D e Trânsito 3D. Se escolheu editar, vá direto para **Edição**.
  Em cada opção, a descrição diz em uma linha o que o estilo faz e se está **instalado** ou **falta instalar**.
- **Sem essa ferramenta** (Codex e outros agentes): escreva a lista numerada com o nome, a linha do que faz e o estado de instalação, e peça que a pessoa responda com o número ou o nome.

## 4. Depois da escolha

1. **Se o estilo não está instalado:** diga isso e mostre o comando, mas só rode com o sim da pessoa.
   - Claude Code: `claude plugin install ID@labs3d --scope user`, e depois ela fecha e abre o Claude Code (plugin novo só carrega ao reabrir).
   - Codex: `codex plugin add ID@labs3d`.
2. **Se está instalado:** diga em uma frase o que vai acontecer e comece pela coluna "Por onde começa".
   - Claude Code: chame a skill indicada com a ferramenta de skills.
   - Codex e outros agentes: abra e siga a skill indicada (ela aparece na lista de skills com esse nome).
   - Se a coluna diz que **a pessoa digita** o comando, mostre o comando e espere: você não consegue chamá-lo por ela.
3. Cada estilo tem as próprias regras e a própria licença; o estilo cuida de avisar. Nos estilos Espaço e Atleta, diga em uma linha que todo vídeo publicado leva a marca d'água fraca do canal, que é condição da licença.

## Regras

- Não instale nada, não gaste crédito de nenhum serviço pago e não publique nada sem o sim da pessoa.
- Não invente estilos: só os da tabela existem hoje.
- Se a pessoa já estava no meio de um vídeo de um estilo e escolheu outro, avise que o trabalho do primeiro fica salvo na pasta dele e volte a ele quando ela pedir.
