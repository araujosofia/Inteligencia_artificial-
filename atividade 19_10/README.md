# Atividade 19/10

Aula 19/10/2026 | Professora Kadidja Valéria | Inteligência artificial

Disciplina: Inteligência Artificial, Linguagens Formais e Autômatos

Estudante: Sofia Araujo Rodrigues  | Turma: Eng. Software N1

Realize os exercícios 2.3, 2.4 e 2.5 do Capítulo 2 sobre agentes inteligentes. Analise a racionalidade, descreva ambientes de tarefa por meio do modelo PEAS e explique os conceitos com suas próprias palavras. Utilize o capítulo disponibilizado e justifique suas respostas.

## Exercício 2.3

### Para cada afirmação, diga se é verdadeira ou falsa e justifique com exemplo ou contraexemplo.

### a. Um agente que detecta apenas informações parciais sobre o estado não pode ser perfeitamente racional.

Falso. Racionalidade não exige onisciência. O agente racional escolhe a ação que maximiza o desempenho esperado com as percepções que recebeu. Ver só parte do estado limita o que ele sabe, mas não o impede de agir da melhor forma possível.

Contraexemplo: o aspirador da Figura 2.3 só percebe o próprio quadrado, e o livro afirma que ele é racional sob as hipóteses da Seção 2.2.1.

### b. Existem ambientes de tarefa nos quais nenhum agente reativo puro pode comportar-se racionalmente.

Verdadeiro. O agente reativo puro decide só pela percepção atual. Se a ação certa depender do histórico, nenhuma regra fixa acerta sempre.

Exemplo: mundo A/B com penalidade de 1 ponto por movimento. Ao perceber [A, Limpo], o agente deveria ir para B se ainda não o verificou, ou ficar parado se B já foi limpo. A mesma percepção exige ações diferentes, então só um agente com estado interno resolve.

### c. Existe um ambiente de tarefa em que todo agente é racional.

Verdadeiro. Se todas as ações têm o mesmo valor esperado de desempenho, qualquer escolha é ótima.

Exemplo: um ambiente onde só existe uma ação (NoOp), ou onde a medida de desempenho dá sempre a mesma pontuação.

### d. A entrada para o programa de agente é a mesma que a entrada para a função de agente.

Falso. A função de agente recebe a sequência inteira de percepções. O programa recebe só a percepção atual e, se precisar do histórico, tem de guardá-lo.

Exemplo: o AGENTE-DIRIGIDO-POR-TABELA (Figura 2.7) recebe a percepção atual e a anexa a uma variável “percepções”.

### e. Toda função de agente é implementável por uma combinação de programa/máquina.

Falso. Nem todo mapeamento é computável, e máquinas reais têm memória e tempo finitos.

Contraexemplo: uma função que recebe um programa e responde se ele para ou não (problema da parada). Ela está bem definida, mas nenhum programa a implementa. A tabela do táxi, com mais de 10^250.000.000.000 entradas, também não cabe em nenhuma máquina.

### f. Suponha que um agente selecione sua ação uniformemente ao acaso do conjunto de ações possíveis. Existe um ambiente de tarefa determinista em que esse agente é racional.

Verdadeiro. Agir ao acaso é racional quando todas as ações têm o mesmo valor.

Exemplo: mundo do aspirador com um único quadrado, sempre limpo e sem penalidade por movimento. Toda ação deixa tudo igual, então o agente aleatório tem pontuação máxima.

### g. É possível para um dado agente ser perfeitamente racional em dois ambientes de tarefa distintos.

Verdadeiro. O mesmo comportamento pode ser o melhor possível em mais de um ambiente.

Exemplo: o aspirador reativo da Figura 2.8 é racional no mundo A/B com sujeira desconhecida e também numa variação em que a sujeira começa sempre só em B.

### h. Todo agente é racional em um ambiente não observável.

Falso. Mesmo sem sensores, as ações têm consequências diferentes, e um agente pode escolher melhor que outro.

Contraexemplo: um aspirador sem sensores que executa [Aspirar, Direita, Aspirar, Esquerda, Aspirar] garante tudo limpo. Um agente que só faz Esquerda deixa B sujo e não é racional.

### i. Um agente jogador de pôquer perfeitamente racional nunca perde.

Falso. O pôquer é estocástico e parcialmente observável. Racionalidade maximiza o desempenho esperado, não o real.

Contraexemplo: com par de ases antes do flop, apostar tudo é a melhor jogada (vence cerca de 85% das vezes contra uma mão aleatória). Mesmo assim, o adversário pode completar uma sequência na última carta e o agente perde.

## Exercício 2.4

### Para cada atividade, identifique o agente, as hipóteses, o PEAS e classifique o ambiente.

### 1. Jogar futebol.

Agente e hipóteses: um jogador de linha, não a equipe, em partida oficial com regras da FIFA.

- P (desempenho): gols marcados e evitados, vitória, passes certos, sem faltas ou cartões.
- E (ambiente): campo, bola, traves, companheiros, adversários, árbitro, gramado e clima.
- A (atuadores): pernas e pés, cabeça, corpo, voz e gestos.
- S (sensores): visão, audição, propriocepção, tato.

**Classificação:**

- Parcialmente observável: não vê o campo todo nem as intenções dos outros.
- Multiagente cooperativo e competitivo: coopera com o time e compete com os adversários.
- Estocástico: quiques, escorregões e chutes imperfeitos.
- Sequencial: uma jogada muda as seguintes.
- Dinâmico: tudo se move enquanto ele decide.
- Contínuo: posições, velocidades e tempo variam continuamente.
- Conhecido: as regras e a física são conhecidas.

### 2. Explorar os oceanos subterrâneos de Titã.

Agente e hipóteses: robô submarino autônomo; comunicação com a Terra com cerca de 1h20 de atraso; energia limitada; nenhum outro agente presente.

- P: área mapeada, amostras e dados coletados e transmitidos, energia economizada, integridade do robô.
- E: oceano sob o gelo, correntes, pressão e frio extremos, relevo, sonda na superfície.
- A: propulsores, lemes, braço e amostradores, sonar, luzes, transmissor.
- S: câmeras, sonar, sensores de pressão, temperatura e química, unidade inercial, sensores de energia.

**Classificação:**

- Parcialmente observável: o oceano é escuro e vasto.
- Agente único: não há outros agentes, e a Terra não age em tempo real.
- Estocástico: correntes e falhas tornam os resultados incertos.
- Sequencial: a rota e a energia gastas agora limitam o futuro.
- Dinâmico: as correntes agem enquanto ele decide.
- Contínuo: posição, profundidade e propulsão são contínuas.
- Desconhecido: esse oceano nunca foi observado diretamente.

### 3. Comprar livros usados de IA na Internet.

Agente e hipóteses: softbot comprador, com orçamento definido e pagamento on-line autorizado.

- P: livros certos, menor preço com frete, estado conforme anunciado, prazo, reputação do vendedor, respeito ao orçamento.
- E: sites, vendedores, outros compradores, sistemas de pagamento e entrega.
- A: buscar, clicar, preencher formulários, mandar mensagens, pagar, mostrar resultados ao usuário.
- S: páginas web, preços, avaliações, e-mails de confirmação, preferências do usuário.

**Classificação:**

- Parcialmente observável: o estado real do livro não aparece no anúncio.
- Multiagente competitivo: outros compradores disputam os mesmos exemplares.
- Estocástico: anúncios somem e entregas atrasam.
- Sequencial: cada compra consome orçamento.
- Dinâmico: preços e estoque mudam enquanto ele compara.
- Discreto: cliques, páginas e preços em centavos.
- Conhecido: o funcionamento dos sites é conhecido.

### 4. Jogar uma partida de tênis.

Agente e hipóteses: um jogador, em jogo de simples com regras oficiais.

- P: pontos, games e sets vencidos, vitória, poucos erros não forçados.
- E: quadra, rede, bola, adversário, árbitro, vento.
- A: braços e raquete, pernas, corpo.
- S: visão, audição, propriocepção.

**Classificação:**

- Parcialmente observável: o efeito da bola e a intenção do adversário não são visíveis.
- Multiagente competitivo: o adversário tenta reduzir o seu desempenho.
- Estocástico: vento, quique e escolhas do adversário.
- Sequencial: um golpe define a posição do próximo.
- Dinâmico: a bola e o adversário se movem enquanto ele decide.
- Contínuo: posições, ângulos e tempo são contínuos.
- Conhecido: regras e física são conhecidas.

### 5. Praticar tênis contra uma parede.

Agente e hipóteses: o mesmo jogador; o objetivo é manter a bola em jogo e treinar os golpes.

- P: rebatidas seguidas sem erro, precisão em alvos na parede, regularidade.
- E: parede, chão, bola, vento.
- A: braços e raquete, pernas, corpo.
- S: visão, audição, propriocepção.

**Classificação:**

- Completamente observável (na prática): sem adversário, o que importa é a bola, que pode ser vista.
- Agente único: a parede não é agente, só reflete a bola.
- Estocástico: pequenas irregularidades e vento, bem menos que um adversário.
- Sequencial: a qualidade de um golpe define o retorno da bola.
- Dinâmico: a bola continua se movendo.
- Contínuo: movimentos e posições são contínuos.
- Conhecido: a física é conhecida.

### 6. Realizar um salto de altura.

Agente e hipóteses: o atleta durante uma tentativa; os outros atletas não interferem fisicamente.

- P: altura transposta, sarrafo não derrubado, poucas tentativas usadas, sem lesão.
- E: pista, sarrafo e postes, colchão, vento, juízes.
- A: pernas (corrida e impulsão), braços, tronco e quadril.
- S: visão, propriocepção e equilíbrio, tato no apoio.

**Classificação:**

- Completamente observável: sarrafo, pista e o próprio corpo são acessíveis.
- Agente único: os rivais só influenciam a classificação final.
- Estocástico: vento e variações na impulsão mudam o resultado.
- Sequencial: corrida → impulsão → trajetória.
- Dinâmico: não dá para pausar no meio do salto.
- Contínuo: velocidade, ângulo e altura são contínuos.
- Conhecido: regras e física são conhecidas.

### 7. Participar de um leilão de um item, realizando lances.

Agente e hipóteses: licitante de software, em leilão inglês on-line com incremento mínimo e prazo.

- P: arrematar o item, preço baixo em relação ao limite do usuário, nunca passar do limite.
- E: plataforma, item, sistema do leilão, outros licitantes, relógio.
- A: dar lance, aguardar, desistir, informar o usuário.
- S: lance atual, histórico de lances, tempo restante, limite do usuário.

**Classificação:**

- Parcialmente observável: os limites e estratégias dos rivais ficam ocultos.
- Multiagente competitivo: todos disputam o mesmo item.
- Determinístico, com incerteza apenas estratégica: as regras definem o efeito de cada lance; a incerteza vem só dos outros agentes.
- Sequencial: cada lance muda o preço e as reações dos rivais.
- Dinâmico: novos lances chegam e o relógio corre.
- Discreto: incrementos fixos e poucas ações possíveis.
- Conhecido: as regras do leilão são conhecidas.

### Conclusão: compare (1) tênis e parede; (2) as informações incompletas na compra de livros; (3) a influência de outros agentes no futebol e no leilão.

(1) Tênis × parede. Sem adversário, o ambiente vira de agente único, fica praticamente completamente observável e mais previsível, porque a parede não reage com estratégia. A medida de desempenho também muda: em vez de vencer pontos, o objetivo passa a ser regularidade e precisão.

(2) Livros usados. O agente não vê o estado real do livro nem a confiabilidade do vendedor. Por isso o ambiente é parcialmente observável e estocástico, e o agente racional precisa coletar informações antes de comprar, como ler avaliações e perguntar sobre a conservação.

(3) Futebol × leilão. Os dois são multiagente.

No futebol há cooperação e competição ao mesmo tempo, com interação física contínua.

No leilão a interação é só competitiva e segue regras discretas, então toda a incerteza é estratégica.

Em ambos, ser previsível pode ser explorado pelo oponente.

## Exercício 2.5

### Defina com suas próprias palavras e dê um exemplo.

### Agente.

Entidade que percebe o ambiente por sensores e age sobre ele por atuadores.

Ex.: robô aspirador com sensores de sujeira e motores.

### Função de agente.

Descrição abstrata que mapeia cada sequência de percepções em uma ação, como uma tabela.

Ex.: a tabela da Figura 2.3: [A, Sujo] → Aspirar.

### Programa de agente.

Implementação concreta da função, rodando numa arquitetura física. Recebe só a percepção atual. Agente = arquitetura + programa.

Ex.: o pseudocódigo da Figura 2.8 rodando no aspirador.

### Racionalidade.

Escolher a ação que maximiza o desempenho esperado, dadas as percepções, o conhecimento prévio e as ações possíveis. Não é onisciência nem garantia de sucesso.

Ex.: atravessar a rua depois de olhar para os dois lados é racional, mesmo que algo improvável cause um acidente.

### Autonomia.

Capacidade de basear o comportamento na própria experiência e aprender, em vez de depender só do projetista.

Ex.: aspirador que aprende que a cozinha suja mais após o jantar. A vespa Sphex, que repete o plano mesmo quando ele falha, é o oposto.

### Agente reativo.

Escolhe a ação só pela percepção atual, com regras condição-ação e sem memória. Funciona bem em ambientes completamente observáveis.

Ex.: “se o carro da frente frear, então frear”; um termostato.

### Agente baseado em modelo.

Mantém um estado interno, atualizado por um modelo de como o mundo evolui e do que suas ações fazem.

Ex.: táxi que lembra do carro no ponto cego antes de trocar de faixa.

### Agente baseado em objetivos.

Tem objetivos explícitos e planeja ações pensando no futuro.

Ex.: GPS que calcula a rota até o destino; trocar o destino muda o comportamento sem reescrever regras.

### Agente baseado em utilidade.

Usa uma função utilidade para medir o quanto cada estado é bom e escolhe a ação de maior utilidade esperada. Isso permite equilibrar objetivos conflitantes e pesar riscos.

Ex.: app de rotas que pondera tempo, pedágio, segurança e trânsito.

### Agente com aprendizagem.

Melhora com a experiência. Tem quatro partes: elemento de desempenho, crítico, elemento de aprendizado e gerador de problemas.

Ex.: filtro de spam que ajusta suas regras quando o usuário marca e-mails como spam.

## Síntese com autômatos

### Escolha um caso do exercício 2.4. Descreva três estados internos, três percepções, três ações e duas regras no formato estado atual + percepção → próximo estado e ação. Explique como o estado interno representa informação passada e cite uma limitação.

Caso escolhido: leilão, com limite L definido pelo usuário.

**Estados internos:**

- Q0 = Aguardando
- Q1 = Liderando
- Q2 = Encerrado/Desistiu

**Percepções:**

- p1 = lance rival + incremento ≤ L
- p2 = lance rival + incremento > L
- p3 = leilão encerrado

**Ações:**

- a1 = dar lance
- a2 = aguardar
- a3 = desistir

**Regras:**

- Regra 1: Q1 + p1 → Q1, a1 (cobre o lance e volta a liderar).
- Regra 2: Q1 + p2 → Q2, a3 (o preço passou do limite, então desiste).

**Informação passada:** a percepção mostra só o último lance. O estado Q1 resume o histórico (“meu lance ainda é o maior”), e o Q2 guarda que o limite já foi ultrapassado.

**Limitação:** o agente não guarda os lances dos rivais nem estima o limite deles, ignora o tempo restante e trata L como fixo. Por isso pode pagar mais do que o necessário.

**Referência:** RUSSELL, S.; NORVIG, P. Inteligência Artificial. 3. ed. Rio de Janeiro: Elsevier, 2013. Cap. 2.
