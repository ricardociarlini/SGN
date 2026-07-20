# SGN — Produção e edição de mídias audiovisuais

Site de página única de **Sérgio Goulart** — mais de 30 anos de edição de imagens,
da TV Manchete à Rede Globo, com passagem por jornalismo, entretenimento e documentários.
Produção e edição de mídias audiovisuais, captação com câmeras e drones, vídeos institucionais.

🔗 **No ar em:** https://ricardociarlini.github.io/SGN/

## Como é feito

HTML e CSS puro. **Sem build, sem bundler, sem JavaScript** — para ver o resultado, basta abrir
o `index.html` no navegador. O deploy é o próprio `git push`: o GitHub Pages serve a raiz da `main`.

```
index.html                 a página inteira
css/style.css              folha de estilo única, mobile-first
img/                       marca (SVG + PNG) e imagens
CLAUDE.md                  convenções do projeto
```

## Design

Direção **"sala de cor"**: preto neutro, quase monocromático, com a hierarquia construída por
escala, peso tipográfico e fio de 1px — não por cor ou sombra. Os metadados (etiquetas, navegação,
legendas) são monoespaçados, na leitura de timecode que o meio audiovisual usa. O âmbar é raro
por decisão: marca só índices, ações e marcadores.

A marca é um monograma de **marcas de enquadramento** com um cabeçote de reprodução ao centro —
lê como câmera e como linha do tempo. Essas mesmas marcas de canto reaparecem como moldura
ao redor de cada vídeo e da foto.

Responsivo de verdade em smartphones, tablets e desktops, com `prefers-reduced-motion` e
foco visível tratados.

## Contato

📱 WhatsApp (21) 98577-2401 · ✉️ sgn.producoes@gmail.com
