# Prompt para criar uma palestra parecida

Troque o que está entre colchetes e cole numa conversa com o Claude. Se tiver fotos e vídeos, anexe ou indique a pasta junto.

```
Quero criar uma apresentação HTML interativa, em português, para uma palestra contando a minha trajetória. Público: [ex.: calouros do curso X da universidade Y]. Ideia central da palestra: [ex.: "a universidade é a oportunidade de descobrir, testar e consolidar quem você é"].

MINHA HISTÓRIA (resumo):
- Origem: [cidade, estado, nº aproximado de habitantes, contexto da família/escola]
- Viradas de chave antes da faculdade: [...]
- Na universidade: [projetos, empresa júnior, estágio, iniciação científica, intercâmbio...]
- Carreira hoje: [onde trabalho, o que faço, números relevantes]
- Próximo passo: [...]
- Frase de fechamento: [ou peça sugestões]

FORMATO E NAVEGAÇÃO
- Uma página HTML com palco fixo de 1920×1080 que escala para caber em qualquer tela.
- Navegação: seta →/espaço/clique avançam; ← volta. F: tela cheia. N: notas do apresentador (texto em <aside> em cada slide). O: visão geral com todos os slides. E: modo edição, para editar qualquer texto clicando nele (salvo no navegador, com botão "Copiar HTML").
- Barra de progresso fina no topo e contador de slides.
- Conteúdo revelado passo a passo: cada clique mostra o próximo bloco do slide.
- Transições simples (fade). Nada de confete, tremor ou brilhos pulsando. Animações só quando mostram uma ação: números que sobem contando, linhas que se desenham, destaque que preenche uma palavra-chave.

ABERTURA COM GLOBO (o "uau")
- Capa estática com título grande, subtítulo com a tese, meu nome e minha foto num quadro vertical. Embaixo, uma linha do tempo que se desenha ligando as etapas da minha vida até "E você?".
- No slide seguinte, um globo 3D (d3.geoOrthographic em canvas) girando no espaço, com fundo de estrelas. Cada clique faz um voo suave: planeta → [país] → [estado] → [minha cidade]. A cidade aparece destacada com um pino "[Cidade] · ≈ X mil habitantes". No último clique, uma linha tracejada liga a minha cidade a [cidade da universidade] e o título da palestra aparece.
- Legendas grandes a cada etapa ("Existe um ponto no mapa…", "…no sul do Brasil,"...).
- Dados geográficos embutidos no HTML (nada buscado da internet na hora): pacote npm world-atlas (contornos do mundo), estados do Brasil e municípios do meu estado (repositório tbrugz/geodata-br no GitHub), simplificados com mapshaper.
- IMPORTANTE: corrigir o sentido dos polígonos (winding) antes de desenhar com d3. Se d3.geoArea(polígono) > 2π, inverter os anéis. Sem isso, o estado e os municípios pintam a tela inteira.
- Usar projection.precision(0) quando o zoom for alto, para não travar.

ESTRUTURA NARRATIVA
- Slide da tese logo no início, apresentando os atos.
- 4 atos com slides de abertura escuros (número grande vazado, título e uma foto grande): 1 Descobrir (antes da faculdade), 2 Testar (a universidade como laboratório), 3 Consolidar (experiência vira carreira), 4 Vocês (a mesma oportunidade para a plateia).
- "Bagagem" no rodapé: cada slide de experiência adiciona uma habilidade (ex.: Disciplina, Protagonismo, Liderança), que entra animada. O rodapé também mostra em qual ato estamos. No fim do ato 3, um slide junta toda a bagagem dividida por ato e diz quantas habilidades vieram da universidade.
- Linha do tempo interativa ("Quem sou eu?"): pontos clicáveis, com foto e descrição de cada fase, e um botão "percorrer" automático.
- Fechamento: foto de conquista em tela cheia (ex.: formatura), foto com a família ("Ninguém chega sozinho") e a frase final aparecendo linha por linha, com o globo se afastando da minha cidade até mostrar o planeta inteiro.
- Último slide: agradecimento, contatos e um QR code gerado na página (biblioteca qrcode-generator) com o link do material para os alunos.

DINÂMICAS COM A PLATEIA
- Contador de mãos levantadas (ex.: "quem é a primeira pessoa da família na universidade?"), com botões +1/+5/+10/zerar.
- "Verdade ou mito" sobre um fato curioso da minha história: placar de votos e cartão que vira para revelar a resposta.
- "Qual é o seu perfil?" com barras de votação ao vivo.
- Cronômetro (1/3/5 minutos) para a plateia escrever o próprio plano de curto, médio e longo prazo.
- Cartões de lições que viram ao clicar.

FOTOS E VÍDEOS
- Antes de montar, me liste quais fotos você precisa, com código (F1, F2...) e o slide onde cada uma entra. Deixe espaços marcados com o código até eu enviar.
- Otimize as fotos (no máximo 1600 px no maior lado, JPG qualidade 80) e os vídeos (H.264 em 720p, sem áudio, com imagem de capa). Os vídeos tocam sem som e em loop só quando o slide está ativo.
- Inclua um slide de bastidores com vídeos verticais lado a lado e um mosaico de fotos.

VISUAL
- Paleta: [ex.: azul-marinho #042c53, azul #143f69, azul-claro #9cc3e6, fundo #eef3f8, ou "use a minha identidade visual: ..."].
- Tipografia: [ex.: Inter Tight nos títulos e Inter no texto].
- Arcos grossos de quarto de anel nos cantos como assinatura gráfica. Cartões com cantos arredondados.

ENTREGA
- Publique como artifact com as mídias na pasta media/. Também salve uma cópia completa (index.html + media/) numa pasta do meu computador.
- Coloque o d3 e o qrcode como arquivos locais em media/, para a apresentação funcionar sem internet no auditório.
- Crie também um guia interativo para os alunos acessarem pelo QR code: teste de perfil, plano de curto/médio/longo prazo com botão de copiar e checklist do primeiro ano.
- Teste no navegador antes de entregar e me mostre o resultado.
```
