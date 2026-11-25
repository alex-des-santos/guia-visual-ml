# REVIEW – vídeos "O que é Machine Learning?" (8 vídeos, 1920×1080, 30 fps, 184 s na sequência)

## Revisão de 24/11 (3ª rodada)
- **Eixos dos vídeos 01–05:** números dos eixos agora com 50 px em negrito e cor `#3a3d42` (antes 30 px em cinza claro); nomes dos eixos com 52 px (antes 36 px); rótulos "sim/não" da árvore com 48 px; nomes das camadas da rede neural com 50 px e saídas com 48 px. Mudanças de layout: no 01, "Tamanho da casa (m²)" foi para dentro do gráfico, acima do eixo; no 02, o nome do eixo foi encurtado para "Palavras suspeitas no e-mail →"; no 05, a rede foi puxada 60–120 px para a esquerda para caber "Cachorro 6%".
- **Vídeo 07:** a linha do preço real termina logo depois da coluna. O rótulo "Árvore 3" fica ao lado do pedaço verde, com uma linha-guia verde, e o rótulo "Árvore 2" desceu para abrir espaço.
- Conferido com os MP4 reduzidos a 375 px: dá para ler os números e os nomes dos eixos em todos.
- Os vídeos 00 e 06 não mudaram nesta rodada.
- `check`: 0 erros (mantidos `film_silent` e a informação de `container_overflow` do K-Means).
## Revisão de 24/11 (2ª rodada)
- **Random Forest (06):** de 5 para 3 árvores, cerca de 1,5× maiores (nós de 30 px, traço de 8 px). Votos em cartões de 300×96 px com texto de 52 px, placar em 64 px, cartão do paciente em 50–56 px, legendas em 64 px. Placar novo: gripe 2 × 1 resfriado. O laranja do "Resfriado" ficou mais escuro (`#d4570a`) para dar mais contraste com o texto branco.
- **Abertura (00):** os cartões "gato/cachorro" agora aparecem um de cada vez dentro da tela do computador, sem passar por cima das setas. A frase final virou "7 jeitos".
- **Gradient Boosting (07, novo, 24 s):** um apartamento de treino com preço real de R$ 400 mil. A árvore 1 chuta R$ 300 mil, a 2 soma R$ 70 mil, a 3 soma R$ 25 mil e o total chega a R$ 395 mil. A coluna empilhada cresce a cada árvore e a barra vermelha do erro encolhe (100 → 30 → 5 mil).
- `data-hold` na frase final do Random Forest: a pausa de 3 s no fim é de propósito.
- Celular: conferi os MP4 renderizados reduzidos para 375 px de largura. Legendas, votos, placar e rótulos do Boosting dão para ler. Os rótulos das árvores do Boosting (46 px, uns 9 px no celular) são o menor texto que ainda lê.

## Decisões (1ª rodada)
- Um projeto só: `index.html` monta as cenas em sequência e cada MP4 sai de `render --start/--end`. O CLI 0.9.19 não aceita mais de um HTML raiz (`multiple_root_compositions`).
- Visual igual em todos: fundo claro `#f6f4ef`, texto `#121417`, fonte Inter 400/700/900. Azul para o modelo, laranja para o caso novo e verde/vermelho só para sim/não.
- Um exemplo do dia a dia por vídeo, seguido do começo ao fim.
- Sem som de propósito, porque a narração é ao vivo. O aviso `film_silent` foi mantido.

## Medido x só olhado
- `check`: 0 erros. Avisos: `film_silent` (de propósito) e uma informação de `container_overflow` nos centros do K-Means (os marcadores começam fora da área do gráfico, sem efeito visível).
- `ffprobe`: 00 = 19 s, 06 = 24 s, 07 = 24 s, todos 1920×1080. Os vídeos 01–05 não mudaram.
- Não conferido: movimento quadro a quadro entre os momentos principais (`keyframes`).

## Pontos fracos que ainda restam
- No vídeo 03, os textos do cartão da Ana (36 px) e das perguntas (38 px) continuam pequenos no celular; não são eixos e ficaram fora desta rodada.
- O movimento quadro a quadro entre os momentos principais não foi conferido (`keyframes`).

