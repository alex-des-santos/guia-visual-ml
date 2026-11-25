# O que é Machine Learning? – vídeos + site

Material da oficina extensionista (público leigo). Duas partes:

- `videos/` – projeto HyperFrames com 8 vídeos (abertura + 7 algoritmos), 1920×1080, 30 fps, sem som (a narração é ao vivo, na palestra).
- `site/` – site estático com os vídeos embutidos, pronto para GitHub Pages (sem backend).

Precisa de Node.js 22+ e FFmpeg no PATH. O CLI fica fixo em `hyperframes@0.9.19` (`videos/package.json`).

## Os vídeos

Todos os 8 vídeos estão numa única composição (`videos/index.html`), um depois do outro. Cada cena fica em `videos/compositions/`:

| Vídeo | Arquivo da cena | Trecho na sequência | MP4 |
| --- | --- | --- | --- |
| Abertura: O que é ML? | `abertura.html` | 0–19 s | `00-abertura.mp4` |
| Regressão Linear | `linear.html` | 19–42 s | `01-regressao-linear.mp4` |
| Regressão Logística | `logistic.html` | 42–65 s | `02-regressao-logistica.mp4` |
| Árvore de Decisão | `tree.html` | 65–88 s | `03-arvore-de-decisao.mp4` |
| K-Means | `kmeans.html` | 88–112 s | `04-k-means.mp4` |
| Rede Neural | `neural.html` | 112–136 s | `05-rede-neural.mp4` |
| Random Forest | `forest.html` | 136–160 s | `06-random-forest.mp4` |
| Gradient Boosting | `boosting.html` | 160–184 s | `07-gradient-boosting.mp4` |

### Preview (o comando fica rodando até você parar)

```powershell
cd videos
npm run dev                                # abre o Studio no navegador (Ctrl+C para parar)
# ou, em segundo plano:
npx --yes hyperframes@0.9.19 preview --background
npx --yes hyperframes@0.9.19 preview --stop
```

### Renderizar de novo

Depois de editar, rode a verificação e renderize só o trecho do vídeo que mudou (valores da tabela acima):

```powershell
cd videos
npm run check
npx --yes hyperframes@0.9.19 render --start 19 --end 42 --quality looks -o renders/01-regressao-linear.mp4
```

Para renderizar os 8 de uma vez (PowerShell):

```powershell
cd videos
$v = @(@('00-abertura',0,19),@('01-regressao-linear',19,42),@('02-regressao-logistica',42,65),@('03-arvore-de-decisao',65,88),@('04-k-means',88,112),@('05-rede-neural',112,136),@('06-random-forest',136,160),@('07-gradient-boosting',160,184))
foreach ($x in $v) { npx --yes hyperframes@0.9.19 render --start $x[1] --end $x[2] --quality looks -o "renders/$($x[0]).mp4" }
Copy-Item renders\*.mp4 ..\site\videos\
```

Se mudar a duração de uma cena, ajuste `data-start`/`data-duration` em `videos/index.html` e os trechos acima. As imagens de capa do site (`site/videos/*.jpg`) saem de um quadro do vídeo:

```powershell
ffmpeg -y -ss 17.5 -i renders/01-regressao-linear.mp4 -frames:v 1 -vf scale=960:-1 -q:v 4 ..\site\videos\01-regressao-linear.jpg
```

## O site

Abrir localmente (o vídeo e os links funcionam melhor por um servidor do que abrindo o arquivo direto):

```powershell
cd site
python -m http.server 8000
# abra http://localhost:8000
```

Também dá para abrir `site/index.html` com dois cliques; só os gráficos interativos precisam de internet (Chart.js vem de CDN).

### Publicar no GitHub Pages

Opção A – repositório só com o site (mais simples):

1. Crie um repositório no GitHub (ex.: `ml-extensao`).
2. Copie o conteúdo de `site/` para a raiz do repositório e faça commit/push.
3. No GitHub: **Settings → Pages → Build and deployment → Deploy from a branch**, branch `main`, pasta `/ (root)`.
4. O endereço fica `https://<seu-usuario>.github.io/ml-extensao/`. Use esse link para gerar o QR code.

Opção B – repositório com a pasta inteira (`videos/` + `site/`): o workflow `.github/workflows/pages.yml` já publica a pasta `site/`. No GitHub, em **Settings → Pages**, escolha **Source: GitHub Actions** e faça push na branch `main`.

O arquivo `site/.nojekyll` evita que o GitHub processe o site com Jekyll.

## Contador de visitas (GoatCounter)

O site conta visitas com o [GoatCounter](https://www.goatcounter.com): gratuito para uso não comercial e sem cookies. Enquanto o código não for trocado, o contador não carrega, e o site funciona igual se o contador falhar.

1. Crie uma conta gratuita em https://www.goatcounter.com/signup. O "código" que você escolher vira o endereço do painel: `https://<código>.goatcounter.com`.
2. Em `site/index.html`, no fim do arquivo, troque `SEU-CODIGO` pelo seu código no atributo `data-goatcounter` (é o único lugar): `data-goatcounter="https://<código>.goatcounter.com/count"`.
3. Publique o site de novo (commit/push). Visitas feitas em `localhost` não são contadas.
4. Para o relatório, entre em `https://<código>.goatcounter.com`: o painel mostra visitantes e visualizações por período. Escolha as datas da atividade e use o número de visitantes como "pessoas impactadas" (é uma estimativa: a mesma pessoa em outro aparelho conta duas vezes).
