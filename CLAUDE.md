# Bao Chinês — app de treino de mandarim

App web pessoal do Vinícius para estudar chinês (mandarim), feito em parceria com o Claude.
Ele é iniciante em chinês e também está começando com Git/GitHub (estuda ADS), então
**explique tudo em português, de forma simples, passo a passo**, e diga o que cada comando faz.

## Onde está publicado

- Repositório: `costardiv1/treino-chines` (branch `main`, raiz do repo)
- Site (GitHub Pages): https://costardiv1.github.io/treino-chines/
- O Vinícius usa o **GitHub Desktop** no Windows. Ao terminar uma mudança, ofereça fazer o
  commit e o push, com mensagem de commit em português.
- O Pages leva ~1 minuto para atualizar; se aparecer a versão antiga, Ctrl + F5.

## Estrutura

Tudo fica num único arquivo: **`index.html`** (HTML + CSS + JS, sem build, sem dependências).
Mantenha assim, a menos que ele peça para separar. Só usa Google Fonts (Nunito e Noto Sans SC).

Dentro do `<script>`:

- `UNIDADES` — vocabulário por unidade (Saudações, Apresentação, Números, Pessoas, Comida).
  Cada item: `{ h: hanzi, p: pinyin com tons, pt: português, alt?: [hanzi aceitos na fala] }`.
- `HISTORIAS` — histórias para leitura. Cada frase tem `pt` (tradução) e `t` (tokens):
  `[hanzi, pinyin, significado]` por palavra; string solta = pontuação.
  Cada história tem `contexto`, `moral` e `perguntas` (a primeira opção em `ops` é a correta;
  as opções são embaralhadas na hora).
- `state` — salvo no `localStorage` com a chave `baoChines` (xp, streak, ultimoDia, licoes,
  historias, mic). **Não mude a chave nem renomeie campos**, senão ele perde o progresso.
- Telas: `home`, `licao`, `fim`, `historia` (trocadas com `mostrarTela`).
- Tipos de exercício na lição: `escolha` (hanzi → pt), `reverso` (pt → hanzi), `ouvir`
  (áudio → hanzi), `pares` (jogo de ligar), `falar` (reconhecimento de voz), `pergunta`
  (desafio das histórias). Exercício errado volta para o fim da fila.

## Voz

- Fala: `speechSynthesis` com voz `zh-CN`.
- Reconhecimento: Web Speech API (`webkitSpeechRecognition`, `zh-CN`) — só funciona bem no
  **Google Chrome** e precisa de https (no GitHub Pages a permissão do microfone fica salva;
  abrindo o arquivo local ela é pedida toda vez).
- A comparação da fala é por semelhança de caracteres (LCS), aprovado com ≥ 75%. Ela não
  avalia tons individualmente; deixe isso claro se ele perguntar.

## Visual

- Tema **claro** apenas: fundo em degradê verde menta pastel (`--bg`) → rosa pastel (`--bg2`),
  rosa coral como cor principal (`--primary`), verde-água nos botões de áudio (`--blue`),
  lavanda na seleção (`--sel`). Ele pediu cores pastel claras; mantenha essa linha.
- Estilo "gamificado" com botões com sombra embaixo, mascote panda 🐼 chamado Bao.
  Inspirado em apps de idioma, mas **sem copiar** marca, mascote ou cores do Duolingo.
- No jogo de pares, todos os botões têm altura fixa (72px) para as colunas ficarem alinhadas.
- Precisa funcionar bem no celular (largura ~400px).

## Ao mudar o app

1. Teste no navegador antes de entregar (abrir a home, fazer uma lição, abrir a história).
2. Confira se não há erro no console.
3. Pinyin sempre com marcas de tom (nǐ hǎo, não ni3 hao3). Revise hanzi e traduções com cuidado.

## Ideias combinadas para o futuro

- Mais histórias da China, curtas e em chinês simples: 井底之蛙 (o sapo no fundo do poço),
  塞翁失马 (o cavalo do velho da fronteira), 画蛇添足, etc.
- Mais unidades de vocabulário.
