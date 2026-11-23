# Linguagem simples para resumos de proposições legislativas (skills)

Dois conjuntos de instruções para assistentes de inteligência artificial (skills). Eles orientam a IA a escrever e a revisar, em linguagem simples, o resumo de uma proposição legislativa, no formato usado pelo Senado Explica: "1. O que é:" e "2. O que diz o autor:".

DOI da versão 1.0.0: [10.5281/zenodo.24476816](https://doi.org/10.5281/zenodo.24476816)

DOI de todas as versões (aponta sempre para a mais recente): [10.5281/zenodo.24476815](https://doi.org/10.5281/zenodo.24476815)

## O que é

Uma skill é uma pasta com um arquivo de instruções (`SKILL.md`) e arquivos de apoio. O assistente de IA lê essas instruções quando o pedido trata do assunto da skill. Não é um programa: não tem código, não acessa sistemas do Senado e não publica nada.

Este repositório traz duas skills:

| Pasta | Para que serve |
|---|---|
| `linguagem-simples-senado-explica/` | Qualquer tipo de proposição: projeto de lei, projeto de lei complementar, proposta de emenda à Constituição, medida provisória, projeto de decreto legislativo e projeto de lei do Congresso Nacional |
| `linguagem-simples-senado-explica-pl/` | Só projetos de lei ordinária, com regras e exemplos próprios desse tipo |

As skills foram feitas como sugestão de um artigo da pós-graduação em Comunicação Legislativa do Instituto Legislativo Brasileiro (ILB), do Senado Federal. Elas não são produto oficial do Senado e não estão em uso no Senado Explica.

## Como funciona

Você entrega ao assistente o texto da proposição e a justificação do autor. A skill manda a IA seguir esta ordem:

1. Pensar no leitor: alguém que não conhece o processo legislativo nem o vocabulário jurídico.
2. Manter a fidelidade ao texto: usar só o que está na proposição e na justificação, sem acrescentar fatos, números ou efeitos, e sem trocar "autoriza" por "cria".
3. Escrever no formato fixo: "1. O que é:" (o que muda e para quem) e "2. O que diz o autor:" (as consequências que o autor prevê, atribuídas a ele).
4. Aplicar as regras de palavras e de frases: palavras comuns, termos técnicos explicados, frases de até 25 palavras, ordem direta, voz ativa.
5. Conferir o rascunho com uma lista de verificação antes de entregar.

Há três modos de uso:

- Gerar: você envia o texto e recebe só o resumo.
- Gerar com relatório: você escreve "com relatório" e recebe, depois do resumo, uma lista para a revisão humana, com cada número e cada consequência ao lado do trecho do original que os sustenta.
- Revisar: você envia um resumo pronto e recebe a versão corrigida, com o motivo de cada mudança.

O resultado é sempre um rascunho. Uma pessoa precisa conferir o resumo contra o texto da proposição antes de qualquer publicação.

## O que há em cada pasta

| Arquivo | Conteúdo |
|---|---|
| `SKILL.md` | As instruções completas: leitor, fidelidade, formato, regras, verificação e exemplos |
| `prompt-portatil.md` (ou `prompt-portatil-pl.md`) | As mesmas regras em um texto único, para colar em assistentes que não aceitam skills |
| `references/glossario.md` | Explicações padronizadas de termos legislativos |
| `references/avaliacao.md` | Como revisar os resumos e testá-los com o público |
| `references/fundamentacao.md` | A fonte de cada regra |

A pasta `para-instalar/` traz cada skill em um arquivo `.zip`, pronto para envio.

## Como instalar

### No Claude (aplicativo ou site)

1. Baixe o arquivo `.zip` da skill que você quer, na pasta `para-instalar/`.
2. No Claude, abra as configurações e procure a área de skills (em "Capacidades" ou "Personalizar", conforme a versão).
3. Envie o arquivo `.zip` e deixe a skill ativada.
4. Em uma conversa nova, peça o resumo. Exemplo: "Resuma este projeto de lei em linguagem simples, com relatório", seguido do texto do projeto e da justificação.

### No Claude Code

Copie a pasta da skill para a pasta de skills do seu usuário:

```bash
cp -R linguagem-simples-senado-explica ~/.claude/skills/
```

Para usar só em um projeto, copie para `.claude/skills/` dentro da pasta do projeto.

### Em outros assistentes de IA

1. Abra o arquivo `prompt-portatil.md` (ou `prompt-portatil-pl.md`).
2. Copie o texto inteiro e cole no campo de instruções do assistente ou no início da conversa.
3. Envie o texto da proposição com a justificação.

As pastas seguem o formato aberto de skills (uma pasta com `SKILL.md`). Ferramentas que aceitam esse formato podem receber o `.zip`.

### Onde foi testado

| Ferramenta | O que foi testado | Resultado |
|---|---|---|
| Claude | As duas skills, instaladas pelo arquivo `.zip` | Instaladas e acionadas pelo autor |
| ChatGPT | O prompt portátil de projetos de lei, com o PL 3330/2025, em 23/11/2026 | Resumo no formato pedido e, com o pedido "com relatório", o relatório depois do resumo |
| Gemini | O mesmo teste, em 23/11/2026 | O mesmo resultado |

Os testes mostram que as instruções funcionam nessas ferramentas. Eles não medem a qualidade dos resumos. O prompt portátil da versão geral não foi testado no ChatGPT nem no Gemini.

## Fontes das regras

- ABNT NBR ISO 24495-1:2024, Linguagem simples, parte 1: princípios e diretrizes norteadores.
- ABNT NBR ISO 24495-2:2026, Linguagem simples, parte 2: comunicação jurídica.
- Lei nº 15.263, de 14 de novembro de 2025, que institui a Política Nacional de Linguagem Simples (art. 5º).
- ROEDEL, Patricia. Manual de linguagem simples: como planejar, desenvolver e testar textos que funcionam. Brasília: Câmara dos Deputados, Edições Câmara, 2024.

As fontes foram consultadas e estão citadas regra a regra em `references/fundamentacao.md`. Os textos delas não são reproduzidos aqui. As normas devem ser obtidas na ABNT.

O prompt usado pela área de tecnologia do Senado (Prodasen) no Senado Explica foi o ponto de partida da proposta. Ele não é reproduzido neste repositório.

## Limites

- A skill não substitui a revisão humana nem o teste com o público previsto na Lei nº 15.263/2025 (art. 5º, XVIII).
- A IA pode errar mesmo seguindo as instruções. O modo "com relatório" ajuda a conferir, mas não decide se o resumo está certo.
- Os glossários são uma proposta inicial e não foram validados por equipe do Senado.
- Os limites numéricos (25 palavras por frase, de 1 a 3 frases no item 1, de 2 a 5 itens no item 2) são referências de trabalho.
- As skills não foram testadas com leitores.
- No ChatGPT e no Gemini, o teste foi um só, com um projeto de lei. O resultado pode mudar conforme o modelo e a versão de cada ferramenta.

## Autoria e uso de IA

Autor: Marcello Fernandes de Souza.

O texto das instruções foi redigido por IA generativa (Claude, da Anthropic), a pedido do autor. A comparação com as fontes e a conferência dos exemplos contra os projetos de lei também foram feitas com a IA. O autor leu o conteúdo e responde por ele.

## Como citar

SOUZA, Marcello Fernandes de. Linguagem simples para resumos de proposições legislativas (skills). Versão 1.0.0. [S. l.]: Zenodo, 2026. DOI: https://doi.org/10.5281/zenodo.24476816.

## Licença

Creative Commons Atribuição 4.0 Internacional (CC BY 4.0): https://creativecommons.org/licenses/by/4.0/deed.pt-br. A licença vale para o que é do autor. Não alcança as normas, a lei e o manual citados.
