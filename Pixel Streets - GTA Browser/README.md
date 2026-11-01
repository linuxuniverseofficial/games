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

Os comandos seguem o padrão do **GTA V** (PC e controle).

| Tecla | Ação |
|---|---|
| **W A S D** / setas | Andar / dirigir |
| **Shift** | Correr (a pé) · Nitro (no superesportivo) |
| **F** | Entrar / sair / roubar veículo |
| **Espaço** | Pular (a pé) · Freio de mão (no carro) |
| **Clique** | Atirar (segure para rajada) · sem arma: **soco** |
| **R** | Soco (a pé) |
| **TAB** (segurar) | **Roda de armas**: o tempo desacelera e o mouse escolhe; soltar confirma. Toque rápido: próxima arma |
| **1 / 2 / 3 / 4 / 5** | Punhos / Pistola / Colt Magnum / Metralhadora / Bazuca |
| Roda do mouse (a pé) | Trocar de arma |
| **E** | Buzina (no carro) · ação a pé (comprar na loja) |
| **H** | Ligar / desligar faróis |
| **Q** (segurar, no carro) | **Roda do rádio** com todas as músicas e a opção DESLIGADO. Toque rápido: próxima |
| **.** / **,** | Próxima / anterior música · roda do mouse no carro também troca |
| **W + S + A ou D** | **Zerinho**: acelerar e frear juntos virando o volante gira o carro 360° no lugar |
| **Clique / botão direito** parado na bomba | Abastecer / consertar no posto |
| **Mouse** | Olhar (visão 3D, clique para travar o cursor) |
| **V** | Troca a câmera: 3ª pessoa → 3ª perto → 3ª bem perto → 1ª pessoa → perspectiva giratória → vista de cima (a pé e no carro) |
| **'** (aspas, ao lado do 1) | Caixa de cheat: digite o código e Enter |
| **Z / C** ou botão direito arrastando | Girar a câmera em perspectiva |
| **+ / −** | Zoom da câmera em perspectiva |
| **N** | Som liga/desliga |
| **M** ou clique no minimapa | Abre / fecha o mapa em tela cheia |
| **Clique direito** no mapa | Marcar / desmarcar destino (GPS) |
| **T** | Missão do veículo (táxi ou viatura) · T de novo encerra |
| **ESC** / **P** | Menu |

### Celular e tablet (touch)

Os controles na tela aparecem sozinhos em telas de toque:

- **Joystick** à esquerda: andar / dirigir (empurrar até a borda corre).
- **Arrastar o dedo** no resto da tela: olhar em volta (visão 3D).
- Botões: **TIRO/SOCO** (segure para rajada; sem arma dá soco; parado na bomba do posto abastece), **ENTRAR/SAIR**, **PULO/FREIO**, **CORRER/NITRO** (liga e desliga), **ARMA**, **BUZINA**.
- Barra de cima: **MAPA**, **CÂMERA** (de cima → 3ª pessoa → 1ª pessoa), **RÁDIO**, **MÚSICA**.
- No mapa grande, **toque e segure** para marcar o destino do GPS.
- Na visão de cima, tocar na tela atira na direção do toque.

---

## Menu

Organizado em seções:

- **Estilo da cidade:** Modern ou Synthwave
- **Cidade:** tamanho (14×14, 24×24 ou 34×34 quarteirões), seed (mesma seed = mesma cidade; botão para sortear), hora inicial (o jogo sempre começa em 3D, 3ª pessoa; a câmera troca no jogo com V)
- **Mundo:** trânsito (0% a 100%), pedestres, chuva
- **Rádio:** fonte (músicas do servidor + minhas · só minhas músicas · **rádio online KRFM ao vivo**), adicionar MP3 do computador, testar rádio
- **CARREGAR JOGO SALVO:** aparece quando existe um save (mostra estilo, seed e data)
- **CONFIG** (também no jogo, botão ao lado de COMANDOS): volume **geral**, **música/rádio** e **efeitos do jogo** em sliders, som liga/desliga, **sombras** e **bloom**. Fica salvo no navegador.
- **VER COMANDOS:** abre uma janela com todos os atalhos, por categoria (a pé, veículo, armas, câmera e mapa, rádio e som, jogo, celular). Durante o jogo há o botão **COMANDOS [?]** ao lado de MENU (ou tecla **?** / **F1**); o jogo pausa enquanto a janela está aberta.
- **CONTINUAR:** aplica trânsito, pedestres, chuva e visão sem gerar cidade nova. Se o estilo foi trocado, gera uma cidade nova automaticamente.

---

## A cidade

### Geração procedural
- Cidade inteira gerada em tempo real a partir da seed.
- **Streaming por blocos:** só a área perto do jogador é montada; o resto é descartado. Uma 34×34 pesa o mesmo que uma 14×14.
- **Quarteirões variados:** comuns, longos (2 ou 3 quadras) e em formato de **L**.
- **Zoneamento com padrão:** a seed escolhe onde nasce o **centro urbano** (perto da praia, no meio do mapa ou deslocado). A cidade cresce em anéis a partir dele, com bordas irregulares mas sem "ilhas":
  - **centro denso:** os prédios mais altos;
  - **área urbana:** prédios que vão baixando conforme se afastam;
  - **bairros residenciais:** casas térreas (no Synthwave, prédios baixos);
  - **zona rural:** tudo o que fica longe do centro.
  
  O tamanho da zona rural é consequência de onde o centro nasceu: centro no meio do mapa → só os cantos são rurais; centro colado na praia → o lado oposto vira campo (até quase metade do mapa).
- **Tipos de quarteirão:** prédios, parques, praças, estacionamentos, casas, zona industrial, marcos da cidade e zona rural.
- **Praças:** piso de pedra, **obelisco** no centro com base em degraus, **estátuas** de bronze em pedestais, bancos e muitas árvores em volta. Os parques comuns também ficaram mais arborizados.
- **Orla turística:** os quarteirões de frente para a praia têm **letreiros luminosos** (como os neons do Synthwave, mas poucos) e toldos coloridos.
- **Zona rural** (nas áreas mais distantes do centro urbano):
  - **estradas de terra** lisas, sem faixas, sem semáforos e sem postes (à noite fica escuro de verdade);
  - terreno com **bosques**, pedras, cercas de madeira, **casas de fazenda** e fardos de feno;
  - na borda do mapa, em vez de prédios, uma **barreira natural de mata fechada e rochas**;
  - a terra tem **aderência tão baixa quanto pista molhada** e levanta poeira atrás do carro;
  - trânsito com mais picapes e SUVs; poucos pedestres.
- **Prédios:** alturas maiores no centro, com recuo de andares, parapeitos, caixas d'água, ar-condicionado no telhado, toldos e janelas que acendem à noite.
  - **Portaria** na fachada da rua: porta de vidro dupla com marquise e degrau (a porta acende à noite).
  - **Ar-condicionado de janela** (caixinha com ventilador) em alguns andares das fachadas externas.
  - **Antenas no telhado:** antenas de TV, parabólicas e mastros altos com **luz vermelha de sinalização** nos prédios mais altos.
- **Becos** entre prédios, com caçambas e lixo.
- **Casas térreas:** telhado de duas águas, porta, janelas, quintal, caminho, cerca, árvore, **antena de TV no telhado ou parabólica na parede**, alguns **varais com roupa** e **lixeiras na calçada**.
- **Garagens raras** com um **superesportivo exclusivo**.
- **Casa segura** (uma por cidade, sempre no mesmo lugar para a mesma seed): veja abaixo.

### Rios e pontes
- A cidade é cortada por **rios procedurais** que correm **paralelos à praia** e fazem curvas "em escada", como no mapa do GTA 1. Eles dividem o mapa em **ilhas/regiões**: por exemplo praia → rio → centro → rio → bairros e indústria.
- Quantidade pelo tamanho: 14×14 quase sempre 1 rio, 24×24 1 ou 2, 34×34 2.
- **Pontes** só em algumas ruas (a cada 3–4 quadras, mais as avenidas da borda). As outras ruas terminam na margem, então atravessar vira estratégia (e fuga da polícia).
- Metade das pontes tem **arco de aço** com tirantes; todas têm mureta dos dois lados.
- O rio é **rebaixado ~3 m** em relação à rua, com **paredes de canal** de concreto e mureta no alto (com colisão: carro e pedestre não caem por acidente). Cair no rio afoga, igual ao mar.
- As pontes têm **laje de verdade e pilar no meio do rio**: por cima passam os carros, **por baixo passam os barcos**.
- Os rios saem pelas bordas do mapa (a foz continua além dos prédios da borda).
- Minimapa e mapa grande mostram os rios em azul.
- **Rio poluído:** a zona industrial costuma nascer na beira de um rio (em ~3 de cada 4 cidades). Quando isso acontece, a água em volta fica **amarronzada** numa mancha irregular (não é um círculo perfeito, tem bordas onduladas e vai clareando até voltar ao azul), com **espuma, manchas de óleo e tambores boiando**. A mancha aparece também no minimapa e no mapa grande.

### Zona industrial
- Aparece **uma vez por cidade**, na transição entre a cidade e o campo (bairros afastados, perto da zona rural), ocupando até 4 quarteirões. Fica marcada no mapa como **INDÚSTRIA**.
- **Muros altos de concreto** ou **alambrados** (grade) em volta, portão com cancela listrada e guarita.
- **Galpões com telhado dente-de-serra** e janelas no telhado, portas de enrolar.
- **Tanques de armazenamento** com cúpula e escada, tubulação elevada ligando os tanques ao galpão.
- **Chaminés listradas** vermelho e branco **soltando fumaça** (com luz vermelha no topo à noite).
- Pilhas de **contêineres** coloridos.
- **Clima próprio:** perto dali o céu fica **nublado e acinzentado** (sem chuva) e o ar mais enevoado.

### Marcos da cidade (um de cada por mapa)
Cada um ocupa um quarteirão inteiro e aparece com o nome no mapa grande:
- **Arranha-céu** (estilo Empire State) no ponto mais denso do centro: torre de ~110 m com recuos escalonados, frisos verticais, coroa iluminada à noite e antena com luz vermelha.
- **Prefeitura:** prédio de pedra largo com **pórtico de colunas romanas**, frontão triangular, escadaria, **cúpula** verde com bandeira e mastros na frente.
- **Hospital:** torre central com faixas verticais e duas alas mais baixas recuadas, saguão de vidro com marquise de pronto-socorro, **cruzes vermelhas** luminosas, **heliponto** no topo e ambulância. **Quando você morre, renasce na porta do hospital.**
- **Universidade:** campus de tijolinho em U em volta de um gramado com árvores, **torre do relógio** com quatro mostradores e portões. Tamanho limitado; em quarteirões grandes o resto vira um parque arborizado do campus.
- **Estádio:** arquibancada oval colorida, gramado com linhas, portões de entrada nas pontas (com colisão correta) e 4 torres de refletores (acesas à noite). Em quarteirões compridos o estádio fica proporcional e o resto vira **estacionamento**.
- **Banco** (às vezes): prédio de pedra com colunas, escadaria, friso dourado, **cifrão luminoso** e **caixas eletrônicos** na fachada. Sempre fica **de frente para uma praça**.
- **Supermercado** (às vezes): galpão largo com faixa colorida, vitrine, marquise, carrinhos e **estacionamento cheio na frente**.
- **Shopping center** (às vezes): prédio grande com fachada de vidro, átrio redondo com cúpula de vidro, letreiro e **estacionamento em volta**.

### Ruas
- **Avenidas** (4 faixas, faixa dupla amarela).
- **Ruas de mão dupla** (2 faixas, faixa amarela simples, calçadas largas).
- **Ruas de mão única** (2 faixas no mesmo sentido, faixa branca tracejada e setas; sentido alternado entre ruas vizinhas, como em Nova York).
- Faixas de pedestre, postes de luz ligados por **cabos elétricos**, árvores e **semáforos** nos cruzamentos.

### Oficina mecânica (tuning)
- Uma por cidade, marcada no mapa com um **quadrado magenta** ("OFICINA MECÂNICA" na legenda). Garagem com letreiro neon magenta, pneus e ferramentas.
- Entre com o carro e pare no centro: abre a oficina, com **paleta de cores** e **seletor de cor livre** para pintar o carro, **instalação de nitro** (Shift acelerando; chamas azuis no escapamento) e **CONSERTAR**, que devolve a lataria a 100%. Por enquanto os serviços são grátis.
- Cor e nitro ficam salvos junto com o carro.

### Litoral
- Um dos 4 lados do mapa vira **praia**: calçadão com postes, mureta, gramado com palmeiras, areia com guarda-sóis, toalhas e banhistas, espuma e mar.
- A praia pode ocupar **o lado inteiro** ou **só metade dele**. Na meia praia, onde a areia acaba começa um **calçadão em L** que desce até o mar (com mureta, postes e guarda-corpo na ponta), e depois dele vêm prédios na beira d'água.
- **Barracas de praia** com toldo listrado e balcão espalhadas pela areia.
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

- **Ao ativar:** sempre nasce uma célula média **contra o vento**, perto de você, que chega até você empurrada pelo vento. Ela surge do zero e se forma aos poucos (~40 s até a força máxima, o mesmo tempo que leva para se dissipar). **Primeiro o céu fecha, depois começa a chover:** as gotas só aparecem quando a nuvem já está formada, e ao dissipar a chuva para antes de o céu abrir e dura de 1,5 a 3 minutos.
- **Depois de 1 minuto:** entra o sorteio. A cada 35–110 s há uma chance (sorteada entre **15% e 40%** por partida) de surgir uma nova célula, perto de você ou em qualquer lugar do mapa. No máximo 4 células ativas.
- **Tempestade a cada 6 chuvas:** a cada 5 células normais, a 6ª é uma **frente grande**: chuva que cobre o **mapa inteiro**, mais forte, e que ao terminar se **quebra em bolsões** menores espalhados.
- **Raios e trovões** quando chove forte: clarão no céu, raio visível com ramificações caindo ao longe e **trovão com atraso pela distância** (perto é estalo, longe é ronco).
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

## Barcos e píeres

- **Píeres** nas margens do rio (vários por cidade): uma **escadaria desce da calçada** até um deck de madeira na altura da água, com guarda-corpo, poste de luz e uma **lancha atracada**.
- **Marina na praia:** um píer comprido saindo da areia para o mar, com lancha.
- **Lancha:** entra com **F** estando no deck. Acelera, derrapa de lado na água, balança nas ondas, levanta a proa em velocidade e deixa **rastro de espuma**. Anda no rio (inclusive **por baixo das pontes**, desviando dos pilares) ou no mar; bate nas paredes do canal.
- Para sair do barco é preciso **encostar num píer ou na praia** (no meio do rio não dá).
- A polícia não consegue seguir você na água: fugir de lancha é uma ótima saída.
- **Easter egg:** em muitas cidades há um **corpo boiando no rio** (de preferência na parte poluída). Chegue de barco perto dele para pegar o que ele carregava: dinheiro ou uma arma.

## Rampas e saltos

- **Rampas** fora das ruas (não atrapalham o trânsito):
  - **em estacionamentos**, para voar por cima dos carros estacionados;
  - **em alguns becos entre prédios**, na entrada do beco, para atravessar voando por cima das caçambas.
- No ar o carro **não tem tração nem direção**; passa por cima de carros, postes, lixeiras e muretas baixas, mas bate em prédios. O carro empina conforme sobe e desce.
- **Aterrissagem:** quique, faíscas e tremor; pouso muito forte danifica o carro (de moto, derruba você). Cair na água afunda.
- **Saltos insanos** (algumas rampas de estacionamento pintadas de vermelho e branco, com **setas amarelas no chão**): ao decolar rápido, a câmera corta para um **ângulo cinematográfico em câmera lenta**. Se você pousar em terra depois da distância mínima, aparece **SALTO INSANO!** e você ganha créditos (só na primeira vez de cada um). Contador do tipo "2/5 saltos insanos", salvo no save.

## Veículos

- Modelos 3D procedurais com carroceria arredondada: **sedã, táxi, esportivo, conversível, hatch, SUV, van, picape, caminhão, ônibus, viatura, superesportivo e moto**.
- **Motos:** leves e rápidas, **inclinam nas curvas**, som de motor mais agudo, com piloto de capacete. Têm mais aderência e menos força bruta nas rodas (não ficam patinando) e deixam **uma única marca de pneu**. Bater forte (acima de ~30 km/h) **derruba você da moto**. Aparecem no trânsito (mais perto da praia e à noite no Synthwave).
- **Variedade por bairro:** conversíveis e esportivos perto da praia (o **conversível** é aberto, ótimo para dirigir em 1ª pessoa), SUVs/hatches/picapes nos bairros de casas, picapes e SUVs na zona rural, mais táxis no centro.
- **Controle de tração:** a força nas rodas é limitada pela aderência, então os carros não ficam patinando e chiando ao arrancar (nem na terra).
- **Aceleração ajustada:** todos os veículos aceleram mais rápido, proporcionalmente (caminhões, vans, picapes, SUVs e ônibus foram os que mais ganharam, com mais 10% na última leva).
- **Física 2D de corpo rígido com 4 pneus** (inspirada no protótipo de Pat Kerr que deu origem ao GTA): aderência lateral, derrapagem, freio de mão, marcas de pneu, fumaça, inclinação da carroceria.
- **Dano:** batidas fortes acumulam dano → o carro **pega fogo e explode**, empurrando e danificando o que estiver por perto (pode causar reação em cadeia).
- **Superesportivo:** chamas azuis no escapamento e **nitro** com Shift.
- **Faróis** com luz real no seu carro (automáticos à noite, G liga/desliga).
- Cerca de 10% dos carros com **neon embaixo**.
- Motor com som diferente por tipo (caminhão e ônibus mais graves).
- **Buzina grave** de dois tons.

### Trânsito
- Trânsito ajustável de vazio a **ruas lotadas** (centenas de carros, desenhados com instancing na GPU).
- Física completa perto do jogador; carros distantes andam "em trilho", com custo quase zero.
- **Semáforos** com verde/amarelo/vermelho; carros param, formam fila e respeitam mão única.
- Motoristas **buzinam** quando travados e, depois de 10–15 s, **dão ré e desviam**.
- Veículos que ficam encaixados um no outro **explodem**.

### Objetos destrutíveis
- **Postes de luz** (o cabo elétrico cai junto, com faíscas e um estalo curto de curto-circuito)
- **Árvores e palmeiras**
- **Semáforos:** derrubar um deixa o cruzamento **em pane**: os outros piscam amarelo e todos avançam achando que têm a preferência
- **Lixeiras** (saem voando e espalham lixo)

---

## Personagem e pedestres

- Personagem e pedestres em **pixel art 16×24** gerados por código, com animação em 4 direções.
- **Pulo** (Espaço): dá para pular por cima de carros baixos (e ficar em pé no teto), lixeiras e caçambas. Vans, caminhões e ônibus são altos demais.
- Pedestres andam pelas calçadas (inclusive nas calçadas largas das ruas estreitas), fogem e são atropelados.
- **Entram e saem de prédios e casas** pela porta (aparecendo e sumindo aos poucos). Na chuva, muito mais gente entra para se abrigar.
- De vez em quando **duas pessoas param para conversar**, uma de frente para a outra, gesticulando; depois cada uma segue seu caminho.
- Às vezes alguém **para em frente a um prédio olhando as janelas** por alguns segundos.
- Atropelados soltam um **"ai"** e **somem aos poucos**.
- Você só cai se for atingido **pela frente** de um carro; batidas de lado só empurram.

---

## Missões paralelas e créditos

- **Créditos ($)** aparecem embaixo do relógio e ficam no save. Por enquanto só acumulam; é o começo do sistema financeiro.
- **Taxista** (entre num táxi e aperte **T**):
  - um passageiro aparece numa calçada a 70–260 m, marcado com **seta verde** e GPS;
  - pare perto dele (devagar): ele anda até o carro e entra;
  - o GPS leva a um destino aleatório a 300–950 m; pare no destino para receber;
  - pagamento pela **distância** + **gorjeta** se chegar antes do tempo de bônus;
  - logo depois aparece a próxima corrida. Sair do táxi ou T encerra. Se o carro ficar muito batido durante a corrida, o passageiro desiste.
- **Vigilante** (entre numa viatura e aperte **T**; não funciona estando procurado):
  - 5 níveis de suspeitos fugindo pela cidade: **1 moto → 1 carro → 2 carros → 3 carros → 4 carros**;
  - os suspeitos ignoram semáforos e costuram o trânsito; cada um tem **seta vermelha** em cima;
  - para parar um suspeito, **bata ou atire** até o carro dele quebrar (ou explodir);
  - cada nível tem tempo-limite; se acabar, eles fogem e a missão falha;
  - completar o nível 5 paga **$500**. Bater nos suspeitos não deixa você procurado.

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

- Armas ficam nos **becos** (ponto verde no mapa). Cada beco sorteia qual arma tem:
  - **Pistola** (tecla 1): 0 a 100 balas, tiro a tiro.
  - **Metralhadora** (tecla 2): 60 a 200 balas, **rajada contínua** segurando o clique, com dispersão.
  - **Bazuca** (tecla 3): 3 a 8 foguetes. O projétil voa com **rastro de fogo e fumaça**; ao acertar um carro **ele explode na hora**, e a explosão afeta tudo em volta (carros, pedestres, você).
- Você carrega as três ao mesmo tempo, cada uma com sua munição; **X** ou a roda do mouse (a pé) alternam.
- Top-down: mira no cursor · 3D: mira no centro da tela.
- **Drive-by:** atira de dentro do carro em qualquer direção (inclusive com a bazuca).
- Tiros danificam veículos, matam pedestres e policiais. Disparar perto da polícia ou atingir viatura (inclusive com explosão) deixa você procurado.
- **Sangue:** tiros espirram sangue e deixam respingos no chão; pedestres mortos (por tiro, atropelamento ou explosão) deixam uma **poça de sangue** que some depois de um tempo. Você também sangra ao levar tiro da polícia.
- **Vida:** cruz vermelha nas calçadas, recupera 50 HP.

---

## Casa segura e save

- Cada cidade tem **uma única casa segura**, gerada pela seed (uma casa térrea, ou a portaria de um prédio no Synthwave). Ela aparece no mapa como uma **casinha amarela**.
- Na porta fica uma **seta amarela girando** (estilo GTA San Andreas). Andar até ela leva para dentro de uma **quitinete**: sofá, TV ligada, tapete, cama, guarda-roupa, cozinha, janela e quadros nas paredes (pintados proceduralmente).
- Entrar **salva o jogo** e **recupera a vida**. Não dá para entrar estando procurado.
- A seta amarela de dentro leva de volta para a rua.
- **Save automático** a cada 20 s (quando não está procurado) e ao fechar a página. Fica salvo no próprio navegador (localStorage):
  - seed, estilo e tamanho da cidade, hora do dia;
  - posição do jogador e o **veículo em uso** (tipo, cor, dano);
  - **vida**, armas e munição de cada uma;
  - itens já coletados (não reaparecem).
- No menu, **CARREGAR JOGO SALVO** recria a mesma cidade e coloca você onde parou.
- **Garagem da casa segura:** são **2 vagas amarelas cobertas dentro do terreno** — ao lado da casa quando o lote é largo, ou num terreno vizinho reservado só para a garagem. Nada fica na calçada ou na rua. Estacione numa vaga e saia do carro: ele fica **guardado e consertado** (com cor e nitro) e reaparece ali sempre, inclusive depois de carregar o jogo. Cabem carros, vans, picapes e motos (até ~5,6 m); **ônibus e caminhão não cabem** (aparece o aviso). Voltar com o carro guardado batido e deixá-lo na vaga também conserta.
- **Moto:** o boneco genérico só aparece quando um NPC pilota; com você, o seu personagem vai sentado nela.

---

## Mapa e navegação

- **Minimapa** com norte para cima (o sol nasce no leste/direita), prédios, becos, armas (verde), vida (vermelho), polícia e células de chuva.
- **Mapa em tela cheia** (TAB ou clique no minimapa) com legenda e indicação da **PRAIA**.
  - **Não pausa o jogo:** o trânsito, os pedestres e a chuva continuam se movendo no mapa.
  - Mostra a direção de cada célula de chuva com setas azuis.
- **Clique direito** (ou toque e segure no celular) marca um destino: **GPS** traça a rota pelas ruas, seta na borda do minimapa e feixe de luz amarelo no mundo.
- **M** abre e fecha o mapa direto, sem precisar sair da câmera com ESC.
- O mapa mostra praças/parques, a zona rural (verde, com estradas de terra marrons), a mata da borda e a casa segura.

---

## Câmeras

- **Top-down** com zoom pela velocidade (estilo GTA 1).
- **Perspectiva giratória:** câmera inclinada num ângulo fixo (~50°) que orbita em volta do jogador, como foco de objeto num editor 3D. Gira com Z / C, botão direito arrastando ou arrastando o dedo; + / − aproximam e afastam. WASD anda em relação à câmera e o tiro mira no cursor, como no top-down.
- O jogo **sempre começa em 3ª pessoa**; **V** (ou o botão CÂMERA no celular) passa pelos 4 modos, a pé ou no carro.
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
- Adicione músicas do seu computador pelo menu.
- **Fonte do rádio** (menu), lembrada entre partidas:
  - **Músicas do servidor + minhas**;
  - **Só minhas músicas** (ignora as do servidor);
  - **Rádio online · KRFM (ao vivo)**: toca o stream `https://azura.sims.dev.br/listen/krfm/128k.mp3`. Como é ao vivo, só liga e desliga (**R**). Se a conexão cair, reconecta sozinha. Os carros que passam tocando som continuam usando as músicas da lista.

---

## Tecnologia

- **Three.js r128** (WebGL), carregado de CDN
- Web Audio API (motor, sirene, rádio com EQ, som 3D, chuva, efeitos)
- Canvas 2D para sprites, texturas e mapas
- Sem dependências de backend

## Controle (DualSense / DualShock / Xbox / genéricos)
- Conecte por USB ou Bluetooth e **aperte qualquer botão** (exigência do navegador). Aparece "🎮 CONTROLE CONECTADO".
- **R2 / L2** analógicos: acelerar e freio/ré, com a pressão dosando a força. **Analógico esquerdo**: andar (meio curso anda devagar, curso todo corre) e dirigir. **Analógico direito**: câmera.
- Layout do **GTA V**: **R2** atirar (sem arma: soco) e acelerar no carro · **L2** freio/ré · **○/B** soco · **✕/A** correr (no carro: nitro) · **□/X** pular (no carro: drive-by) · **△/Y** entrar/sair · **L1** segurar = roda de armas (analógico escolhe, tempo lento) · **R1** freio de mão · **L1+R1** drive-by · **L3** buzina · **D-pad ←** no carro: rádio (segurar = roda do rádio) · **D-pad →** no carro: faróis / a pé: ação na loja ou próxima arma · **↑** próxima música · **↓** missão · **Touchpad/View** toque = câmera, segurar = mapa · **R2+L2+direção** zerinho · no posto: **□** abastece, **○** conserta.
- Menus navegáveis pelo controle: setas mudam o foco, ✕ confirma, ○ volta, ← → ajustam os sliders.
- **Vibração** (Chrome/Edge): batidas proporcionais ao impacto, pouso de rampa, tiros (pistola, rajada da SMG, coice da bazuca), explosões pela distância, levar tiro ou atropelamento, trovão próximo (com atraso do som), tremor em terra/grama, nitro, motor da moto e barco.
- **CONFIG → CONTROLE**: status do controle, intensidade da vibração, sensibilidade da câmera, zona morta, inverter eixo Y e botão TESTAR VIBRAÇÃO. Tudo salvo no navegador.
- No Firefox o controle funciona mas não vibra.

## Previsão do tempo e tempestade
- A tempestade **não sai mais sozinha** (não é mais a 6ª célula). As células de chuva normais continuam aleatórias.
- **Menu → MUNDO → tick "Tempestade"** (logo abaixo de "Chuva"): marcado, aparece em azul **"PREVISÃO DO TEMPO: TEMPESTADE EM 1H"** com a direção de onde ela vem, depois avisos de 30 min e 10 min. A partir dos 35 min as nuvens escuras surgem no horizonte daquele lado e avançam. **Deixando marcado, ela vem e vai alternando**: depois que uma passa, a previsão avisa a próxima (3 a 6 horas de jogo depois). **Desmarcar** cancela a previsão ou faz a tempestade em andamento se dissipar.
- O céu vira um **degradê de duas cores**: o horizonte do lado de onde a tempestade vem fica escuro e o lado oposto continua claro, com as nuvens escondendo a transição. A frente escura avança do horizonte: na hora marcada está bem em cima da cidade e, em ~30 min de jogo, **fecha o céu inteiro**, até o horizonte do lado oposto (aviso "TEMPESTADE · céu totalmente fechado"). Só então começa a chuva pesada, com raios e trovões.
- Ao enfraquecer, o céu começa a limpar **pelo mesmo lado** de onde ela veio e a parte escura atravessa o céu até sumir no lado oposto. Com chuva ligada, ela se quebra em pancadas isoladas. Funciona mesmo com a chuva comum desligada.
- **Chuva normal**: cada célula nova agora é anunciada antes de se formar ("chuva se formando a nordeste em ~30 min · vindo na sua direção" ou "bem aqui"). A célula leva alguns minutos para aparecer.
- Os avisos da previsão aparecem numa caixa azul no centro, um pouco abaixo dos avisos normais.

## Sol e lua
- O sol agora é um **disco redondo** (antes ele pegava o formato dos triângulos da esfera do céu).
- A **lua nasce quando o sol se põe e se põe quando ele nasce**, sempre no lado oposto do céu, e é escondida pelas nuvens.
- **4 fases**, uma por noite em sequência: **nova → crescente → cheia → minguante** (a fase inicial depende da seed). Desenhadas no padrão do hemisfério sul: a crescente aparece iluminada à esquerda e a minguante à direita. A lua nova fica quase invisível.
- A claridade da noite muda com a fase: lua cheia ilumina bem mais, lua nova deixa a cidade mais escura. Com a lua alta, a luz da noite vem da direção dela.
- Às 18:30 aparece em azul o aviso da noite, por exemplo "🌕 HOJE À NOITE: LUA CHEIA". O relógio mostra o ícone da fase durante a noite. A contagem dos dias é salva junto com o jogo.

## Asfalto molhado e poças com reflexo
- **Chão molhado:** depois que chove, o chão vai molhando aos poucos onde a célula de chuva passou (ruas, calçadas e estradas de terra) e seca devagar quando a chuva para. Durante a tempestade a cidade toda fica molhada.
- **Asfalto molhado:** ganha um brilho de espelho fraco. Nas **poças** o reflexo é forte, como um espelho.
- **Reflexo real:** a cena é renderizada espelhada, então aparecem prédios, céu, letreiros de neon, postes acesos e faróis dos carros, de dia, à noite e também no estilo synthwave/vaporwave.
- **Gotas:** enquanto chove, as gotas fazem anéis que distorcem o reflexo nas poças.
- **Tamanho das poças:** nas calçadas são menores (escoam melhor); na terra ficam barrentas.
- **CONFIG → GRÁFICOS → "Reflexos nas poças e no asfalto molhado":** liga e desliga o efeito. Desligar deixa o jogo mais leve em PCs fracos e celulares.

## Salvar / carregar por arquivo
- O jogo **não salva mais sozinho no navegador**. No MENU (ESC) use **SALVAR JOGO**: baixa um `.psave` (texto JSON) com seed, estilo, posição, vida, dinheiro, armas, dia/hora, carros da garagem, itens pegos e saltos feitos.
- **CARREGAR ARQUIVO** (no menu inicial ou em jogo) escolhe o `.psave` e volta exatamente de onde parou — funciona em qualquer navegador/PC, sem depender de cookies.
- Se ainda existir um save antigo do navegador, aparece **CARREGAR SAVE ANTIGO (NAVEGADOR)** para não perder o progresso (ele não é mais atualizado).
- Ao fechar a aba com mais de 1 min sem salvar, o navegador pergunta se quer mesmo sair.
- **Casa segura**: entrar restaura a vida e conserta o veículo com que você chegou (se estiver por perto); ela **não salva** mais — o aviso lembra de salvar pelo menu.

## Ajustes de mundo (CONFIG → MUNDO)
- **Trânsito** e **Pedestres** saíram do menu inicial e foram para o CONFIG (valem na hora e ficam salvos).
- Nova escala: trânsito padrão **20%** (100% agora = metade do máximo antigo); pedestres padrão **75%** (= quantidade padrão antiga; 100% ≈ +33%). Polícia: 1 viatura até 50%, 2 até 90%, 3 acima.

## Outras correções
- Poças e asfalto molhado **secam em ~1h de jogo** depois que a chuva passa (antes levava mais de 4h). Desligar os reflexos em PC fraco: CONFIG → GRÁFICOS.
- Entrada das indústrias não tem mais poste plantado na frente do portão.
- Modelos revisados para a câmera de rua: pórticos (prefeitura/banco) com a face de baixo da viga e do frontão, marquises do hospital e do mercado, cornijas, toldos, placas, neon, aparelhos de ar, postes, semáforos, quiosques, píeres, garagens e o assoalho dos carros agora fechados por baixo (~3% a mais de polígonos).

## Ruas de neon (synthwave)
- Os neons das fachadas (barrinhas coloridas, faixas nos andares, contornos no topo e letreiros) seguem um **plano de ruas**: ruas retas de ponta a ponta.
- A **rua da praia é sempre de neon**, com neon reforçado (praticamente todo prédio tem barrinhas, e muitos têm letreiros e faixas). Depois vêm paralelas a ela a cada ~1/3 da cidade.
- Entre duas paralelas de neon entram 1 ou 2 **trechos perpendiculares** que param uma quadra antes de encostar nelas, então as ruas de neon nunca se cruzam.
- **Toda rua que cruza uma rua de neon fica sem neon nenhum.** O plano muda com a seed.

## Save completo (clima + CONFIG) e pontes
- O arquivo `.psave` agora guarda também **o clima inteiro**: chuva/tempestade ligadas, células de chuva em andamento, tempestade (previsão, frente de nuvens, cobertura, fase), vento e o **chão molhado/poças**. Carregar continua exatamente com o mesmo tempo.
- O save também leva as **configurações do CONFIG** (volumes, som, sombras, bloom, reflexos, trânsito, pedestres, controle). Ao carregar o arquivo, elas são aplicadas e ficam salvas nesse navegador.
- **Pontes**: agora há água correndo por baixo delas, e as margens embaixo da ponte têm muro de canal.

## Visual arredondado (agora padrão)
- **Esquinas com curva suave**: entre ruas estreitas o canto vira um quarto de círculo de calçada; nas avenidas o canto da calçada é cortado em arco. Carros, pedestres, mapa e poças seguem a curva.
- **Postes** com tubo cilíndrico, braço curvo e luminária oval; **semáforos** cilíndricos com tampas arredondadas e luz em esfera.

## Monitor de desempenho (MENU → MONITOR ou tecla F3)
- Painel flutuante no canto esquerdo, que fica aberto enquanto você joga (a escolha fica salva). Mostra números e barras (verde/amarelo/vermelho):
  - **FPS** e tempo de cada quadro.
  - **CPU**: quanto do tempo de cada quadro o jogo passa calculando e mandando desenhar (thread principal da aba).
  - **GPU**: tempo real da placa de vídeo por quadro, quando o navegador libera o cronômetro (`EXT_disjoint_timer_query_webgl2`; Chrome/Edge no PC normalmente sim). Senão aparece "n/d".
  - **RAM**: memória JavaScript da aba (Chrome/Edge).
  - **VRAM**: estimativa da memória de vídeo (malhas, texturas, buffers de tela, reflexo e sombras).
  - Chamadas de desenho, triângulos, geometrias e texturas.
- O navegador não deixa nenhuma página ler o uso real de CPU/GPU/RAM do sistema; os valores são medidos de dentro do jogo e servem para comparar opções (sombras, bloom, reflexos, tamanho da cidade, trânsito).
- No menu, o botão de carregar agora se chama **CARREGAR SAVE**.

## Modelos
- **Sedã e táxi remodelados**: carroceria arredondada feita por seções (capô levemente caído, traseira mais alta, cantos arredondados), cabine com para-brisa e vidro traseiro inclinados, teto curvo e colunas na cor do carro, para-choques, grade, retrovisores, maçanetas e faróis/lanternas ovais. Os outros veículos continuam com o modelo antigo por enquanto.
- **Lancha**: a proa (bico) estava com as faces viradas para dentro e ficava invisível; corrigido, e ganhou fundo.

## Todos os veículos remodelados
- Viatura, esportivo, superesportivo, conversível, hatch, SUV, van, picape, ônibus e caminhão agora usam a mesma modelagem do sedã: carroceria e cabine feitas por seções arredondadas, vidros inclinados, teto curvo, para-choques, retrovisores e faróis/lanternas ovais (cada tipo com suas proporções: SUV alto com bagageiro, van monovolume, picape com caçamba, super com aerofólio e entradas laterais, conversível com para-brisa e bancos).
- **Moto**: tanque, carenagem e para-lamas arredondados, garfo e guidão cilíndricos, farol oval.
- **Lancha**: casco em V feito por seções, com proa pontuda e convés de madeira.

## Câmera dentro do veículo (1ª pessoa)
- Agora fica **sobre o capô**, olhando por cima dele. Em ônibus e caminhão (sem capô) fica logo à frente do para-brisa.

## Correções
- **Reflexo da chuva em cima do rio**: a máscara das áreas molhadas era aplicada de cabeça para baixo; agora o molhado fica só em ruas, calçadas e pontes.
- **Notificações empilhadas**: cada aviso tem seu próprio tempo e eles se encaixam um embaixo do outro (até 4), com a barra de missão em cima; nada mais se sobrepõe.
- **Rádio**: o nome da música aparece ao entrar no veículo ou ao trocar de música/estação e some depois de 5 s.
- **Rodas**: a parte de cima de cada roda fica escondida abaixo da **linha da lataria**, que acompanha a suspensão: quando a carroceria levanta ao acelerar, frear ou inclinar em curva, aparece mais roda naquele lado (como numa caixa de roda de verdade); com o carro capotado também fica certo. Nos carros distantes a roda é meia roda fixa.
- **CONFIG → RESTAURAR PADRÕES** (no fim do painel): volta volumes (85/80/85%), som, sombras, bloom, reflexos, trânsito 20%, pedestres 75% e controle (vibração 100%, sensibilidade 100%, zona morta 15%, sem inverter) ao padrão. Pede um segundo clique para confirmar.

- Ao começar um **jogo novo**, o save antigo do navegador (do sistema anterior) é apagado e o botão dele some.

## Atualização grande (novembro)
### Motos
- Rodas das motos inteiras; o boneco 3D saiu. O piloto agora é um **personagem 2D** sentado na moto.
- **Roubar a moto**: o piloto sai correndo. **Um tiro na moto**: o piloto cai, levanta e vai embora (não morre).
### Tiros e armas
- Pistola e metralhadora precisam de **3 tiros** para matar; quem leva tiro e sobrevive foge. **Tiro na cabeça mata na hora** ("TIRO NA CABEÇA"). Bazuca continua matando na hora.
- Nova arma: **Colt Magnum** (tecla **4**): 1 tiro mata, coice forte, recarga lenta. Aparece nos becos como as outras armas.
### Personagens
- Todos os personagens 2D foram refeitos com o **dobro de pixels** (32×48): rosto com olhos, sobrancelhas, nariz e boca, boné com aba, camisa com gola e sombra, cinto, sapatos com sola, cabelo comprido, **óculos** e **colar** em alguns NPCs.
- Pronto para a futura loja de roupas: cores de **boné/chapéu, camisa, calça e sapato** e **óculos/colar** liga-desliga (paleta do jogador, salva no arquivo de save).
### Praia
- **Areia com textura granulada** e **espuma/ondinhas** na beira do mar e nas margens dos rios.
- **Gente caminhando pela praia** (mais de dia, poucas à noite); vão embora quando chove.
- **1 ou 2 fogueiras** na praia com gente em pé olhando o fogo: 1–2 pessoas de dia, 5–6 à noite.
- **Farol** na ponta da praia sem prédios, no fim de um banco de areia; à noite a luz acende. Chegar na porta leva ao topo; a portinha do topo desce. Pular do parapeito: queda mata, cair na água afoga.
### Cidade
- **Cemitério** (estilo Los Santos): muro, portões de grade abertos, árvores secas retorcidas, lápides variadas (algumas tortas), mausoléu com porta (futuramente entrável) e obelisco no centro. Em cima, nuvem negra permanente e pouco sol (sem chuva) e **neblina** só nele. (Na cidade 7×7 ele não cabe.)
- **Delegacia** (prédio azul e branco "POLÍCIA"). **Morreu → renasce na porta do hospital; preso → na porta da delegacia** (se não existir, lugar aleatório).
- Algumas casas têm **piscina** (cair nela não mata) e **churrasqueira**, algumas acesas soltando fumaça.
- **Letreiros de neon com texto**: HOTEL, CAFETERIA, BAR e BOATE com nomes sorteados (COLONY, FLAMINGO, PARADISO, ATLANTIS…).
- **Casa segura** com interior mais caprichado (estante, quadros, luminária, móveis arredondados).
### Céu e eventos
- **Helicóptero e avião** passam de vez em quando pela cidade (alturas diferentes, nunca colidem), com som de motor abafado e luzes piscando.
- **Perseguições aleatórias**: às vezes uma viatura persegue um carro pela cidade; ela atira, bate, o carro pode explodir ou sumir no horizonte. Não deixa você procurado.
- **TV da casa segura**: perto da TV aparece "F Assistir TV". A câmera vai para uma vista aérea estilo telejornal ("PIXEL NEWS · AO VIVO", manchete e letreiro correndo, sem HUD) mostrando **uma tempestade se formando** ou **uma perseguição policial**. F de novo desliga: o clima volta ao que estava e a polícia/carro somem.
### Cheats (CONFIG → CHEATS)
- Vida infinita, munição infinita, veículo nunca explode, nunca ser procurado e **+ $1000**. Com qualquer cheat usado na partida, **não dá para salvar**.
### Modo mobile
- Em celular o jogo avisa **"MODO MOBILE"** e gera a cidade **7×7** (sombras e reflexos começam desligados). A opção "Mobile · 7×7" também existe no tamanho da cidade.

## Correções (desempenho e piscadas)
- **Vazamento dos pilotos de moto**: algumas motos saíam do jogo sem limpar o boneco 2D, que ficava parado no lugar (o "rastro") e se acumulava (centenas em poucos minutos, derrubando o FPS). Agora todo piloto fica numa lista e é apagado assim que a moto some.
- **Piscadas (z-fighting)**: varredura automática de todas as superfícies da cidade.
  - Câmeras de rua (1ª/3ª pessoa e capô) com plano de corte próximo maior (25–30 cm em vez de 5–15 cm): profundidade 2 a 6 vezes mais precisa à distância.
  - Pátio das indústrias não fica mais exatamente sobre a calçada; estacionamentos dos marcos (shopping etc.) acima do piso do marco; caminhos e covas do cemitério, deck da piscina e grelha da churrasqueira separados das superfícies de baixo.

## Atualização v67 — soco, controles GTA V, posto de combustível e zonas de procurado
### Soco
- Sem arma (ou com **PUNHOS** escolhido na roda / tecla **1**): **R**, **clique** ou **○** dão um soco com avanço do corpo, som de golpe e faíscas.
- Pedestre: 1º soco faz fugir, 2º derruba no chão, 3º mata. Policial a pé leva o soco e você fica procurado. Soco em carro amassa um pouco (e viatura também chama a polícia).
- Em 1ª pessoa aparece um punho em pixel art na tela que avança a cada soco.
- O HUD mostra **PUNHOS** quando você está de mãos vazias.
### Controles iguais ao GTA V
- Teclado, mouse e controle remapeados (tabela acima e janela COMANDOS / CONFIG → CONTROLE atualizadas).
- **Roda de armas** (segurar TAB ou L1) e **roda do rádio** (segurar Q ou D-pad ←): o jogo entra em câmera lenta enquanto ela está aberta, ícones em pixel art, munição de cada arma, armas que você não tem ficam apagadas, ponteiro mostra a direção.
- O rádio ganhou **próxima / anterior** com **.** e **,** e a opção **DESLIGADO** dentro da roda.
### Rádio contínuo
- Trocar de carro não pula mais a música: ela continua exatamente de onde parou.
### Motos
- Os pilotos (pedestres e o jogador) desceram ~50% no assento: as pernas ficam na altura das rodas, parecendo sentados na moto.
### Zerinho
- Acelerar e frear ao mesmo tempo (W+S ou R2+L2) com a direção virada faz o carro girar 360° no lugar, com fumaça dos pneus, marcas de borracha no asfalto e vibração. Funciona também na moto (gira um pouco mais devagar). Gasta mais combustível.
### Combustível
- Cada veículo que você dirige tem tanque (barra laranja **COMBUSTÍVEL** abaixo da vida do carro). Carros roubados vêm com 40–100%; viaturas, cheias.
- Acelerar, nitro e zerinho gastam mais. Um tanque dura cerca de 15 minutos acelerando. Abaixo de 15% a barra pisca e aparece aviso; sem combustível o carro só anda na banguela.
- O nível do tanque vai junto no save.
### Posto de combustível (novo prédio comercial)
- 1 a 3 postos por cidade (depende do tamanho), com bandeira aleatória (PIXOIL, NEOGÁS, TURBO, SOLAR): cobertura com faixa colorida e luzes, 2 ilhas com 4 bombas (telinhas e mangueiras), totem de preços, loja de conveniência com vitrine e letreiro "CONVENIÊNCIA 24H", gelo, gás, ar-condicionado no teto e estacionamento em volta. Ícone laranja de bomba no minimapa e no mapa, e nome **POSTO** no mapa grande.
- **Pare ao lado de uma bomba**: aparece o aviso com os preços. **Clique / □** abastece ($0,60 por %; se faltar dinheiro, abastece o que der) e **botão direito / ○** conserta o carro (preço pelo dano).
- **Explode muito forte**: 2 tiros numa bomba (1 de Magnum), batida forte de carro na bomba, ou explosão por perto (bazuca, carro explodindo). São **3 explosões em sequência** (bomba, bomba, cobertura), cada uma com 3× o tamanho e a quantidade de fogo e fumaça da explosão de carro, raio de dano bem maior, luz forte e tremor de tela.
- Depois o posto fica **todo preto e chamuscado** (como os carros queimados), com manchas de queimado no chão e fogo e fumaça nas bombas por cerca de 30 segundos. As bombas e a loja ficam fora de uso e o posto **reabre depois de um dia no jogo**. Se foi você, a polícia vem atrás.
### Loja de conveniência (novo interior)
- Entre pela seta amarela na porta da loja. Lá dentro: piso xadrez, balcão com caixa registradora, prateleira de cigarros e bebidas atrás do caixa, 2 gôndolas cheias de produtos, 5 geladeiras de vidro iluminadas, máquina de café/raspadinha, caixa eletrônico, cone de piso molhado, letreiro "ABERTO" na vitrine, plaquinha do lanche e luminárias. O caixa é um personagem uniformizado que acompanha você com o olhar.
- **Comprar comida**: sem arma, no balcão, **E / F / D-pad →** compra um lanche por $15 e recupera 50 de vida.
- **Assalto**: com uma arma na mão, mire no caixa. Ele treme de medo e uma barra de ASSALTO enche em ~3 s. Ao completar, você leva $180–420 (bem menos se o mesmo posto foi assaltado há pouco). Atirar dentro da loja acelera o assalto; matar o caixa rende o dinheiro da gaveta.
- **A polícia vem na hora**: o caixa aperta o alarme e em 7 s a polícia invade (ou assim que você sair), com viaturas chegando ao posto e você já procurado. Socar o caixa também dispara o alarme. Não dá pra entrar na loja estando procurado.
### Nível de procurado por região
- Quando você **escapa** da polícia, fica uma **zona vermelha** (raio de 2 quarteirões, 4 de diâmetro) no local do crime, desenhada no minimapa e no mapa grande como uma mancha vermelha pulsante (como a mancha azul da chuva).
- A polícia guarda a sua **roupa** e **todos os veículos** em que te viu durante a perseguição (a pé também conta).
- Entrar na zona com **a mesma roupa e o mesmo veículo** = perseguição imediata. Só **um dos dois** igual = você tem **10 segundos** pra sair da zona antes de ser reconhecido. Roupa e veículo trocados = passa despercebido.
- No HUD, ao lado de onde aparece PROCURADO, ficam um ícone de **camisa** e um de **carro**: aceso em vermelho quando ainda bate com o crime, apagado quando você trocou. Mostra também o estado: tempo até a zona sumir, "NA ZONA", "SUSPEITO 7s" (piscando) ou "DISFARÇADO".
- Ficando longe da zona por **1 hora no jogo** (1 minuto real), ela some. As zonas vão junto no save.

## Atualização v68
- **Cheats do GTA San Andreas**: digite o código direto durante o jogo (como no SA), ou aperte **'** para abrir a caixa de cheat, ou faça a sequência do PS2 no controle. A lista completa também está em **CONFIG → CHEATS**. Qualquer cheat bloqueia salvar até um jogo novo.

| Código | Efeito | Controle (PS2) |
|---|---|---|
| HESOYAM | Vida cheia, +$250.000, conserta e enche o tanque do carro | R1 R2 L1 ✕ ← ↓ → ↑ ← ↓ → ↑ |
| AEZAKMI | Nunca ser procurado (liga/desliga) | ○ → ○ → ← □ △ ↑ |
| BAGUVIX | Vida infinita (liga/desliga) | ↓ ✕ → ← → R1 → ↓ ↑ △ |
| FULLCLIP | Munição infinita (liga/desliga) | L1 R1 □ R1 ← R2 R1 ← □ ↓ L1 L1 |
| LXGIWYL | Armas 1: pistola e metralhadora | R1 R2 L1 R2 ← ↓ → ↑ ← ↓ → ↑ |
| KJKSZPJ | Armas 2: + Colt Magnum | R1 R2 L1 R2 ← ↓ → ↑ ← ↓ ↓ ← |
| UZUMYMW | Armas 3: + bazuca | R1 R2 L1 R2 ← ↓ → ↑ ← ↓ ↓ ↓ |
| TURNUPTHEHEAT | Polícia na cola | R1 R1 ○ R2 ← → ← → ← → |
| TURNDOWNTHEHEAT / ASNAEB | Limpa o procurado e as zonas vermelhas | R1 R1 ○ R2 ↑ ↓ ↑ ↓ ↑ ↓ |
| CPKTNWT | Explode todos os carros por perto | R2 L2 R1 L1 L2 R2 □ △ ○ △ L2 L1 |
| AUIFRVQS | Chuva | R2 ✕ L1 L1 L2 L2 L2 ○ |
| AFZLLQLL | Sol (limpa chuva e tempestade) | R2 ✕ L1 L1 L2 L2 L2 ↓ |
| SPEEDFREAK | Nitro no carro atual | — |

  Enquanto você digita um código, as letras a partir da 3ª não acionam comandos do jogo (W A S D continuam andando). A 1ª e a 2ª letra ainda funcionam normalmente; por exemplo, o F de FULLCLIP entra/sai do carro. A caixa **'** evita isso.
- **Câmeras novas**: além da 3ª pessoa padrão, **3ª pessoa perto** e **3ª pessoa bem perto** (no carro, câmera colada na lataria; a pé, o personagem bem grande na tela). O **V** passa por elas antes da 1ª pessoa.
- **Etiqueta flutuante na bomba**: ao chegar perto do posto de carro, aparece em cima da bomba mais próxima um balão laranja com os botões certos: **□/○** no DualSense/DualShock, **X/B** no Xbox, **clique/botão direito** no teclado e mouse, com o preço de abastecer e consertar e o lembrete "pare ao lado da bomba".
- **Pilotos de moto ainda mais baixos**: a cintura fica na altura do tanque.
- **Roda do rádio** mostra 10 músicas (mais a opção DESLIGADO).
- **Som dos carros que passam** tocando música 30% mais baixo.
- **Correção**: nas esquinas entre rua de asfalto e estrada de terra (como ao lado do cemitério na zona rural), o canto arredondado da calçada deixava aparecer um pedaço quadrado de asfalto; agora ali é terra.

## Atualização v69 — postos estilo Vice City (synthwave)
- No estilo **synthwave/vaporwave**, os postos ganham o visual do GTA Vice City: duas faixas grossas de **neon** em volta da cobertura, metade **rosa/magenta** e metade **ciano**, com um brilho colorido no chão debaixo de cada metade.
- Paleta pastel compatível: cobertura e loja em creme/pêssego, pilares quadrados cor de salmão, bombas prateadas com faixa **vermelha e azul** e base pêssego, placas com fundo roxo escuro e letras rosa.
- A loja de conveniência ganha neon **verde-menta** no contorno do telhado e um neon rosa acima da vitrine.
- Depois de explodir, o posto continua todo preto, sem neon.

## Atualização v70
### Shopping center novo (com interior de 2 andares)
- **Fachada nova**: prédio grande de 2 andares com pórtico central todo de vidro (caixilhos), marquise com pilares na entrada, alas laterais mais altas (CINEMA e MODA), faixas de vidro nos dois andares, faixa colorida entre os pisos, claraboia e máquinas no teto e letreiro **SHOPPING PIXEL**. Estacionamento em volta.
- **No synthwave/vaporwave** (inspirado no North Point Mall do GTA Vice City): paredes rosa-pastel e azul-turquesa, contorno de **neon vermelho** no prédio e no pórtico, letreiro vermelho. Por dentro: piso xadrez rosa/roxo, paredes lilás e neons **ciano e rosa** nas vitrines, na galeria, na claraboia e nos corrimãos da escada rolante.
- **Interior**: entre pela seta amarela na porta. **Térreo**: corredor com fonte, canteiros com palmeiras, bancos, luminárias, galeria do 1º andar vista de baixo e **escada rolante** no fim do corredor. Subindo, o **1º andar** tem vão central com corrimão de vidro, de onde se vê o térreo lá embaixo. Para descer, pegue a escada rolante de novo.
- **16 lojas** (8 por andar) com fachada, vitrine, porta e letreiro: MODA PIXEL, CONVENIÊNCIA, GAMES, TECH, LIVROS, CAFÉ, ÓTICA, JOIAS, SAPATOS, BRINQUEDOS, MÚSICA, ESPORTES, PERFUMES, PIZZA, FARMÁCIA e CINEMA. As de vitrine têm produtos e prateleiras; há clientes passeando.
- **CONVENIÊNCIA** (térreo): no balcão, **E / F / D-pad →** compra lanche ($15, +50 de vida).
- **MODA PIXEL** (térreo): araras, manequins, espelho e vendedora. No balcão abre o **PROVADOR**, onde você troca a cor da **camisa, calça e calçado**, coloca ou tira **boné** (com cor), **óculos escuros** (várias lentes) e **colar** (ouro, prata, rosa, azul). Tem prévia do personagem de frente e de lado; cada peça trocada custa $10. Trocar de roupa também despista a polícia nas **zonas vermelhas**.
- Não dá para entrar no shopping estando procurado.
### Fantasma do cemitério (easter egg)
- Perto do cemitério pode surgir um **fantasma**: é um pedestre comum, mas todo em branco e cinza, translúcido, com brilho, tremulando e **flutuando acima do chão**. De dia é raro; à noite é bem mais comum.
- Ele vaga entre os túmulos, geme (som) e persegue quem chega perto. Se encostar, **tira vida** (menos se você estiver dentro do carro).
- **Se ele te matar** ("ASSOMBRADO"), dá tempo de ver o fantasma **voltando à vida**: ele ganha cor aos poucos, entre brilhos, vira uma pessoa de verdade e sai andando.
### Água viva
- **Mar e rios limpos** ficaram **transparentes**: dá para ver o fundo de areia com pedras e algas. O fundo do mar afunda e escurece até o azul profundo.
- **Ondas**: linhas de reflexo que se movem pela superfície do mar e dos rios.
- **Cardumes**: grupos de peixes nadando debaixo d'água, no mar e nos rios limpos (o rio poluído continua sem vida).
### Céu e clima
- **Nuvens esparsas** no céu limpo: a cobertura muda sozinha de 0% a 100% ao longo do dia. No máximo fica um pouco abaixo da nuvem de uma célula de chuva, só para "sujar" o céu.
- **Poças com sol forte**: o reflexo fica mais fraco (mais transparente) de dia quando não está chovendo em cima de você.
### Farol
- O caminho de areia até o farol agora é **orgânico**: faz uma curva suave, abre em leque onde encosta na praia (sem o "T") e tem **pedras cinzas** de vários tamanhos ao longo das bordas, com espuma acompanhando a curva. O mapa também desenha a curva.
### Cidade
- **Semáforos novos**: caixa **amarela** com **3 lentes** (vermelho, amarelo e verde), e só a cor ativa acende. O pisca-alerta da tempestade pisca a lente amarela.
- **Calçada contínua** em cruzamento em T de ruas estreitas: o lado sem rua não tem mais aqueles "dentes" na calçada.
- **Domos mais redondos** (farol, prefeitura, shopping e parabólicas) com mais polígonos.
- **Posto no mapa**: o ícone laranja aparece mesmo com o posto longe (antes só aparecia depois de passar perto).
### Motos
- O piloto não "pula" mais ao inclinar a moto nas curvas.

## Atualização v71 — menus mais legíveis
- Os **menus** (MENU, CONFIG, COMANDOS, OFICINA e PROVADOR) agora usam uma **fonte normal** (sem pixel), bem mais fácil de ler. As cores, bordas, botões e o estilo continuam os mesmos. O HUD do jogo (vida, dinheiro, avisos, mapa) continua com a fonte pixelada.
- A lista de **cheats do GTA SA** (códigos e sequências do controle) saiu do CONFIG e foi para a janela **COMANDOS**, numa seção própria. No CONFIG ficaram só as caixinhas de cheat e o botão +$1000.

## Atualização v72
- **Todos os textos da interface sem pixelização**: HUD (vida, dinheiro, relógio, avisos, procurado, velocímetro, rádio), MONITOR (F3), rodas de arma/rádio, botões de toque, notícias da TV, e os textos do minimapa e do mapa grande agora usam fonte normal. Cores e estilo continuam os mesmos. Os letreiros dentro do mundo 3D (placas, neons, fachadas) continuam no estilo pixel.
- **Cemitério sem a nuvem escura própria**: o céu sobre o cemitério agora segue as nuvens ralas normais do céu limpo. A neblina no chão do cemitério continua.
- **Correção na água do rio**: um trecho de rio perto da zona poluída ficava inteiro escuro e sem ondas (o jogo tratava o bloco todo como poluído). Agora isso é decidido pedaço por pedaço: só onde a água está suja o fundo fica marrom e sem ondas, e no resto a água fica transparente e com ondas. A água também não escurece mais onde dois trechos se sobrepõem.

## Atualização v73 — janela COMANDOS por abas
- A janela **COMANDOS** agora tem **botões por grupo**: A PÉ, VEÍCULO, ARMAS, CÂMERA E MAPA, RÁDIO E SOM, JOGO, CONTROLE, CHEATS e CELULAR. Cada botão mostra só aquele grupo e **TUDO** mostra a lista completa. Funciona com mouse, toque e controle (setas + ✕).
- O **mapa completo dos botões do controle** saiu do CONFIG e foi para COMANDOS → CONTROLE. No CONFIG → CONTROLE ficaram só os ajustes: status do controle, vibração, sensibilidade, zona morta, inverter eixo e testar vibração.

## Atualização v74 — desempenho e ajustes
### Otimização do reflexo das poças
- O reflexo agora é atualizado **a cada 2 frames** (na poça não dá pra perceber a diferença) e em **resolução menor** (36% da tela; 30% na vista de cima).
- O espelho só desenha os **quarteirões próximos** (até ~230 m da câmera).
- **Pedestres, sombras dos pedestres, partículas (fumaça, faíscas, chuva de vidro…)** não entram mais no reflexo: são centenas de objetos pequenos que custavam caro e quase não apareciam na poça.
- Na prática, o custo extra do chão molhado caiu bastante, e o visual continua igual.
### Cemitério
- O **portão dos fundos**, que abria direto contra o mausoléu e aparecia torto, foi **removido**: o muro dos fundos agora é contínuo. A entrada é só pelo portão da frente, com o arco e o nome.
- **Armas escondidas entre os túmulos**: Colt Magnum, metralhadora, bazuca e um kit de vida. São um motivo para entrar… e para fugir do fantasma.
### Controle
- **Correr**: segure **✕ / A** (ou aperte o L3).
- **Mapa**: agora é **SHARE / VIEW / BACK** (ou o touchpad, se você usar). A **câmera** é no **R3**.
### Céu
- **Mais nuvens** no céu limpo: a cobertura varia de ~30% a 100% (antes podia chegar perto de zero), com nuvens mais cheias, sempre um pouco abaixo da nuvem de chuva.

## Atualização v75 — nuvens de fundo separadas da chuva
- As nuvens do céu limpo agora são uma **camada própria, em escala menor**: muitos fiapos e flocos pequenos, brancos e translúcidos, que se movem devagar. Elas **não usam mais o mesmo desenho das nuvens de chuva**.
- **0%** = só alguns fiapos; **100%** = céu bem "salpicado" de nuvenzinhas, mas ainda com o azul aparecendo. Isso é bem diferente da nuvem grande e escura de uma célula de chuva ou da tempestade, que continuam do jeito que eram.
- A cobertura muda sozinha ao longo do dia (~30% a 100%). Onde há nuvem de chuva, as nuvenzinhas somem por baixo dela.

## Atualização v76 — radar giratório e barras compactas
- O **minimapa (radar) gira** junto com o jogador: a frente de para onde você olha/dirige fica sempre **para cima**, como no GTA. A rotação é suavizada, sem tremer. A seta do jogador fica fixa apontando para cima, a bússola **N** gira mostrando onde é o norte, a seta amarela do destino fora do radar e o clique direito para marcar destino acompanham a rotação. O mapa grande continua com o norte para cima.
- As barras **VEÍCULO** e **COMBUSTÍVEL** ficam **lado a lado** e com **metade da largura**, acima da barra de vida, para ocupar menos espaço na tela. Elas continuam medindo de 0 a 100% normalmente.

## Atualização v77
- A **barra de vida** agora tem exatamente a mesma largura total das duas barras de cima (VEÍCULO + COMBUSTÍVEL): as bordas da esquerda e da direita ficam alinhadas, no PC e no celular.

## Atualização v78 — reflexo ainda mais leve (menos engasgos na chuva)
- O reflexo voltou a ser atualizado **todo frame**, mas bem mais barato. Atualizar um frame sim e outro não deixava o tempo de cada frame irregular e dava sensação de engasgo; agora o ritmo é constante.
- **Resolução do reflexo** caiu de 36% para **22%** da tela (18% na vista de cima). Na poça, que já é distorcida e borrada, quase não dá pra notar.
- O espelho agora só desenha os **quarteirões até ~150 m** (antes ~230 m).
- Entram no reflexo **só as coisas grandes e que brilham**: paredes e janelas dos prédios, telhados, neons, luzes, postes, semáforos e carros. Ficam de fora árvores, calçadas, faixas, lixeiras, detalhes pequenos, pedestres e partículas.
- O **céu não é mais redesenhado** no reflexo: a poça usa um gradiente com a cor do céu da hora. Antes o reflexo recalculava as nuvens e a tempestade, que era a parte mais cara.

## Atualização v79
- **Semáforo derrubado não deixa mais o trânsito caótico**: bater num semáforo continua deixando os semáforos daquele cruzamento **piscando amarelo** (aviso "SEMÁFORO EM PANE"), mas os carros da IA seguem o ciclo normal de parar e andar naquele cruzamento, sem invadir uns aos outros.

## Atualização v80
- O botão **CONTINUAR** do menu agora é **verde** (fica mais claro com o mouse ou o controle em cima), destacando a volta para o jogo.

## Atualização v81
- **Poças mais discretas**: o reflexo ficou com **metade da intensidade** (semi-reflexivo, mais "opaco"), e o céu refletido ficou um pouco mais escuro. Assim a poça mostra o asfalto molhado por baixo, em vez de parecer um espelho.
- A resolução do reflexo voltou para **36%** da tela (30% na vista de cima). O resto das otimizações da v78 continua.

## Atualização v82 — chão molhado mais leve
- **Formato das poças pré-calculado**: o desenho das poças (antes 3 camadas de ruído calculadas em cada pixel, todo frame) agora é uma textura gerada uma vez no começo do jogo. As poças ficam com o mesmo visual.
- **Chuva por textura**: o shader não percorre mais as 6 células de chuva em cada pixel; a intensidade da chuva vem da mesma grade que já marca onde está molhado (atualizada a cada 0,5 s).
- **Gotas só perto da câmera**: os anéis das gotas nas poças só são calculados até ~25 m (e somem suavemente). A ondulação do reflexo usa uma leitura de textura em vez de 2 ruídos.
- **Corte de distância**: depois de ~150–175 m o chão molhado é descartado logo no início do cálculo (antes fazia tudo para depois sumir na neblina).
- **Calçada simplificada**: a calçada molhada só escurece e ganha um brilho leve nas poças, sem espelho e sem gotas. O reflexo fica na rua, onde aparece de verdade.

## Atualização v83 — reflexo falso e luz da tempestade
### Reflexo falso nas poças (bem mais leve)
- As poças **não redesenham mais a cidade** num espelho (era o que mais pesava na chuva). Agora o reflexo é **simulado**: a poça mostra um degradê com as cores do céu da hora (mais claro olhando de longe, mais escuro olhando pra baixo) e **rastros verticais de luz** das luzes próximas, como asfalto molhado de verdade: postes acesos, faróis dos carros à noite, semáforos (vermelho/amarelo/verde) e o giroflex vermelho/azul da polícia.
- As gotas, a ondulação, as poças e o brilho continuam iguais. Prédios e carros não aparecem mais "espelhados" na poça.
### Tempestade escurece aos poucos
- Antes o sol só sumia de repente quando a chuva começava (depois do céu 100% fechado). Agora a luz do sol e do ambiente **começa a cair quando a tempestade cobre 50% do céu** e chega ao mais escuro quando cobre 100%.
- A tempestade escurece cerca de **10% a mais** que uma chuva comum isolada, mas continua bem mais clara que a noite. Quando ela vai embora, a luz volta junto com o céu limpando.

## Atualização v84 — chuva natural
- O tick **Chuva** saiu do menu: a chuva agora faz parte do jogo sempre. Só a **Tempestade** continua como opção, por ser especial.
- Cada cidade tem o seu **clima**, que vem do **seed**: uma chance de chuva entre **0% e 100%**. Com chance baixa quase nunca chove; com chance alta chove bastante. Exemplos: seed 411 ≈ 84%, 1234 ≈ 85%, 909580 ≈ 33%, 520300 ≈ 27%, 77 ≈ 5%, 5 ≈ 4%.
- O momento de cada chuva continua **aleatório**: você pode entrar no jogo e não chover, ou entrar e **já estar chovendo** (a chance de começar chovendo é a mesma do clima da cidade).
- Saves antigos com a chuva desligada passam a ter chuva natural também.
- Cheats: **AUIFRVQS** faz chover agora, em cima de você; **AFZLLQLL** limpa o céu e segura a chuva por uns 5 minutos.

## Atualização v85
- No menu, a opção virou só **Tempestade ativa**, com uma linha curta: chega 1h de jogo (1 min real) depois de marcar e volta de tempos em tempos.
- A explicação da chuva foi para uma nova aba **FAQ** na janela COMANDOS, junto com respostas rápidas sobre previsão do tempo, tempestade, seed, como salvar e o que fazer se o jogo estiver pesado.
