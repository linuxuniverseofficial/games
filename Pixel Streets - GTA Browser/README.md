# Pixel Streets

Jogo de mundo aberto para navegador, inspirado no GTA 1: personagem em pixel art 2D andando por uma cidade 3D gerada proceduralmente, com carros 3D, física de pneus, polícia, armas, rádio, ciclo de dia e noite e chuva.

Tudo em **um único arquivo HTML** (HTML + CSS + JavaScript + WebGL via Three.js). Não precisa de servidor de aplicação, banco de dados nem build.

---

Inspired by:
https://uniday.studio/games/247-clt-early-access?cur=brl&lang=pt-BR

Using GTA-inspired engine:
https://patkerr.co.uk/2d-vehicles/

And with lots of vibe coding, this is the first low poly GTA for browser.
The concept is simple: Be simple but complete and funny.

Enjoy!

### How to install

Download `index.html` and run with any modern browser.
Everything is inside the html and the game uses only .js and .css code within.

Made by Claude Opus 5.5

---

## Como rodar

1. Coloque o `index.html` em qualquer servidor web estático (nginx, Apache, Caddy, GitHub Pages…) ou abra direto no navegador.
2. (Opcional) Crie uma pasta `radios/` ao lado do HTML com suas músicas.
3. Abra no navegador, escolha as opções no menu e clique em **GERAR CIDADE E JOGAR**.

> Equalizador do rádio e som 3D funcionam quando o jogo é servido por http(s). Abrindo o arquivo direto do disco (`file://`), o rádio toca sem esses efeitos.

---

## Controles

| Tecla | Ação |
|---|---|
| **W A S D** / setas | Andar / dirigir |
| **Shift** | Correr (a pé) · Nitro (no superesportivo) |
| **F** | Entrar / sair / roubar veículo |
| **Espaço** | Freio de mão (drift) |
| **Clique** ou **E** | Atirar (com a pistola) |
| **Mouse** | Olhar (visão 3D, clique para travar o cursor) |
| **V** | Alternar 1ª / 3ª pessoa (visão 3D) |
| **G** | Ligar / desligar faróis |
| **Q** / roda do mouse | Próxima música |
| **R** | Ligar / desligar o rádio |
| **H** | Buzina |
| **M** | Som liga/desliga |
| **TAB** ou clique no minimapa | Mapa em tela cheia |
| **Clique direito** no mapa | Marcar / desmarcar destino (GPS) |
| **ESC** | Menu |

---

## Menu

- **Estilo da cidade:** Modern ou Synthwave
- **Tamanho:** 14×14, 24×24 ou 34×34 quarteirões
- **Seed:** número que define a cidade (mesma seed = mesma cidade); botão para sortear
- **Hora inicial:** 00:00 a 23:00
- **Visão:** 3D (1ª/3ª pessoa, padrão) ou Top-down
- **Trânsito:** 0% a 100%
- **Pedestres:** densidade ajustável
- **Opções:** Sombras · Bloom · Som · Chuva
- **Rádio:** adicionar MP3 do computador, testar rádio, "Só minhas músicas"
- **CONTINUAR:** aplica trânsito, pedestres, chuva e visão sem gerar cidade nova. Se o estilo foi trocado, gera uma cidade nova automaticamente.

---

## A cidade

### Geração procedural
- Cidade inteira gerada em tempo real a partir da seed.
- **Streaming por blocos:** só a área perto do jogador é montada; o resto é descartado. Uma 34×34 pesa o mesmo que uma 14×14.
- **Quarteirões variados:** comuns, longos (2 ou 3 quadras) e em formato de **L**.
- **Tipos de quarteirão:** prédios, parques, estacionamentos e casas térreas (só Modern, mais comuns longe do centro).
- **Prédios:** alturas maiores no centro, com recuo de andares, parapeitos, caixas d'água, ar-condicionado no telhado, toldos e janelas que acendem à noite.
- **Becos** entre prédios, com caçambas e lixo.
- **Casas térreas:** telhado de duas águas, porta, janelas, quintal, caminho, cerca, árvore, alguns **varais com roupa** e **lixeiras na calçada**.
- **Garagens raras** com um **superesportivo exclusivo**.

### Ruas
- **Avenidas** (4 faixas, faixa dupla amarela).
- **Ruas de mão dupla** (2 faixas, faixa amarela simples, calçadas largas).
- **Ruas de mão única** (2 faixas no mesmo sentido, faixa branca tracejada e setas; sentido alternado entre ruas vizinhas, como em Nova York).
- Faixas de pedestre, postes de luz ligados por **cabos elétricos**, árvores e **semáforos** nos cruzamentos.

### Litoral
- Um dos 4 lados do mapa vira **praia**: calçadão com postes, mureta, gramado com palmeiras, areia com guarda-sóis, toalhas e banhistas, espuma e mar.
- Os banhistas **vão embora quando chove** e **voltam depois** que a chuva passa.
- **Cair na água mata** (a pé ou de carro: o veículo afunda).

### Estilos
- **Modern:** concreto, táxis amarelos, árvores.
- **Synthwave:** prédios pastel, palmeiras, paleta Miami anos 80, sol retrô listrado. O neon (letreiros, faixas art déco, contornos) aparece **só em algumas avenidas** sorteadas pela seed.

---

## Dia, noite e clima

- **Relógio na tela** · 1 segundo = 1 minuto de jogo (24 min por ciclo).
- Sol nasce no **leste** e se põe no **oeste**; sombras e cores do céu mudam ao longo do dia.
- À noite: estrelas, lua, janelas, postes e faróis **acendendo aos poucos**, bloom.
- Sem chuva o céu fica **limpo e azul** (com névoa no horizonte); as nuvens só existem onde há chuva.

### Chuva regional (opção "Chuva" no menu)
A chuva não cobre a cidade inteira de uma vez: ela vem em **células de chuva** que nascem, crescem, andam com o vento e se dissipam.

- **Ao ativar:** sempre nasce uma célula média **contra o vento**, perto de você, que chega até você empurrada pelo vento. Ela se forma aos poucos (~20–35 s até a força máxima) e dura de 1,5 a 3 minutos.
- **Depois de 1 minuto:** entra o sorteio. A cada 35–110 s há uma chance (sorteada entre **15% e 40%** por partida) de surgir uma nova célula, perto de você ou em qualquer lugar do mapa. No máximo 4 células ativas.
- **Frentes grandes (16% das células):** chuva que cobre o **mapa inteiro**, mais forte, e que ao terminar se **quebra em bolsões** menores espalhados.
- **Tempestade (frente grande):**
  - chuva mais pesada;
  - árvores e palmeiras **balançam com o vento**;
  - **todos os semáforos piscam amarelo** (só visual: os carros continuam respeitando a sinalização normal).
- **No céu:** a nuvem de cada célula aparece **cerca de 3x maior** que a área onde realmente chove, então dá para vê-la chegando de longe. Embaixo da chuva o céu fecha e escurece.
- **Desmarcar "Chuva"** faz as células se dissiparem aos poucos, sem corte brusco.

### Efeitos da chuva
- Gotas quase invisíveis no escuro que **brilham com a cor das luzes próximas** (postes, faróis, semáforos, giroflex). No Synthwave a chuva é mais escura e o brilho perto das luzes é mais forte.
- Asfalto molhado mais brilhante, neblina mais fechada e **som de chuva** que aumenta conforme a intensidade no lugar onde você está.
- **Pista molhada:** seu carro perde aderência (derrapa mais e freia pior) enquanto estiver dentro da chuva.
- Pedestres **abrem guarda-chuva** ou **saem correndo**.
- **Banhistas** recolhem as coisas e saem da praia quando chove, e **voltam** quando a chuva passa.
- **Minimapa e mapa grande** mostram as células de chuva com o tamanho real da área molhada e uma **seta azul** indicando para onde cada uma está indo.

---

## Veículos

- Modelos 3D procedurais com carroceria arredondada: **sedã, táxi, esportivo, van, picape, caminhão, ônibus, viatura e superesportivo**.
- **Física 2D de corpo rígido com 4 pneus** (inspirada no protótipo de Pat Kerr que deu origem ao GTA): aderência lateral, derrapagem, freio de mão, marcas de pneu, fumaça, inclinação da carroceria.
- **Dano:** batidas fortes acumulam dano → o carro **pega fogo e explode**, empurrando e danificando o que estiver por perto (pode causar reação em cadeia).
- **Superesportivo:** chamas azuis no escapamento e **nitro** com Shift.
- **Faróis** com luz real no seu carro (automáticos à noite, G liga/desliga).
- Cerca de 10% dos carros com **neon embaixo**.
- Motor com som diferente por tipo (caminhão e ônibus mais graves).

### Trânsito
- Trânsito ajustável de vazio a **ruas lotadas** (centenas de carros, desenhados com instancing na GPU).
- Física completa perto do jogador; carros distantes andam "em trilho", com custo quase zero.
- **Semáforos** com verde/amarelo/vermelho; carros param, formam fila e respeitam mão única.
- Motoristas **buzinam** quando travados e, depois de 10–15 s, **dão ré e desviam**.
- Veículos que ficam encaixados um no outro **explodem**.

### Objetos destrutíveis
- **Postes de luz** (o cabo elétrico cai junto, com faíscas)
- **Árvores e palmeiras**
- **Semáforos:** derrubar um deixa o cruzamento **em pane**: os outros piscam amarelo e todos avançam achando que têm a preferência
- **Lixeiras** (saem voando e espalham lixo)

---

## Personagem e pedestres

- Personagem e pedestres em **pixel art 16×24** gerados por código, com animação em 4 direções.
- Pedestres andam pelas calçadas (inclusive nas calçadas largas das ruas estreitas), fogem e são atropelados.
- Atropelados soltam um **"ai"** e **somem aos poucos**.
- Você só cai se for atingido **pela frente** de um carro; batidas de lado só empurram.

---

## Polícia

- Viaturas patrulham com **giroflex sempre aceso** (sirene só na perseguição).
- Quantidade conforme o trânsito: 1 (até 50%), 2 (até 90%), 3 (acima).
- Fica **procurado** se:
  - uma viatura te vê batendo num carro (raio de ~3 carros),
  - você bate numa viatura ou atira perto/na polícia,
  - você mata **10 pedestres**.
- **Perseguição:** viaturas calculam rota pelas ruas, derrapam, dão ré quando presas e chamam reforço.
- **A pé:** policiais **descem do carro e atiram**.
- **Fim da perseguição:**
  - fugir **de carro** e ficar a mais de 110 m por **1 minuto**,
  - destruir **3 viaturas**,
  - matar **15 policiais** (matar o 16º faz ela voltar).
- **Preso** se ficar parado encurralado.
- Indicador de **PROCURADO** com estrela amarela piscando.

---

## Armas e coletáveis

- **Pistola:** encontrada em becos (ponto verde no mapa), com 0 a 100 balas.
  - Top-down: mira no cursor · 3D: mira no centro da tela.
  - **Drive-by:** atira de dentro do carro em qualquer direção.
  - Tiros danificam veículos, matam pedestres e policiais.
- **Vida:** cruz vermelha nas calçadas, recupera 50 HP.

---

## Mapa e navegação

- **Minimapa** com norte para cima (o sol nasce no leste/direita), prédios, becos, armas (verde), vida (vermelho), polícia e células de chuva.
- **Mapa em tela cheia** (TAB ou clique no minimapa) com legenda e indicação da **PRAIA**.
  - **Não pausa o jogo:** o trânsito, os pedestres e a chuva continuam se movendo no mapa.
  - Mostra a direção de cada célula de chuva com setas azuis.
- **Clique direito** marca um destino: **GPS** traça a rota pelas ruas, seta na borda do minimapa e feixe de luz amarelo no mundo.

---

## Câmeras

- **Top-down** com zoom pela velocidade (estilo GTA 1).
- **3ª pessoa** atrás do personagem e **câmera de perseguição** no carro.
- **1ª pessoa** a pé e **cockpit** no carro.
- Olhar livre com o mouse (volta para a frente sozinha ~2 s depois de parar de mexer).

---

## Rádio

- Lê automaticamente qualquer `.mp3`, `.ogg`, `.m4a`, `.wav`, `.opus` ou `.flac` na pasta `radios/` ou ao lado do jogo (se o servidor listar diretórios).
- Sem listagem de diretório: use `radios/lista.txt` (um arquivo por linha) ou nomeie como `musica1.mp3`, `musica2.mp3`…
- Ordem **embaralhada pela seed**, toca em sequência; trocar de carro passa para a próxima música.
- Equalizador e compressor para um som mais encorpado.
- **Som espacial:** a pé, alguns carros passam tocando músicas da sua lista.
- Adicione músicas do seu computador pelo menu; "Só minhas músicas" ignora as do servidor.

---

## Tecnologia

- **Three.js r128** (WebGL), carregado de CDN
- Web Audio API (motor, sirene, rádio com EQ, som 3D, chuva, efeitos)
- Canvas 2D para sprites, texturas e mapas
- Sem dependências de backend
