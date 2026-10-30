# labs3d

Biblioteca de **estilos de vídeo feitos em código**. Você instala uma vez, chama o menu, escolhe o estilo e usa. Para trocar de estilo, chame o menu de novo.

## Instalar

No **Claude Code** (instala a biblioteca e todos os estilos de uma vez):

```bash
claude plugin marketplace add paullabs/labs3d
claude plugin install labs3d@labs3d --scope user
```

No **Codex** (o Codex não instala os estilos sozinho, então são seis comandos):

```bash
codex plugin marketplace add paullabs/labs3d
for p in labs3d espaco-em-codigo atleta-em-codigo 3d-animation transito-3d edit-labs-ai; do codex plugin add $p@labs3d; done
```

`--scope user` instala para todas as suas pastas. Para conferir, `claude plugin list` tem de mostrar `Scope: user` e `codex plugin list` tem de mostrar `installed, enabled`. Depois de instalar, feche e abra o Claude Code.

## Usar

No Claude Code, digite `/labs3d:menu`. No Codex, peça "abrir o menu do labs3d". O menu mostra os estilos, diz quais estão instalados e começa pelo que você escolher.

## Os estilos

| Estilo | Plugin | O que faz |
|---|---|---|
| **Espaço** | `espaco-em-codigo` | Shorts e Reels de espaço e ciência em 3D feito em código. |
| **Atleta (luta)** | `atleta-em-codigo` | Vídeos de luta com um atleta 3D sem rosto: boxe, aula, Reels, raio X. |
| **Narrador 3D** | `3d-animation` | Reels narrados em animação 3D, com Blender por script. |
| **Trânsito 3D** | `transito-3d` | Trânsito em mapa 3D real, no Blender. |
| **Edição** | `edit-labs-ai` | Cortes de podcast, motion Vox, colagem em camadas, documentário de arquivo, decupagem. Exige o Higgsfield conectado. |

Cada estilo mora no repositório dele, com versão, licença e regras próprias. Os estilos Espaço e Atleta têm licença própria: uso livre, com a marca d'água fraca do canal em todo vídeo publicado.

## Quem já instalou um estilo direto

Quem instalou, por exemplo, `espaco-em-codigo@espaco-em-codigo` passa a ter o mesmo estilo duas vezes depois de entrar na labs3d (`espaco-em-codigo@labs3d`). Remova o antigo: `claude plugin uninstall espaco-em-codigo@espaco-em-codigo`.

## Para acrescentar um estilo

Um estilo novo é um plugin num repositório próprio. Acrescente uma entrada em `.claude-plugin/marketplace.json` e uma linha na tabela de `plugins/labs3d/skills/menu/SKILL.md`. O formato do endereço importa:

- plugin na **raiz** do repositório: `{ "source": "url", "url": "https://github.com/paullabs/NOME.git" }`;
- plugin numa **subpasta**: `{ "source": "git-subdir", "url": "https://github.com/paullabs/NOME.git", "path": "pasta/do/plugin" }`.

Não use `{ "source": "github", ... }`: o Codex não o reconhece, e para plugin em subpasta o Claude instala **sem erro e sem nenhuma skill**. Depois, acrescente o estilo em `dependencies` do `plugins/labs3d/.claude-plugin/plugin.json`.
