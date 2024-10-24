# Classificação de Persuasão em Textos de Memes: Uma Abordagem Baseada em Engenharia de Características

## Monografia apresentada à Escola Nacional de Ciências Estatísticas do Instituto Brasileiro de Geografia e Estatística, como requisito parcial à obtenção do título de Bacharel em Estatística, sob orientação do Prof. Eduardo Corrêa Gonçalves.

O conteúdo apresentado neste `README.md` trata-se de um resumo do trabalho. O trabalho completo pode ser acessado neste mesmo repositório.

### Resumo

A propaganda visa influenciar a opinião pública para promover uma agenda específica,
incentivando opiniões contrárias ou a favor. Para isso, emprega técnicas de persuasão,
utilizando uma comunicação direcionada a moldar a opinião de quem recebe a informação,
podendo ser disseminada por diversos meios. Paralelamente, nas redes sociais, os
memes se mostram como uma poderosa ferramenta comunicativa, capazes de se espalhar
rapidamente e atingir um grande número de pessoas. Assim, os memes podem ser um
veículo eficaz para a disseminação de propaganda. Na literatura, já existem estudos sobre
a detecção computacional de propaganda em textos de artigos. No entanto, apenas recentemente
os pesquisadores começaram a investigar a classificação de persuasão em memes,
que representa ambiente mais desafiador. Este trabalho aborda a classificação de persuasão
em textos de memes, utilizando algoritmos de aprendizado de máquina. A abordagem
é baseada na engenharia de características, uma estratégia usada para transformar texto
(dado não estruturado) em um formato adequado para os algoritmos de classificação.
Serão utilizados modelos de árvore de decisão, floresta aleatória e regressão logística.

Palavras-chaves: `Persuasão.` `Propaganda.` `Meme.` `Classificação.` `Engenharia de Características.`
`Processamento de Linguagem Natural.` `Aprendizado de Máquina.`

### Introdução

Nos últimos anos, os memes emergiram como uma forma peculiar e poderosa de
comunicação na era digital. Embora popularizados no ambiente online, é difícil precisar
com rigor o momento em que conteúdos que circulam na internet passaram a ser reconhecidos
como memes (CHAGAS, 2021). Sabe-se que nos anos 90, tornou-se corriqueiro
traduzir memes como piadas e outras formas virais que ganhavam rápido alcance em
fóruns de discussão online e newgroups. Na era da internet, esses elementos de mídia compartilhável
têm a habilidade de se espalhar rapidamente pelo mundo através da interação
social (WANG; WOOD, 2011) e, hoje, se encontram quase que onipresentes nas redes
sociais. Desde um ambiente de humor até a manifestação política, sua natureza altamente
compartilhável e adaptável os torna ideais para o ambiente dinâmico das redes sociais, se
destacando pela sua capacidade de atrair e envolver as pessoas (CHAGAS, 2021).

De acordo com Merriam-Webster (2023), o fenômeno tem origem ainda na década
de 70. A palavra "meme"foi cunhada em 1976 pelo renomado biólogo britânico Richard
Dawkins em seu livro "The Selfish Gene". Dawkins introduziu o termo como uma unidade
cultural que se replica e se transmite de pessoa para pessoa por meio da imitação, semelhante
ao conceito de gene na biologia. Ele derivou a palavra "meme"do grego "mimema",
que significa "algo imitado". Dawkins usou os memes como uma forma de explicar como
ideias, comportamentos, rituais e outras formas de cultura são transmitidas e evoluem ao
longo do tempo (DAWKINS, 1976). Segundo Dawkins, exemplos de memes são melodias,
ideias, frases de efeito e até mesmo moda, argumentando que, assim como genes, os memes
competem entre si pela atenção e reprodução, e aqueles que são mais adaptáveis e
atraentes têm mais chances de se espalhar e sobreviver.

Desde então, o conceito de meme expandiu-se para além do domínio da biologia,
tornando-se uma parte fundamental da cultura digital contemporânea, onde memes são
compartilhados e adaptados em uma escala global. Em uma analogia com a biologia,
memes podem ser unidades culturais que se propagam e se adaptam por meio do compartilhamento
online. Plataformas como Instagram, Facebook, TikTok, Reddit e X (antigo
Twitter) servem como espaços de criação, compartilhamento e discussão de memes.

No entanto, por trás de sua aparente trivialidade, os memes não apenas podem
refletir os interesses e preocupações de uma geração conectada, mas também podem ser
utilizados como campanhas de influência por parte de governos (ZAKEM; MCBRIDE;
HAMMERBERG, 2021), o que pode impactar ativamente a maneira como percebemos e
interpretamos o mundo ao nosso redor. Desde comentários sociais até críticas políticas, os
memes se tornaram uma importante ferramenta para a expressão (MIHAILIDIS, 2020), podendo assumir a capacidade de moldar opiniões.

Essa mesma capacidade dos memes de influenciar as percepções e opiniões pode ser
manipulada para espalhar desinformação e propaganda, através de técnicas de persuasão.
Propagandas possuem o objetivo de influenciar a opinião das pessoas com o propósito de
expandir uma agenda específica (MARTINO et al., 2020). Com o rápido compartilhamento
e disseminação dos memes nas redes sociais, tornou-se cada vez mais fácil para indivíduos
e grupos com interesses específicos explorarem essa forma de comunicação para promover
agendas políticas, disseminar teorias da conspiração e distorcer fatos. A natureza rápida
e concisa dos memes pode simplificar questões complexas e levar a uma compreensão
superficial ou distorcida de eventos e questões importantes. Além disso, a viralidade dos
memes pode amplificar mensagens enganosas ou prejudiciais, aumentando sua influência
e impacto.

Diferentes técnicas de persuasão podem ser aplicadas em memes, aproveitando sua
capacidade de transmitir mensagens de forma rápida e eficaz. O uso de falácias lógicas,
com o uso de humor e ironia, pode tornar uma mensagem mais cativante e persuasiva, ao
mesmo tempo em que tenta suavizar possíveis resistências do público-alvo. Por exemplo,
a Figura 1 ilustra um meme, em inglês, que retrata a congressista americana Ilhan Omar
junto ao ex-presidente dos Estados Unidos, Donald Trump. Neste meme, a associação é
feita entre a expressão de desgosto em relação ao ex-presidente e o terrorismo.

Este trabalho pretende utilizar técnicas de Processamento de Linguagem Natural
(PLN) para criar um sistema capaz de classificar um meme como normal ou persuasivo
unicamente em função de seu texto. O Processamento de Linguagem Natural é um
campo de pesquisa que tem como objetivo investigar e propor métodos e sistemas de
processamento computacional da linguagem humana (CASELI; NUNES, 2024). Ele funciona
como como uma interseção entre ciência da computação, inteligência artificial e
linguística computacional, oferecendo as ferramentas necessárias para os computadores
entenderem a nossa linguagem (LOPEZ; KALITA, 2017). O trabalho empregará uma
abordagem baseada em engenharia de características (feature engineering), que consiste
na transformação dos textos dos memes (dados brutos) em vetores numéricos que são
exigidos pelos algoritmos de classificação (NARGESIAN et al., 2017; ZHENG; CASARI,
2018).

<img src="https://github.com/user-attachments/assets/d14d8118-ddfb-4940-8835-e0bb83ec86f9" alt="Figura 1" width="400"/>

#### Justificativa

A utilização de técnicas de persuasão em memes é um problema do mundo moderno,
visto que pode levar a propagação de desinformação e influenciar a percepção do
público sobre diversos assuntos através de mídias sociais na internet. Como este problema
é relativamente novo, ainda há uma carência de estudos sobre o tema. Embora existam
pesquisas focadas na identificação de propaganda em textos de artigos (CRUZ; ROCHA;
CARDOSO, 2019; MARTINO; BARRÓN-CEDEÑO; NAKOV, 2019), apenas recentemente
os pesquisadores começaram a investigar e estudar a classificação e detecção de propaganda em textos de memes. Trata-se de um problema importante e relevante, dado
o vasto alcance e a rápida disseminação que os memes podem atingir.

#### Objetivos

O objetivo deste trabalho é criar um sistema de classificação de textos curtos,
especificamente aplicado à análise de textos de memes, de forma a classificar se o conteúdo
do texto é persuasivo ou não. Ao desenvolver um sistema capaz de identificar de forma
eficaz a presença de propaganda em memes, este trabalho poderá fornecer um material
para pesquisas futuras sobre o tema. A classificação em textos de memes se encontra
em um contexto desafiador, visto que os textos tendem a ser muito curtos e informais,
podendo empregar linguagem coloquial e referências culturais. Com o objetivo de tentar
a compreensão sobre o tema, este trabalho terá como foco o uso de técnicas de engenharia
de características e de algoritmos capazes de gerar modelos interpretáveis (FREITAS,
2014), isto é, modelos que possuem a habilidade de “explicar” as suas classificações para
os usuários. Mais especificamente, os algoritmos de classificação utilizados nesse trabalho
são Árvore de Decisão CART (BREIMAN et al., 1984), Regressão Logística (JURAFSKY;
MARTIN, 2024a) e Floresta Aleatória (Random Forest)1 (BREIMAN, 2001).

### Base de Dados

O trabalho utilizará a base de dados fornecida na competição SemEval 2024 (SemEval,
2024). Nesta competição, diversas equipes competem entre si com o objetivo de
construir modelos para identificar as diferentes técnicas de persuasão que podem estar
sendo utilizadas ou não nos textos dos memes. As equipes tiveram seus desempenhos
medidos através de métricas avaliativas, tais como o F1-Score (JURAFSKY; MARTIN,
2024c). A competição, iniciada nos últimos meses de 2023 e finalizada em 2024 foi organizada
por pesquisadores da Itália, França, Bulgária, Emirados Árabes Unidos e Catar. Até
o momento do desenvolvimento deste trabalho, não havia sido publicado nenhum artigo
elaborado por membros das equipes participantes da competição.

A base de dados fornecida pela organização da competição foi dividida em três
conjuntos distintos: treino, validação e teste. Cada conjunto de dados possui as seguintes
variáveis: "id"(identificador único para cada observação), "text" (texto do meme), "labels"
(classificações relacionadas aos métodos de persuasão presentes no texto, ou indicando
a ausência deles) e "link" (link para abrir a imagem do meme). A coluna “labels” pode
estar rotulada com mais de uma classificação de persuasão diferente ao mesmo tempo.
Essa estruturação dos dados permite uma análise detalhada e sistemática dos textos,
auxiliando a construção e avaliação de modelos de classificação.

A base de treino possui 7.000 observações e será usada nesse trabalho para treinar
diferentes modelos de classificação. A base de validação possui 500 observações e foi utilizada
pelos competidores em um estágio preliminar da competição. Ela não será utilizada
no presente TCC. Já a base de teste possui 1.000 observações e será utilizada para estimar
o desempenho preditivo dos modelos, onde serão verificadas as medidas de acurácia,
precisão, recall e F1-Score (JURAFSKY; MARTIN, 2024c).

### Classificação das Técnicas de Persuasão

De acordo com os organizadores da competição SemEval 2024, há 20 técnicas de
persuasão distintas que podem ser aplicadas em textos. Essas técnicas podem ser aplicadas
de forma isolada ou em conjunto com outras de forma simultânea. As técnicas podem ser encontradas [neste link](https://propaganda.math.unipd.it/semeval2024task4/definitions.html).

### Análise Exploratória

Cada observação de cada uma das três bases está rotulada com as técnicas de
persuasão que estão sendo utilizadas no texto do meme, caso
o texto tenha conteúdo persuasivo. A base de treino possui todas as 20 técnicas em seus
textos. A Figura 2 exibe a frequência de cada técnica na base de treino. No total, as
técnicas foram empregadas 11.290 vezes.

![Figura 2 v2](https://github.com/user-attachments/assets/f134b354-b916-43ab-bf97-2f9bad24db99)

A técnica Smears destaca-se como a principal estratégia de persuasão adotada
nos memes, respondendo por 17,63% de todas as técnicas utilizadas. Em seguida, a técnica
Loaded Language ocupa a posição de segunda mais frequente, representando 15,50%
do total. Por sua vez, a técnica Name calling/Labeling figura como a terceira mais prevalente,
com uma representatividade de 13,45%. Quanto à técnica de persuasão com a
menor incidência na base de dados, observa-se que é a Obfuscation, Intentional vagueness,
Confusion, registrando apenas 0,19% do total.

Cada texto pode ser rotulado com diferentes técnicas de persuasão simultaneamente.
Dentro do conjunto de observações da base de treinamento, 3.274 foram identificadas
com duas ou mais técnicas, enquanto 2.462 foram rotuladas com apenas uma
técnica. Além disso, há 1.263 textos na base que não apresentam nenhuma técnica de persuasão
em seu conteúdo. A Figura 4 a seguir ilustra a distribuição do número de textos
em relação ao total de técnicas aplicadas.

![Figura4 (Gráfico 2)](https://github.com/user-attachments/assets/c8ca6ddf-249a-48a8-bb85-a041b153ae70)

Uma análise da distribuição das palavras presentes nos textos dos memes também pode ajudar a entender o comportamento de conteúdo persuasivo e não persuasivo. Como
a base possui uma alta quantidade de observações e, por consequência, uma alta quantidade
de palavras, uma nuvem de palavras pode ilustrar a importância e frequência das
palavras na base. Para isso, foram desconsideradas as stopwords, que são palavras que não
vão trazer informação de fato sobre o conteúdo presente, tais como artigos e pronomes
(MOREIRA, 2023). A Figura 5 a seguir exibe a nuvem de palavras de toda a base.

![Figura5 nuvem de palavras - base total](https://github.com/user-attachments/assets/ec0e0150-fa0a-465f-b540-ed9c702c9d2d)

De acordo com a nuvem de palavras para a base inteira, temos o destaque das
palavras “Trump”, “president”, “people” e “America”. São palavras que podem indicar a
forte presença de conteúdo político na base. Ainda é possível ver mais termos relacionados
à política, ainda com uma frequência superior à outras palavras da base, tais como
“Biden”, “Obama”, “vote”, “Democrat”, “Republican”, “government”, “Russia”, “Putin”,
entre outras.

Em uma análise mais detalhada, podemos também analisar as nuvens de palavras
exclusivamente para textos classificados como propaganda e para textos classificados
como não-propaganda, a fim de tentar identificar possíveis diferenças entre elas. A Figura
6 a seguir exibe a nuvem de palavras para os memes que foram rotulados como
não-propaganda, ou seja, onde não há técnicas de persuasão sendo aplicadas.

![Figura6 nuvem de palavras - não-propaganda](https://github.com/user-attachments/assets/3992f247-4c76-4fc9-ad91-0cb56ee63810)

A presença de conteúdo politico também dá indícios de ser forte, conforme a nuvem
de palavras para os memes classificados como não-propaganda. Palavras como “Trump”,
“President”, “Ukraine”, “Russia” e “Biden” se destacam. A maior diferença aparente em
relação à base total é o crescimento da palavra “Ukraine”, se referindo ao país da Ucrânia.

De forma a expandir a análise, a Figura 7 exibe a nuvem de palavras para os
memes rotulados como propaganda, ou seja, com conteúdo persuasivo.

Novamente vemos uma forte presença de conteúdo político, com palavras como
“Trump”, “America”, “people”, “president”, “government”, “country”, entre outros. Entretanto,
diferente do que ocorre com os textos que não são propaganda, é possível identificar
xingamentos e palavrões neste caso, ainda que em frequência menor do que as
palavras de maior destaque. Palavras relacionadas à violência e atos violentos também podem ser identificadas.

![Figura7 nuvem de palavras - propaganda](https://github.com/user-attachments/assets/83805aad-7f9b-4c8f-8801-6883364a9b01)

### Metodologia

O processo de construção do sistema para detecção de persuasão proposto nesse
trabalho é composto por 5 etapas:

* Pré-processamento.
* Engenharia de Características.
* Balanceamento da base de treino.
* Treinamento do modelo.
* Teste e avaliação do modelo.

#### Pré-processamento

Em um primeiro momento, foi realizado o pré-processamento dos textos das bases
de treino e teste. O passo inicial foi a remoção das `stopwords` utilizando a biblioteca
`spaCy` do Python. Para a língua inglesa, a biblioteca `spaCy` considera uma lista de
326 palavras como stopwords. A remoção dessas palavras auxilia na análise exploratória da
base e na criação de atributos, pois são termos que podem aparecer com alta frequência,
mas não fornecem informações relevantes sobre o conteúdo do texto.

Em seguida, foi realizada a `lematização` das palavras. A `lematização` é uma forma
de normalização das palavras, as convertendo para uma forma padrão (FINATTO et al.,
2024). As frases “eu corro” e “eles correm”, por exemplo, passariam a ser “eu correr” e
“eles correr”, respectivamente. Da mesma forma, isto foi feito para os textos dos memes,
em inglês, das bases de treino e teste. A lematização é útil para converter formas variantes
das palavras (plural, feminino, gerúndio, etc.) para uma representação única e concisa.

Por fim, o processo de `tokenização` foi utilizado para transformar cada texto em
um vetor de palavras. A `tokenização` envolve a separação do texto em unidades linguísticas
mínimas (`tokens`), separando as palavras por meio de delimitadores (FINATTO et
al., 2024). Neste trabalho, os espaços e os sinais de pontuação foram utilizados como
delimitadores.

De forma ilustrativa, apresenta-se a seguir um exemplo do processo de remoção de
`stopwords`, `lematização` e `tokenização`. Considere a seguinte frase: `O gato pulou alto!`. O
seu pré-processamento se daria da seguinte forma:

* Remoção das `stopwords`, resultando na frase: `gato pulou alto!`.
* `Lematização`, resultando na frase: `gato pular alto!`.
* `Tokenização`, resultando no vetor: `[“gato”, “pular”, “alto”, “!”]`.

#### Engenharia de Características

Para obter atributos numéricos a partir dos dados textuais, foi empregada a `engenharia
de características`. A `engenharia de características` é o ato de extração de atributos
dos dados brutos e a transformação desses atributos em formatos adequados, como vetores
numéricos, necessários para os algoritmos de aprendizado de máquina (NARGESIAN et
al., 2017; ZHENG; CASARI, 2018).

De forma a obter-se um vetor numérico representativo do texto do meme, foram
considerados os seguintes atributos utilizados por Cruz, Rocha e Cardoso (2019), que
foram adaptados para o contexto do problema e extraídos para o texto de cada meme da
base de treino:

* Número total de frases: representa o total de frases do texto do meme.
*  Média de caracteres por frase: representa a média de caracteres por frase do texto
do meme, onde cada frase é delimitada por ponto final, ponto de exclamação ou
ponto de interrogação.
* Variância de caracteres por frase: representa a variância de caracteres por frase do
texto do meme, utilizando a mesma delimitação de frase do atributo (2).
* Total de caracteres: representa o total de caracteres presente em todo o texto do
meme.
* Média de caracteres por palavra: representa a média de caracteres por palavra do
texto do meme.
* Variância de caracteres por palavra: representa a variância de caracteres por palavra
do texto do meme.
* Frequência de pontuação: representa a frequência absoluta de todos os símbolos de
pontuação presentes no texto do meme.
* Frequência de letras maiúsculas: representa a frequência absoluta de todas as letras
maiúsculas presentes no texto do meme.
* Proporção de token sobre palavras lematizadas: representa o total de palavras lematizadas
dividido pelo total de tokens do texto do meme (“andou” e “andei” são
dois tokens diferentes, mas ao serem lematizados, ambos se tornam “andar”).
* TF-IDF.

De forma ilustrativa, considere o seguinte texto, em português, para passar pelo
processo de extração de atributos numéricos através da engenharia de características:

`As Olimpíadas chegaram! Os atletas acabam de chegar em Paris para a maior
competição esportiva do mundo. O Time Brasil está preparado? De acordo com os
atletas, eles estão!`

Considerando as variáveis apresentadas previamente (desconsiderando o TF-IDF),
temos os seguintes atributos numéricos extraídos:

* Número total de frases: 4.
* Média de caracteres por frase: 42,25.
* Variância de caracteres por frase: 499,69.
* Total de caracteres: 172.
* Média de caracteres por palavra: 4,79.
* Variância de caracteres por palavra: 7,06.
* Frequência de pontuação: 5.
* Frequência de letras maiúsculas: 8.
* Proporção de tokens sobre palavras lematizadas: 0,74.

Analisando o atributo `Proporção de tokens sobre palavras lematizadas`, de mais complexo entendimento que os outros, podemos
detalhar seu processo de cálculo. Os `tokens` gerados para o texto formam o seguinte vetor
de palavras e pontuações:

`["As", "Olimpíadas", "chegaram", "!", "Os", "atletas", "acabam", "de", "chegar", "em",
"Paris", "para", "a", "maior", "competição", "esportiva", "do", "mundo", ".", "O", "Time",
"Brasil", "está", "preparado", "?", "De", "acordo", "com", "os", "atletas", ",", "eles",
"estão", "!"]`

Este vetor tem o total de 34 elementos. O próximo passo consiste em gerar um
vetor com as palavras lematizadas, que resulta no seguinte vetor de palavras e pontuações:

`[’!’, ’,’, ’.’, ’?’, ’Brasil’, ’Olimpíadas’, ’Paris’, ’Time’, ’acabar’, ’acordo’, ’atleta’,
’chegar’, ’com’, ’competição’, ’de’, ’de o’, ’ele’, ’em’, ’esportivo’, ’estar’, ’grande’,
’mundo’, ’o’, ’para’, ’preparado’]`

No vetor lematizado há um total de 25 elementos. Neste caso, não há repetições.
Desta forma, o atributo é calculado por 25/34, resultado no valor de 0,74.

#### TF-IDF

Uma das formas a ser utilizada para a extração de atributos a partir do conteúdo
dos textos será a `Matriz Documento-Termo (Document-Term Matrix - DTM)` com pesos
`TF-IDF`. Para explicar o `TF-IDF`, será apresentado um exemplo de como essa medida
é usada no contexto de busca de documentos na Internet. Para ordenar documentos em
resposta à uma consulta realizada, há duas premissas que podem ser utilizadas:

* Documentos que contém mais vezes os termos da consulta terão mais chances de
serem relacionados a ela e, então, serem relevantes.
* Os termos mais raros na coleção de documentos são úteis para a diferenciação de
conteúdo nos documentos (MOREIRA, 2023).

Por exemplo, se uma pessoa decide pesquisar sobre artigos de notícias do cenário
político nos EUA em um corpus de documentos (um site de notícias, por exemplo), alguns
termos serão mais relevantes que outros. Palavras como “Biden” ou “Casa Branca” serão
termos úteis para a pesquisa, enquanto termos como “basquete” ou “previsão do tempo”
já não terão tanta utilidade.

O `TF-IDF` e a `DTM` são usados não apenas para recuperação da informação (busca
de documentos), mas também em problemas de classificação. Na `DTM`, cada linha representa
um documento em uma coleção de documentos e cada coluna representa uma palavra
ou grupo de palavras, onde cada célula da matriz representa o peso do termo no documento
(JURAFSKY; MARTIN, 2024e). Para atribuir pesos aos termos em relação aos documentos,
é muito comum utilizar a medida `TF-IDF`, onde `TF` significa “term-frequency”
(frequência do termo) e `IDF` significa “inverse document-frequency” (frequência inversa do
termo) (MOREIRA, 2023). A medida `TF-IDF` é, então, o produto de `TF` e `IDF`. 

O cálculo dos pesos `TF-IDF` foi realizado utilizando a biblioteca `Scikit-learn`, no
`Python`. A biblioteca calcula o termo `TF(𝑡,𝑑)` como sendo a frequência absoluta em que o
termo 𝑡 aparece no documento 𝑑. O componente `IDF` tem o objetivo de dar um peso maior aos termos mais raros,
pois eles são úteis para discriminar o conteúdo dos documentos (MOREIRA, 2023). Portanto,
quanto mais raro o termo for no corpus, maior será o valor `IDF`.

Neste trabalho, cada documento corresponde a um texto de meme, e o corpus é
composto pelo conjunto de todos os textos de memes presentes na base de dados. Nos
experimentos, os termos serão representados de duas formas distintas:

* Os `50 unigramas` mais frequentes.
* Os `50 bigramas` mais frequentes.

Os `unigramas` e `bigramas` são dois exemplos de `n-gramas`. O `n-grama` é uma sequência
de n palavras (JURAFSKY; MARTIN, 2024b). Portanto, o `unigrama` é uma sequência
de uma palavra e o `bigrama` é uma sequência de duas palavras.

#### Balanceamento da Base

Bases desbalanceadas podem levar o modelo a favorecer previsões na classe majoritária (CRUZ; ROCHA; CARDOSO, 2019). Como a base de treino contém 78% de suas observações
classificadas como propaganda, tem-se um caso em que os modelos podem favorecer a
previsão dos textos da base de teste dessa forma. Portanto, com o objetivo de retirar
essa tendência de classificação, serão aplicadas duas formas distintas de balanceamento:
`undersampling` e `oversampling`.

Ao se utilizar dados do mundo real, classes desbalanceadas podem ser esperadas.
Se o grau de desbalanceamento dos dados para a classe majoritária for algo extremo então
o classificador pode produzir uma alta acurácia na previsão, dado que o modelo prevê a
maioria das instâncias como pertencentes à classe majoritária (LEEVY et al., 2018).

O método `undersampling` consiste na redução da quantidade de observações da
classe majoritária. A forma mais popular para a aplicação de `undersampling`, que também
será utilizada neste trabalho, é o `undersampling` aleatório. O método consiste em remover
observações da classe majoritária, aleatoriamente, até que a base de dados alcance o
balanceamento entre as classes.

Por outro lado, o método `oversampling` consiste na geração de novas amostras
de observações pertencentes à classe minoritária. A forma mais comum de utilização
do método, que também será utilizada nesse trabalho, é através da geração de novas
observações a partir de uma amostragem com reposição da classe minoritária. Desta
forma, observações aleatórias da classe minoritária são replicadas na base até que se
tenha o balanceamento entre as classes.

Os dois métodos de balanceamento serão aplicados na base de treino, de forma a
balancear as classes para tentar obter um melhor desempenho dos modelos de classificação.
Resultados empíricos de trabalhos relevantes apontam que o método de `oversampling`
aleatório alcança melhores resultados do que o método de `undersampling` aleatório (LEEVY
et al., 2018).

#### Técnicas de Classificação

##### Árvores de Decisão


