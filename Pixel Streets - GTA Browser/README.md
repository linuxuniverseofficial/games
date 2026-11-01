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
| **Espaço** | Pular (a pé) · Freio de mão (no carro) |
| **Clique** ou **E** | Atirar (segure para rajada) |
| **1 / 2 / 3** | Pistola / Metralhadora / Bazuca |
| **X** ou roda do mouse (a pé) | Trocar de arma |
| **Mouse** | Olhar (visão 3D, clique para travar o cursor) |
| **V** | Troca a câmera: 3ª pessoa → 1ª pessoa → perspectiva giratória → vista de cima (a pé ou no carro) |
| **Z / C** ou botão direito arrastando | Girar a câmera em perspectiva |
| **+ / −** | Zoom da câmera em perspectiva |
| **G** | Ligar / desligar faróis |
| **Q** / roda do mouse | Próxima música |
| **R** | Ligar / desligar o rádio |
| **H** | Buzina |
| **N** | Som liga/desliga |
| **M**, **TAB** ou clique no minimapa | Abre / fecha o mapa em tela cheia (sem precisar do ESC) |
| **Clique direito** no mapa | Marcar / desmarcar destino (GPS) |
| **T** | Missão do veículo (táxi ou viatura) · T de novo encerra |
| **ESC** | Menu |

### Celular e tablet (touch)

Os controles na tela aparecem sozinhos em telas de toque:

- **Joystick** à esquerda: andar / dirigir (empurrar até a borda corre).
- **Arrastar o dedo** no resto da tela: olhar em volta (visão 3D).
- Botões: **TIRO** (segure para rajada), **ENTRAR/SAIR**, **PULO/FREIO**, **CORRER/NITRO** (liga e desliga), **ARMA**, **BUZINA**.
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
- **△/Y** entrar/sair · **✕/A** pular (a pé) e freio de mão · **○/B** freio de mão e voltar nos menus · **R1** atirar (a pé também R2 ou □) · **L1** nitro · **□/L3** buzina no carro · **L3** correr a pé · **← →** arma · **↑** rádio · **↓** missão · **R3** câmera · **Touchpad/View** mapa · **Options/Start** menu.
- Menus navegáveis pelo controle: setas mudam o foco, ✕ confirma, ○ volta, ← → ajustam os sliders.
- **Vibração** (Chrome/Edge): batidas proporcionais ao impacto, pouso de rampa, tiros (pistola, rajada da SMG, coice da bazuca), explosões pela distância, levar tiro ou atropelamento, trovão próximo (com atraso do som), tremor em terra/grama, nitro, motor da moto e barco.
- **CONFIG → CONTROLE**: status do controle, intensidade da vibração, sensibilidade da câmera, zona morta, inverter eixo Y e botão TESTAR VIBRAÇÃO. Tudo salvo no navegador.
- No Firefox o controle funciona mas não vibra.

## Previsão do tempo e tempestade
- A tempestade **não sai mais sozinha** (não é mais a 6ª célula). As células de chuva normais continuam aleatórias.
- **Menu → MUNDO → TEMPESTADE**: escolha "Prevista: chega em 1h de jogo (1 min)". Aparece em azul **"PREVISÃO DO TEMPO: TEMPESTADE EM 1H"** com a direção de onde ela vem, depois avisos de 30 min e 10 min. A partir dos 35 min as nuvens escuras surgem no horizonte daquele lado e avançam até cobrir a cidade.
- O céu vira um **degradê de duas cores**: o horizonte do lado de onde a tempestade vem fica escuro e o lado oposto continua claro, com as nuvens escondendo a transição. A frente escura avança do horizonte: na hora marcada está bem em cima da cidade e, em ~30 min de jogo, **fecha o céu inteiro**, até o horizonte do lado oposto (aviso "TEMPESTADE · céu totalmente fechado"). Só então começa a chuva pesada, com raios e trovões.
- Ao enfraquecer, o céu começa a limpar **pelo mesmo lado** de onde ela veio e a parte escura atravessa o céu até sumir no lado oposto. Com chuva ligada, ela se quebra em pancadas isoladas. Depois a opção volta para "Sem tempestade". Funciona mesmo com a chuva comum desligada.
- **Chuva normal**: cada célula nova agora é anunciada antes de se formar ("chuva se formando a nordeste em ~30 min · vindo na sua direção" ou "bem aqui"). A célula leva alguns minutos para aparecer.
- Os avisos da previsão aparecem numa caixa azul no centro, um pouco abaixo dos avisos normais.

## Sol e lua
- O sol agora é um **disco redondo** (antes ele pegava o formato dos triângulos da esfera do céu).
- A **lua nasce quando o sol se põe e se põe quando ele nasce**, sempre no lado oposto do céu, e é escondida pelas nuvens.
- **4 fases**, uma por noite em sequência: **nova → crescente → cheia → minguante** (a fase inicial depende da seed). Desenhadas no padrão do hemisfério sul: a crescente aparece iluminada à esquerda e a minguante à direita. A lua nova fica quase invisível.
- A claridade da noite muda com a fase: lua cheia ilumina bem mais, lua nova deixa a cidade mais escura. Com a lua alta, a luz da noite vem da direção dela.
- Às 18:30 aparece em azul o aviso da noite, por exemplo "🌕 HOJE À NOITE: LUA CHEIA". O relógio mostra o ícone da fase durante a noite. A contagem dos dias é salva junto com o jogo.
