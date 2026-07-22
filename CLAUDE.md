# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Estado atual do projeto

Site estático de página única, **HTML + CSS puro, sem build e sem JavaScript**:

- `index.html` — a página inteira
- `css/style.css` — folha de estilo única
- `Esse site dever ser elaborado como.txt` — briefing do cliente (fonte de verdade do conteúdo)

Não há package manager, bundler, lint nem testes — e não deve haver, a menos que o usuário peça.
Para ver o resultado, basta abrir `index.html` no navegador. Deploy é upload dos arquivos.

### Versionamento

O projeto é versionado em https://github.com/ricardociarlini/SGN.git (branch `main`).
O usuário quer que **toda alteração concluída seja enviada para lá** — ao terminar uma mudança,
faça commit e `git push` sem precisar perguntar. Commits em português, no imperativo.

O `user.email` está definido **localmente** neste repo como o pessoal
(`ricardociarlinitrabalho@gmail.com`), para não vazar o e-mail corporativo do `--global`.
Não remova essa configuração local.

**O repositório é público** — foi preciso para o GitHub Pages funcionar no plano free.
Nunca comite credencial, chave ou dado pessoal de terceiro aqui.

### Deploy

O site é publicado pelo **GitHub Pages** a partir da raiz da `main`, em
https://ricardociarlini.github.io/SGN/ — ou seja, **`git push` é o deploy**. Não há etapa de build.
O `.nojekyll` desliga o processamento do Jekyll; mantenha o arquivo.
Todos os caminhos no HTML são relativos (`css/…`, `img/…`) porque o site é servido em um
subdiretório (`/SGN/`) — nunca use caminho absoluto começando com `/`.

### Convenções do código

- Mobile-first: o CSS base é o layout de celular; os breakpoints (560 / 720 / 900 px) ficam
  agrupados no fim de `style.css`, não espalhados pelo arquivo.
- Todas as cores, fontes e medidas globais são custom properties no `:root`. Mude lá, não no ponto de uso.
- Direção visual **"sala de cor"**: preto neutro (`#08090a`), quase monocromático, cantos praticamente
  retos (`--radius: 2px`) e hierarquia feita por escala, peso e fio de 1px — não por cor nem sombra.
  O âmbar `--accent` é deliberadamente **raro**: só índices, ações e marcadores. Não espalhe.
- Três famílias, cada uma com um papel fixo: `--display` (Archivo) em títulos e números,
  `--sans` (Inter) no corpo, `--mono` (IBM Plex Mono) em **todo metadado** — etiquetas `.tag`,
  navegação, botões, legendas, `.reel-meta`, rodapé. Esse mono em caixa alta é o que dá o ar
  de timecode/EDL; não troque por sans "para ficar mais limpo".
- `.framed` desenha as quatro marcas de canto (mesma linguagem do símbolo da marca) com oito
  gradientes num único `::after`, sem markup extra. Use a classe em qualquer moldura de imagem
  ou vídeo. Em `.about-photo` o `::after` é limitado à razão 3/2 para não cercar a legenda.
- A régua do hero (`.timeline`) é um elemento próprio: ticks por `repeating-linear-gradient` e um
  marcador quadrado por item. Só entram ali marcos **factuais do briefing** — nada de números novos.
- A marca é vetorial: `img/logo-sgn.svg` (horizontal, fundo escuro), `img/logo-sgn-fundo-claro.svg`,
  `img/logo-sgn-perfil.svg` e `img/favicon.svg` (só o símbolo). O símbolo são as quatro marcas de
  enquadramento + o cabeçote de reprodução (playhead) em âmbar. No site ele é SVG **inline** no header
  e no rodapé (`.logo-mark`) para herdar `currentColor` e o `--accent` — se mudar o desenho, mude nos
  dois lugares e nos quatro arquivos SVG.
- Os PNGs (`logo-sgn-perfil-1000.png`, `logo-sgn-perfil-500.png`, `logo-sgn-simbolo-512.png`,
  `favicon-32.png`, `favicon-180.png`) foram rasterizados dessa mesma geometria — se o desenho mudar,
  precisam ser regerados. O `logo-sgn-simbolo-512.png` tem fundo transparente; os demais, fundo sólido.
  Para regerar: Chrome headless (`--headless=new --screenshot --window-size=…`) sobre um HTML que
  embuta o SVG em `width:100vw;height:100vh`. Renderize sempre **grande** (720px+) e reamostre para os
  tamanhos pequenos — janelas menores que ~500px renderizam cortado no headless.
- As seções de reels usam um carrossel **só de CSS** (`.reel-rail`, flex + `scroll-snap-type: x mandatory`),
  sem JavaScript e sem setas. Os cards têm a mesma largura nas duas seções — mude em `.reel`, não por seção.
- A foto da seção Apresentação é `.about-photo` (razão 3/2, `object-fit: cover`). O arquivo é
  `img/Sergio_ilha_edicao_202607221205.jpeg`, foto real do Sérgio na ilha de edição.
- Os reels são `<iframe loading="lazy">` dentro de `.reel-frame` (razão fixa 9/16):
  Facebook via `facebook.com/plugins/video.php?href=<url-encoded>`, Instagram via `/reel/<id>/embed`.
  Ambos funcionam sem SDK — não adicione os scripts de embed das plataformas.
- Fontes vêm do Google Fonts (Archivo + Inter + IBM Plex Mono), com fallback de sistema já declarado.
- `prefers-reduced-motion` e foco visível já estão tratados; preserve-os ao mexer em animação.

## Conteúdo do site

Página única para **SGN - Produção e edição de mídias audiovisuais** (Sérgio Goulart),
com as seções definidas pelo briefing, nesta ordem:

1. **Apresentação** — biografia do Sérgio Goulart (30+ anos, TV Manchete → Rede Globo; jornalismo,
   entretenimento, documentários; coberturas de Copas do Mundo e Olimpíadas in loco).
2. **Indicação e reconhecimento** — 2 reels do Facebook (depoimentos/reconhecimento).
3. **Cursos** — cursos **online** de edição de imagens ministrados pelo Sérgio e reconhecimento
   de colegas, com CTA para WhatsApp/e-mail (não há página de inscrição nem preço divulgado),
   com o vídeo `instagram.com/tv/Ca3H_cWFPBk/` (pedido do usuário, não está no briefing original).
4. **Trabalhos realizados** — 2 reels do Instagram + 2 reels do Facebook (portfólio).
5. **Contatos** — WhatsApp (21) 98577-2401 e sgn.producoes@gmail.com.

"Rio de Janeiro · atendimento em qualquer lugar" (hero, contato e meta description) **não** está no
briefing, mas foi confirmado pelo usuário em 20/07/2026: o Sérgio é do Rio. É informação válida —
não remova por ausência no briefing.

As URLs exatas dos reels estão no arquivo de briefing — sempre copie de lá, nunca de memória.
Os fundos das seções alternam `--bg` / `--bg-alt`: ao inserir uma seção nova, mantenha a alternância.

## Restrições vindas do briefing

- **Nunca inventar informações fictícias.** Sem depoimentos, clientes, números, prêmios ou datas
  que não estejam no briefing. Se faltar conteúdo, pergunte ao usuário em vez de preencher.
- **Tom sóbrio e profissional**, voltado a edição de imagem/áudio e drones — não é um site divertido
  ou colorido; o apelo visual vem de tipografia, ritmo e uso de imagem/vídeo, não de excesso de cor.
- **Responsivo de verdade** em smartphones, tablets e desktops — requisito explícito do cliente.
- Hashtags e emojis do briefing são material de rede social, **não** conteúdo literal para o site;
  use-os apenas como sinal de tom/palavras-chave.

## Idioma

Todo o conteúdo visível ao usuário final é em **português do Brasil**, com acentuação correta.
