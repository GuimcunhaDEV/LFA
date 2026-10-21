# Atividade sobre agentes inteligentes

Aula 20/10/2026 | Professora Kadidja Valéria | Inteligência artificial

Disciplina: Linguagens Formais e Autômatos | Ciência da Computação

Estudante: Guilherme Humberto | Turma: N1 CiC

## Exercício 2.3

### a. Um agente que detecta apenas informações parciais sobre o estado não pode ser perfeitamente racional.

- Julgamento: Falso.
- Justificativa: Um agente pode tomar a melhor decisão possível com as informações que recebe, mesmo sem conhecer todo o estado do ambiente. Ser racional não significa saber tudo, mas escolher a ação mais adequada com base nas percepções, no conhecimento e nas opções disponíveis.
- Exemplo ou contraexemplo: Um aspirador pode perceber que o cômodo atual está sujo e limpá-lo sem saber se o outro cômodo também está sujo. A informação que falta não impede que a ação atual seja racional.

### b. Existem ambientes de tarefa nos quais nenhum agente reativo puro pode comportar-se racionalmente.

- Julgamento: Verdadeiro.
- Justificativa: Um agente reativo puro decide com base na percepção atual e não guarda um histórico dos acontecimentos. Em ambientes em que uma decisão depende de informações vistas anteriormente, essa limitação pode impedir uma atuação racional.
- Exemplo ou contraexemplo: No jogo da memória, o agente precisa lembrar onde cartas foram reveladas antes. Um agente que só considera a carta que está vendo naquele momento não consegue usar essa informação passada para escolher melhor.

### c. Existe um ambiente de tarefa em que todo agente é racional.

- Julgamento: Verdadeiro.
- Justificativa: Isso é possível quando as ações não alteram a medida de desempenho. Nesse caso, escolher uma ação boa ou ruim não faz diferença para o resultado avaliado.
- Exemplo ou contraexemplo: Imagine um ambiente com apenas um estado, no qual todas as ações disponíveis dão exatamente a mesma recompensa. Como nenhuma escolha melhora ou piora o resultado, qualquer agente satisfaz a medida de desempenho.

### d. A entrada para o programa de agente é a mesma que a entrada para a função de agente.

- Julgamento: Falso.
- Justificativa: A função de agente relaciona o histórico completo de percepções a uma ação. Já o programa normalmente recebe a percepção atual e usa seu estado interno, quando existe, para considerar o que aconteceu antes.
- Exemplo ou contraexemplo: Em um jogo, a função de agente pode definir uma ação com base em todas as jogadas observadas até ali. O programa pode receber apenas a jogada mais recente e manter internamente as informações anteriores.

### e. Toda função de agente é implementável por uma combinação de programa/máquina.

- Julgamento: Falso.
- Justificativa: Uma função de agente pode, em teoria, especificar decisões para um número ilimitado de históricos de percepção. Nem toda função desse tipo pode ser calculada por um programa finito; algumas não são computáveis.
- Exemplo ou contraexemplo: Se uma função exigisse resolver corretamente um problema matemático não computável para decidir cada ação, nenhum programa comum conseguiria implementá-la em todos os casos. Programas implementam funções computáveis, não qualquer função imaginável.

### f. Um agente escolhe sua ação uniformemente ao acaso. Existe um ambiente determinista em que esse agente é racional.

- Julgamento: Verdadeiro.
- Justificativa: O ambiente pode ser determinista e, mesmo assim, todas as ações disponíveis terem o mesmo efeito sobre a medida de desempenho. Nesse caso, escolher ao acaso não prejudica o resultado.
- Exemplo ou contraexemplo: Em um ambiente no qual qualquer ação produz a mesma recompensa, um agente que escolhe aleatoriamente entre as ações é racional, ainda que não escolha sempre a mesma.

### g. É possível para um dado agente ser perfeitamente racional em dois ambientes de tarefa distintos.

- Julgamento: Verdadeiro.
- Justificativa: A racionalidade depende do ambiente e da medida de desempenho. Uma mesma política pode ser adequada em mais de um ambiente, desde que as ações que escolhe sejam as melhores para os objetivos de cada um.
- Exemplo ou contraexemplo: Um agente que sempre escolhe a ação “parar” pode ser racional em dois ambientes diferentes nos quais parar seja a ação que oferece a maior recompensa, ou tenha o mesmo resultado que as demais ações.

### h. Todo agente é racional em um ambiente não observável.

- Julgamento: Falso.
- Justificativa: Não conseguir observar o ambiente não torna qualquer ação racional. Ainda é possível comparar as escolhas com o desempenho esperado e com o conhecimento que o agente possui.
- Exemplo ou contraexemplo: Um robô que não recebe informações do ambiente e fica parado pode deixar de alcançar o objetivo, mesmo que pudesse seguir uma estratégia previamente programada. A ausência de percepção não faz com que toda decisão seja igualmente boa.

### i. Um agente jogador de pôquer perfeitamente racional nunca perde.

- Julgamento: Falso.
- Justificativa: Um agente racional escolhe as ações que oferecem o melhor resultado esperado com as informações disponíveis, mas não controla todas as cartas nem as decisões dos adversários. Portanto, uma boa decisão ainda pode terminar em derrota.
- Exemplo ou contraexemplo: Um jogador pode apostar corretamente com uma mão forte e perder porque o adversário recebeu cartas melhores. Isso não prova que a decisão foi irracional.

## Exercício 2.4

As classificações abaixo consideram um agente individual em cada situação. Quando necessário, adoto uma versão simplificada do cenário para deixar claras as hipóteses. “Conhecido” significa que o agente conhece as regras ou o funcionamento geral do ambiente; isso não significa que consiga prever todas as situações.

### Caso 1 — Jogar futebol

- Agente analisado: Um jogador individual de futebol, humano ou robótico.
- Objetivo e hipóteses: Contribuir para que a equipe vença, respeitando as regras. Considero uma partida normal, com duas equipes, árbitro e bola em movimento.
- P — Medida de desempenho: Gols e assistências, passes bem-sucedidos, recuperação da bola, respeito às regras e resultado da equipe.
- E — Ambiente: Campo, bola, gols, companheiros, adversários, árbitro e condições do jogo.
- A — Atuadores: Pernas, pés, cabeça e tronco, usados para correr, chutar, passar, saltar e mudar de direção.
- S — Sensores: Visão e audição, além da percepção de equilíbrio, posição corporal e contato com a bola.

| Propriedade | Classificação | Justificativa |
|---|---|---|
| Observabilidade | Parcialmente observável | O jogador vê boa parte do campo, mas pode não enxergar a bola em todos os momentos nem conhecer as intenções dos demais jogadores. |
| Número de agentes | Multiagente, cooperativo e competitivo | O jogador coopera com seus companheiros e disputa a partida contra a equipe adversária. |
| Previsibilidade | Estocástico | A trajetória da bola e as jogadas dependem das ações de muitas pessoas e de variações físicas, tornando o resultado difícil de prever com certeza. |
| Dependência entre decisões | Sequencial | Cada passe, deslocamento ou chute afeta as situações seguintes. |
| Mudança durante a decisão | Dinâmico | A bola e os jogadores continuam se movimentando enquanto o agente decide. |
| Natureza dos elementos | Combinação de contínuos e discretos | Posições, velocidade e tempo variam continuamente; gols, faltas e cartões são eventos discretos. |
| Conhecimento do funcionamento | Conhecido | As regras do jogo são conhecidas, embora o comportamento dos adversários não possa ser previsto completamente. |

### Caso 2 — Explorar os oceanos subterrâneos de Titã

- Agente analisado: Uma sonda robótica autônoma projetada para explorar um oceano subterrâneo hipotético em Titã.
- Objetivo e hipóteses: Mapear a região e coletar dados científicos, preservando a sonda e sua energia. Como é um cenário hipotético, considero que a sonda dispõe de sensores e propulsão adequados, mas não de um mapa completo.
- P — Medida de desempenho: Área mapeada, qualidade e quantidade dos dados coletados, cumprimento dos objetivos e conservação de energia e equipamentos.
- E — Ambiente: Oceano subterrâneo, rochas, relevo, correntes, obstáculos, temperatura, pressão e possíveis fontes de interesse científico.
- A — Atuadores: Propulsores, lemes, braços robóticos, instrumentos de coleta e mecanismos de comunicação.
- S — Sensores: Câmeras, sonar, sensores de pressão e temperatura, instrumentos de análise química e sensores de posição e movimento.

| Propriedade | Classificação | Justificativa |
|---|---|---|
| Observabilidade | Parcialmente observável | Os sensores só alcançam uma parte do entorno, e obstáculos ou regiões ainda não exploradas permanecem desconhecidos. |
| Número de agentes | Agente único | Considero apenas a sonda tomando decisões, sem outros agentes inteligentes participando diretamente da exploração. |
| Previsibilidade | Estocástico | Correntes, falhas e condições locais podem produzir resultados difíceis de prever com exatidão. |
| Dependência entre decisões | Sequencial | Cada rota e coleta afeta as informações disponíveis e as possibilidades das etapas seguintes. |
| Mudança durante a decisão | Dinâmico | A sonda se move e as correntes podem mudar enquanto ela planeja a próxima ação. |
| Natureza dos elementos | Combinação, com predominância contínua | Posição, profundidade, temperatura e pressão variam continuamente; comandos e estados de missão também podem ser discretos. |
| Conhecimento do funcionamento | Desconhecido | Como a região é pouco explorada, a sonda não conhece completamente o mapa nem todas as condições e efeitos de suas ações. |

### Caso 3 — Comprar livros usados de IA na Internet

- Agente analisado: Um agente de compra que procura livros usados de inteligência artificial em lojas e plataformas on-line.
- Objetivo e hipóteses: Encontrar a edição desejada em boas condições, com preço total razoável e vendedor confiável. Considero que o agente conhece as regras básicas da plataforma, mas não consegue verificar fisicamente o livro antes da compra.
- P — Medida de desempenho: Adequação da edição, estado de conservação, preço total com frete, confiabilidade do vendedor e recebimento do livro correto.
- E — Ambiente: Sites de venda, anúncios, livros disponíveis, vendedores, compradores, meios de pagamento e serviços de entrega.
- A — Atuadores: Pesquisar, aplicar filtros, abrir anúncios, comparar opções, enviar perguntas, adicionar ao carrinho e realizar ou cancelar a compra.
- S — Sensores: Títulos e descrições, fotos, preços, avaliações dos vendedores, informações de frete, estoque e políticas de devolução.

| Propriedade | Classificação | Justificativa |
|---|---|---|
| Observabilidade | Parcialmente observável | Fotos e descrições não garantem que o estado real do livro corresponda ao anúncio; também podem existir informações desatualizadas. |
| Número de agentes | Multiagente, com interesses diferentes | O comprador interage com vendedores e pode disputar exemplares limitados com outros compradores. |
| Previsibilidade | Estocástico | Um anúncio pode ficar indisponível, o vendedor pode demorar a responder e a entrega pode sofrer atrasos. |
| Dependência entre decisões | Sequencial | A busca, a comparação, as perguntas e a decisão de comprar dependem dos resultados das etapas anteriores. |
| Mudança durante a decisão | Dinâmico | Preços, estoque e disponibilidade podem mudar enquanto o agente compara os anúncios. |
| Natureza dos elementos | Combinação de discretos e contínuos | Abrir um anúncio ou confirmar uma compra são ações discretas; preços, frete e prazo de entrega são valores numéricos. |
| Conhecimento do funcionamento | Conhecido, com informações incompletas sobre os itens | O agente pode conhecer as regras do site, embora não saiba com certeza o estado físico do livro nem todas as condições de venda. |

### Caso 4 — Jogar uma partida de tênis

- Agente analisado: Um dos jogadores, considerado individualmente.
- Objetivo e hipóteses: Vencer a partida, devolvendo a bola dentro das regras e evitando erros. Considero uma partida normal, com adversário, quadra e equipamentos em condições adequadas.
- P — Medida de desempenho: Pontos e games vencidos, erros não forçados, colocação dos golpes e resultado da partida.
- E — Ambiente: Quadra, rede, bola, raquetes, adversário, árbitro e condições da superfície.
- A — Atuadores: Pernas, braços, mãos, tronco e raquete, usados para correr, posicionar-se e golpear a bola.
- S — Sensores: Visão, audição, tato e percepção da posição e do movimento do próprio corpo.

| Propriedade | Classificação | Justificativa |
|---|---|---|
| Observabilidade | Parcialmente observável | A bola e a quadra são visíveis, mas a intenção do adversário e detalhes exatos de sua próxima ação não são conhecidos. |
| Número de agentes | Multiagente e competitivo | Os jogadores buscam objetivos opostos: cada um tenta vencer a partida. |
| Previsibilidade | Estocástico | O agente não controla os golpes do adversário, e pequenas variações na execução alteram a trajetória da bola. |
| Dependência entre decisões | Sequencial | Cada golpe depende da bola recebida e influencia o golpe seguinte. |
| Mudança durante a decisão | Dinâmico | A bola e os jogadores continuam em movimento enquanto cada um escolhe como agir. |
| Natureza dos elementos | Combinação de contínuos e discretos | Movimento e trajetória são contínuos; pontos, games e sets são contagens discretas. |
| Conhecimento do funcionamento | Conhecido | As regras e os fundamentos do jogo são conhecidos, mesmo sem conhecer a estratégia do adversário. |

### Caso 5 — Praticar tênis contra uma parede

- Agente analisado: Um jogador praticando sozinho contra uma parede.
- Objetivo e hipóteses: Treinar precisão e regularidade dos golpes. Considero que a bola e a parede ficam visíveis e que as condições da quadra e da parede são estáveis; variações reais ainda podem ocorrer.
- P — Medida de desempenho: Quantidade de devoluções consecutivas, precisão dos golpes, controle da direção e consistência.
- E — Ambiente: Jogador, raquete, bola, parede, quadra e superfície de jogo.
- A — Atuadores: Pernas, braços, mãos, tronco e raquete para se deslocar e golpear a bola.
- S — Sensores: Visão para acompanhar a bola e a parede, audição do contato e percepção corporal para ajustar força e posição.

| Propriedade | Classificação | Justificativa |
|---|---|---|
| Observabilidade | Completamente observável, na hipótese adotada | A bola, a parede e o espaço de jogo estão visíveis e fornecem as informações relevantes para posicionar o golpe. |
| Número de agentes | Agente único | A parede não toma decisões; apenas devolve a bola conforme o contato. |
| Previsibilidade | Determinístico, aproximadamente | Com condições estáveis e comportamento físico conhecido, o rebote pode ser estimado. Na prática, vento, efeito e erros de execução introduzem variações. |
| Dependência entre decisões | Sequencial | Cada golpe define a trajetória que o jogador precisará responder em seguida. |
| Mudança durante a decisão | Dinâmico | A bola continua se deslocando enquanto o jogador se posiciona e prepara a próxima devolução. |
| Natureza dos elementos | Combinação de contínuos e discretos | A posição e a velocidade da bola variam continuamente; cada golpe é uma ação separada. |
| Conhecimento do funcionamento | Conhecido | O jogador conhece as regras básicas e pode aprender a prever os rebotes da parede. |

### Caso 6 — Realizar um salto de altura

- Agente analisado: Um atleta realizando uma tentativa de salto em altura.
- Objetivo e hipóteses: Superar a maior altura possível sem derrubar a barra e dentro das regras. Considero uma tentativa individual, sem modelar diretamente a disputa estratégica com outros atletas.
- P — Medida de desempenho: Altura superada, validade da tentativa, número de tentativas utilizadas e segurança do atleta.
- E — Ambiente: Pista de aproximação, barra, suportes, área de queda, superfície, clima e regras da competição.
- A — Atuadores: Pernas, braços e tronco, usados para correr, impulsionar-se, girar e ajustar a posição do corpo.
- S — Sensores: Visão, equilíbrio, percepção da posição dos membros, sensação de velocidade e contato com a pista e o colchão.

| Propriedade | Classificação | Justificativa |
|---|---|---|
| Observabilidade | Parcialmente observável | O atleta vê a barra e a pista, mas não mede perfeitamente a própria força, fadiga, velocidade e posição corporal em cada instante. |
| Número de agentes | Agente único, para uma tentativa | A execução analisada depende principalmente das ações do atleta. Os outros competidores influenciam a disputa, mas não controlam diretamente o salto. |
| Previsibilidade | Estocástico | Mesmo com técnica conhecida, pequenas diferenças na corrida, impulsão e posição corporal podem mudar o resultado. |
| Dependência entre decisões | Sequencial | A impulsão e a passagem pela barra dependem da corrida de aproximação e dos movimentos anteriores. |
| Mudança durante a decisão | Dinâmico | O corpo está em movimento durante a corrida e o salto, então a situação muda rapidamente. |
| Natureza dos elementos | Combinação de contínuos e discretos | Velocidade, ângulo e altura são contínuos; uma tentativa válida ou inválida é um resultado discreto. |
| Conhecimento do funcionamento | Conhecido | As regras e os princípios físicos gerais são conhecidos, embora o resultado exato de cada tentativa não seja garantido. |

### Caso 7 — Participar de um leilão de um item, realizando lances

- Agente analisado: Um comprador que decide quando e quanto oferecer pelo item.
- Objetivo e hipóteses: Tentar adquirir o item sem pagar mais do que ele vale para o comprador e respeitando o orçamento. Considero um leilão on-line com lances de outros participantes e regras publicadas.
- P — Medida de desempenho: Conseguir o item desejado, pagar um preço aceitável, respeitar o orçamento e evitar compras desvantajosas.
- E — Ambiente: Item leiloado, vendedor, plataforma, regras do leilão, relógio ou prazo final e demais participantes.
- A — Atuadores: Enviar um lance, aumentar a oferta, definir um limite máximo e deixar de participar.
- S — Sensores: Preço atual, histórico de lances disponível, tempo restante, descrição do item, regras e notificações da plataforma.

| Propriedade | Classificação | Justificativa |
|---|---|---|
| Observabilidade | Parcialmente observável | O agente pode ver os lances divulgados, mas não conhece necessariamente o limite de cada concorrente nem se haverá novas ofertas. |
| Número de agentes | Multiagente e competitivo | Vários compradores disputam o mesmo item, enquanto o vendedor busca concluir a venda. |
| Previsibilidade | Estocástico | A próxima oferta depende das decisões de outros participantes, que não são conhecidas antecipadamente. |
| Dependência entre decisões | Sequencial | Cada lance muda o preço e influencia as decisões seguintes e a estratégia do agente. |
| Mudança durante a decisão | Dinâmico | O preço e o tempo restante mudam durante o leilão, inclusive enquanto o agente calcula uma oferta. |
| Natureza dos elementos | Combinação de discretos e contínuos | Os lances são ações discretas, mas preço e tempo restante são medidas numéricas que mudam ao longo do processo. |
| Conhecimento do funcionamento | Conhecido, com incerteza sobre os participantes | As regras podem ser conhecidas, mas as avaliações e estratégias dos concorrentes permanecem ocultas. |

### Comparação final

1. No tênis contra outra pessoa, as decisões do adversário mudam a trajetória da bola e tornam a situação competitiva e menos previsível. Contra a parede não há um adversário tomando decisões: o rebote depende principalmente do golpe e das condições físicas, o que deixa o treino mais previsível.

2. Na compra de livros usados, o agente depende de anúncios e fotos que podem não mostrar todas as marcas de uso. Também pode haver estoque desatualizado, custos de frete ou diferenças entre a descrição e o produto recebido. Por isso, ele precisa comparar fontes e lidar com a incerteza antes de comprar.

3. No futebol, companheiros e adversários mudam o posicionamento e as opções de passe a cada instante. No leilão, os demais participantes podem aumentar o preço ou superar uma oferta. Em ambos os casos, o agente precisa considerar que as decisões dos outros influenciam o resultado.

## Exercício 2.5

### Agente

- Definição: É algo que percebe o ambiente por meio de sensores e age sobre ele usando atuadores. Pode ser uma pessoa, um robô ou um programa de computador.
- Exemplo: Um robô aspirador percebe sujeira e obstáculos e se movimenta para limpar o chão.

### Função de agente

- Definição: Descreve qual ação deve ser escolhida para cada sequência possível de percepções. É uma especificação do comportamento esperado, independentemente de como ele será programado.
- Exemplo: Uma função pode indicar que, ao perceber um obstáculo à frente, o robô deve virar para evitar a colisão.

### Programa de agente

- Definição: É a implementação executável que recebe percepções e produz ações em uma máquina. Diferentemente da função abstrata, precisa ser representado por instruções e recursos computacionais concretos.
- Exemplo: O software de um robô lê os sensores de distância e envia um comando para os motores virarem.

### Racionalidade

- Definição: É escolher a ação que oferece o melhor resultado esperado de acordo com as percepções, o conhecimento disponível, as ações possíveis e a medida de desempenho. Ser racional não garante vencer sempre, pois o ambiente pode ter incertezas.
- Exemplo: Um agente de compras escolhe o livro com a edição certa, bom estado e menor custo total, considerando também a confiabilidade do vendedor.

### Autonomia

- Definição: Um agente é autônomo quando seu comportamento depende de suas próprias percepções e experiências, e não apenas de instruções fixas fornecidas de antemão. A aprendizagem pode aumentar essa autonomia.
- Exemplo: Um robô aspirador que ajusta seus trajetos depois de aprender onde costuma encontrar obstáculos é mais autônomo do que um que segue sempre um caminho fixo.

### Agente reativo

- Definição: Escolhe uma ação diretamente a partir da percepção atual, normalmente por regras do tipo “se acontecer isso, faça aquilo”. Um agente reativo puro não usa um histórico interno para decidir.
- Exemplo: Um sistema que acende a luz quando o sensor detecta movimento e a apaga quando não detecta.

### Agente baseado em modelo

- Definição: Mantém um estado interno e usa um modelo de como o ambiente funciona para interpretar as percepções atuais. Assim, consegue considerar informações anteriores e situações que não observa diretamente.
- Exemplo: Um robô de limpeza guarda um mapa dos cômodos e registra quais áreas já percorreu.

### Agente baseado em objetivos

- Definição: Considera um objetivo antes de escolher a ação e avalia quais caminhos podem levar até ele. Pode comparar sequências de ações, em vez de apenas reagir ao que percebe no momento.
- Exemplo: Um navegador escolhe ruas que levam ao endereço informado pelo usuário.

### Agente baseado em utilidade

- Definição: Avalia os possíveis resultados por uma medida de utilidade e prefere a alternativa com melhor valor esperado. Isso ajuda quando há várias opções que atingem o objetivo, mas diferem em custo, risco ou qualidade.
- Exemplo: Um agente de compras compara preço, prazo de entrega e avaliação do vendedor para escolher a opção mais vantajosa.

### Agente com aprendizagem

- Definição: Usa a experiência para melhorar seu desempenho ao longo do tempo. Ele pode ajustar suas regras ou seu modelo a partir dos resultados das ações anteriores.
- Exemplo: Um sistema de recomendação aprende com os livros que o usuário consulta ou compra e passa a sugerir títulos mais adequados.

## Síntese com autômatos

Vou usar o cenário de compra de livros usados de inteligência artificial. Para simplificar, o agente tem três estados internos:

- **S0 — Buscando:** ainda está procurando anúncios compatíveis com o livro desejado.
- **S1 — Avaliando:** encontrou uma opção e está comparando edição, conservação, preço total e vendedor.
- **S2 — Pedido enviado:** encontrou uma opção que atende aos critérios e enviou a solicitação de compra.

As percepções consideradas são: **P1** — aparece um anúncio relevante; **P2** — o anúncio atende aos critérios de preço, edição e conservação; **P3** — o preço ou a condição do anúncio não é aceitável. As ações possíveis são: **A1** — abrir e guardar o anúncio; **A2** — enviar o pedido de compra; **A3** — descartar o anúncio e voltar à busca.

Regras de transição:

1. `S0 + P1 → S1, A1`: ao encontrar um anúncio relevante, o agente passa a avaliá-lo e guarda as informações para comparação.
2. `S1 + P2 → S2, A2`; `S1 + P3 → S0, A3`: se a opção atender aos critérios, o agente envia o pedido; se não atender, descarta o anúncio e volta à busca.

O estado interno representa informação passada porque guarda qual etapa já foi alcançada e os dados do anúncio que o agente encontrou. Sem esse registro, ele poderia repetir buscas ou esquecer por que uma opção foi selecionada. A limitação é que esse autômato é simples: não representa todos os anúncios, possíveis falhas de pagamento, cancelamentos, atrasos ou mudanças de preço. Em um sistema real, seriam necessários mais estados e regras.

## Referências

RUSSELL, Stuart; NORVIG, Peter. *Inteligência artificial*. 3. ed. Rio de Janeiro: Elsevier, 2013. Capítulo 2: Agentes inteligentes.

UDF. *Instruções gerais da atividade: agentes inteligentes*. Aula de Linguagens Formais e Autômatos, professora Kadidja Valéria, 20 out. 2026.
