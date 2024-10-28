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

As `árvores de decisão` são um método aprendizado não paramétrico usado para
classificação e regressão. De acordo com a biblioteca `Scikit-learn`, o objetivo é criar um
modelo que preveja o valor de uma variável alvo, aprendendo regras de decisão simples
inferidas a partir dos dados. Uma vantagem deste algoritmo é a facilidade na sua interpretação.

As `árvores de decisão` são construídas através da análise de uma base de treino, no
qual a classificação de cada observação é conhecida, sendo utilizada posteriormente para
classificar dados novos e desconhecidos (KINGSFORD; SALZBERG, 2008).

De acordo com Ali et al. (2012), a ideia do algoritmo veio a partir da estrutura de
uma árvore real, que é composta por raiz e nós, sendo que os nós seriam as ramificações
e os locais onde elas se dividem. A árvore de decisão, então, é construída a partir dos nós
e os ramos são representados pelos segmentos que conectam os nós. Ela começa da raiz e se move para baixo. O nó onde as ramificações se encerram é conhecido como folha.
Cada nó representa uma certa característica enquanto os ramos representam uma gama
de valores. A Figura a seguir apresenta um exemplo de uma `Árvore de Decisão` que
classifica um cliente como possível comprador de carro importado com base em sua renda
e idade (SILVA; GONÇALVES, 2021).

![Figura8 Exemplo_AD](https://github.com/user-attachments/assets/2f4adf59-69d1-4b7a-90c2-6a3755d7b851)

Uma `Árvore de Decisão` é formada por um conjunto de regras de classificação,
uma vez que existe sempre um único caminho da raiz para cada folha, onde o caminho
representa uma expressão lógica da regra utilizada para classificar um objeto (SILVA;
GONÇALVES, 2021). Por exemplo, as regras da Figura anterior para classificar o cliente como
possível comprador de carro importado são:

* SE (renda = “alta”), ENTÃO (possível comprador = “sim”).
* SE (renda = “média”) e (idade > 30), ENTÃO (possível comprador = “sim”).

O algoritmo `CART` (BREIMAN et al., 1984) é um dos mais populares para a
geração de árvore de decisão. Este algoritmo realiza a decisão de como dividir a árvore 
através do `Índice de Gini`, que será utilizado para montar a árvore através de decisões
binárias. Portanto, cada nó gerado terá duas ramificações.

Como o algoritmo `CART` realiza apenas divisões binárias em cada nó, sempre serão
feitas divisões que resultem em duas ramificações (BREIMAN et al., 1984). Suponha que
um atributo preditivo “tempo” tenha as seguintes classificações possíveis: sol, chuva e
nublado. Neste caso, o algoritmo `CART` faria partições da seguinte forma: {sol, chuva},
{sol, nublado}, {chuva, nublado}, {sol}, {chuva} e {nublado}. Então, seria calculado o
`Índice de Gini` para cada combinação possível entre as repartições. Dessa forma, é feita a
soma ponderada de cada partição.

#### Floresta Aleatória (Random Forest)

O método `Floresta Aleatória` é uma combinação de árvores de decisão em que
cada árvore depende de valores de um vetor aleatório amostrado, em que os vetores são
independentes e identicamente distribuídos, sendo que o k-ésimo vetor gerado governa a
k-ésima árvore de decisão (BREIMAN, 2001).

Segundo descrito por Ali et al. (2012), cada árvore é gerada a partir dos seguintes
passos:

* Gerando uma amostra aleatória com reposição e de tamanho 𝑁, se o número de
casos na base de treinamento for igual a 𝑁, da base de dados. Essa amostra é
usada como treinamento para a árvore de decisão.
* Sendo 𝑑 o valor total de atributos preditivos, 𝑚 atributos são selecionados aleatoriamente
de 𝑑, sendo que 𝑚 ≪ 𝑑. A melhor divisão dos 𝑚 atributos selecionados
é utilizada para a divisão do nó. Durante o processo de geração de árvores aleatórias,
o valor de 𝑚 é constante.
* Cada árvore gerada cresce o máximo possível.

#### Regressão Logística

A `Regressão Logística` é um classificador probabilístico, sendo uma das ferramentas
analíticas mais importantes das ciências sociais e naturais (JURAFSKY; MARTIN,
2024a). No `Processamento de Linguagem Natural`, ela é o algoritmo de aprendizado de máquina
supervisionado básico para classificação e também tem uma relação muito próxima
com redes neurais (JURAFSKY; MARTIN, 2024a).

Conforme Jurafsky e Martin (2024a) destacam, o principal propósito da regressão
logística binária reside em tornar um classificador capaz de tomar uma decisão dicotômica
sobre a classe de uma nova observação. Para isso, temos o conjunto 𝑋 = {𝑋1,𝑋2, . . . ,𝑋𝑑}
de atributos numéricos para cada observação 𝑥, sendo que o output 𝑦 do classificador será
igual a 1 quando a observação for classificada como parte da classe e 0 caso contrário.
Neste trabalho, foi definido que o valor 1 significa texto com persuasão e 0 significa texto
sem persuasão. Queremos saber a probabilidade condicional 𝑝(𝑦 = 1|𝑥). Caso essa seja
maior que 0,5, então teremos a classificação 𝑦 = 1 e, caso contrário, 𝑦 = 0.

Ainda segundo Jurafsky e Martin (2024), a `regressão logística` resolve essa tarefa
aprendendo um vetor de pesos (coeficientes) e um termo de viés (intercepto). Cada peso
𝑤𝑖 é um número real associado ao atributo preditivo 𝑋𝑖. Então, para tomar uma decisão,
primeiro multiplica-se cada 𝑋𝑖 pelo peso 𝑤𝑖, soma-se o resultado e adiciona-se o termo de
viés 𝑏, resultando em um valor 𝑧 que expressa a soma ponderada para a classe.

O vetor de pesos w vai indicar o quão importante cada atributo é para a classificação.
O valor 𝑧 também pode ser representado pelo produto escalar dos vetores w e
X. O produto escalar de dois vetores a e b pode ser escrito como a · b e será a soma
dos produtos dos elementos correspondentes de cada vetor.

Para representar 𝑧 como uma probabilidade, a função `sigmoide` (também chamada
de função logística), apresentada na Figura a seguir, é introduzida e apresentada graficamente, de forma a termos valores entre 0 e 1. Como cada um dos pesos possuem
valores reais, o valor de 𝑧 na pode variar de −∞ até +∞.

![Figura9 funcao sigmoide](https://github.com/user-attachments/assets/8a2e4316-f28e-4251-856f-c85315c43f07)

O processo de treinamento da regressão logística envolve uma função objetiva para
aprendizado, que visa minimizar os erros e otimizar o desempenho do modelo. A função
objetiva utilizada é a perda de `entropia cruzada`. A função 𝐿(^𝑦, 𝑦) mede o quão próximo
^𝑦, a classe estimada, está de 𝑦, a classe verdadeira (JURAFSKY; MARTIN, 2024a).
A otimização da função de perda ocorre através do `gradiente descendente`. Seu objetivo
é encontrar o conjunto de pesos que irá minimizar a função de perda (JURAFSKY;
MARTIN, 2024a). O `gradiente descendente` é um método que encontra o mínimo de uma função
ao descobrir, no espaço de parâmetros 𝜃, a direção em que a inclinação da função está
aumentando de forma mais acentuada. Então, ele se move na direção oposta (JURAFSKY;
MARTIN, 2024a).

### Métricas de Avaliação

Uma vez que o modelo é treinado, o próximo passo consiste em obter as suas
predições em uma base de teste. A base de teste é composta por objetos rotulados, mas
que não foram utilizados na construção do modelo. A partir das predições que o modelo
faz na base de teste, tona-se possível construir uma matriz de confusão. A avaliação
dos classificadores se dará pela acurácia, precisão, recall e F1-Score, métricas de avaliação
calculadas a partir da matriz de confusão (JURAFSKY; MARTIN, 2024c). A estrutura da
matriz de confusão utilizada neste trabalho é apresentada na Tabela a seguir, onde cada elemento
da matriz corresponde à frequência absoluta de classificações. A matriz de confusão possui
as seguintes classificações:

* `VN`: Verdadeiro Negativo (classificou que não era persuasivo e acertou).
* `FP`: Falso Positivo (classificou que era persuasivo e errou).
* `FN`: Falso Negativo (classificou que não era persuasivo e errou).
* `VP`: Verdadeiro Positivo (classificou que era persuasivo e acertou).

![estrutura_matriz_confusao](https://github.com/user-attachments/assets/2d728855-d3a2-4c76-b364-0c27e69ba182)

A `acurácia` mede a proporção de predições corretas feita pelo modelo, ou seja,
a quantidade de exemplos que foram corretamente classificados em relação ao total de
exemplos.

![formula_acuracia](https://github.com/user-attachments/assets/56c2ae13-4636-4f41-8c3c-b1805ad27711)

A `precisão` indica a proporção de exemplos positivos classificados corretamente
pelo modelo em relação a todos os exemplos que o modelo classificou como positivos.

![formula_precisao](https://github.com/user-attachments/assets/5402264d-4453-4b44-8cc7-e51df7bbf385)

O `recall` mede a proporção de exemplos positivos que foram corretamente identificados
pelo modelo em relação a todos os exemplos que são realmente positivos.

![formula_recall](https://github.com/user-attachments/assets/5f7f6eea-b743-43bb-9d76-daac3c0e64c9)

Por fim, a medida `F1-Score` é média harmônica da precisão e do recall, fornecendo
uma métrica que balanceia precisão e recall.

![formula_f1score](https://github.com/user-attachments/assets/fbeee373-dace-4f5c-a202-2757507df017)


### Resultados

Neste capítulo são apresentados os resultados obtidos a partir dos experimentos
realizados conforme a metodologia previamente descrita. Os experimentos foram realizados
com o objetivo de criar e avaliar diferentes modelos de classificação para detectar a
presença de conteúdo persuasivo no texto do meme. Para isso, a base de treino foi utilizada
para treinar os classificadores e a base de teste foi utilizada para estimar o desempenho
preditivo dos modelos.

Para resolver o problema do desbalanceamento da base, utilizou-se os métodos
de balanceamento de base descritos na metodologia. Foram utilizados os atributos preditivos
apresentados na seção metodológica, que foram obtidos através da engenharia de
características. A partir desses atributos, diferentes combinações foram realizadas nos experimentos.
A seguir, apresentam-se os atributos utilizados em cada um dos experimentos.

* Atributos utilizados por Cruz et al. (2019), desconsiderando a medida TF-IDF.
* Atributos utilizados por Cruz et al. (2019) com a medida TF-IDF para os 50
bigramas mais frequentes.
* Atributos utilizados por Cruz et al. (2019) com a medida TF-IDF para os 50
unigramas mais frequentes.

#### Resultados Gerais

No `experimento 1` podemos obter o efeito isolado dos atributos gerados pela engenharia
de características, sem considerar o TF-IDF. Os experimentos 2 e 3 nos fornecem
o efeito conjunto dos atributos e a medida TF-IDF, com bigramas e unigramas, respectivamente.
A Tabela a seguir exibe os resultados obtidos no `experimento 1`, onde não foi
incluída a medida TF-IDF.

![tabela_exp1](https://github.com/user-attachments/assets/26f181c9-ceba-4279-8d0b-99d8899dbde0)

No `experimento 1`, ao se utilizar `undersampling`, a `Floresta Aleatória` se destaca
com uma acurácia de 0,6940 e um F1-Score de 0,7916, superando tanto a `Árvore de
Decisão` quanto a `Regressão Logística`. A alta precisão, de 0,9366, indica que a `Regressão
Logística` tem um baixo índice de falsos positivos.

No cenário de `oversampling`, todos os classificadores apresentam uma melhoria na
acurácia, recall e F1-Score. Novamente, a `Floresta Aleatória` lidera com uma acurácia de
0,8020 e um F1-Score de 0,8833. A `Árvore de Decisão` também apresenta bons resultados,
com uma acurácia de 0,7730, precisão de 0,8791 e um F1-Score de 0,8638. A `Regressão Logística`, embora tenha melhorado em relação ao cenário com `undersampling`, ficou atrás
com uma acurácia de 0,6660 e um F1-Score de 0,7668.

Em uma análise global do `experimento 1`, a `Floresta Aleatória` apresenta os maiores
valores de acurácia, recall e F1-Score no cenário de `oversampling`. A `Árvore de Decisão`,
que é um método mais simples, alcançou resultados próximos dos resultados obtidos pela
`Floresta Aleatória` com o `oversampling`. Esse é um ponto relevante, dado que a `Árvore de
Decisão` gera um modelo interpretável e de fácil entendimento. Já a `Regressão Logística`
vence na precisão, no cenário de `undersampling`. O experimento ainda foi realizado em um
cenário com balanceamento `SMOTE` (CHAWLA et al., 2002), técnica de balanceamento
bastante tradicional que gera observações sintéticas da classe minoritária. Porém, esta
técnica obteve resultados inferiores e foi desconsiderada deste trabalho.

A Tabela a seguir apresenta os resultados do `experimento 2`, incluindo a medida
TF-IDF com os 50 bigramas mais frequentes. Neste experimento, no cenário com undersampling, a `Floresta Aleatória` obtém
a maior acurácia, recall e F1-Score. Contudo, com exceção da `Regressão Logística`, os
desempenhos dos modelos foram inferiores ao cenário com `oversampling`. A `Regressão
Logística` vence na precisão, com um valor de 0,9427, apenas um pouco maior do que o
obtido no `experimento 1`.

Quando o `oversampling` é aplicado, a `Árvore de Decisão` e a `Floresta Aleatória` apresentam fortes aumentos de acurácia e F1-Score. Neste cenário, a `Árvore de Decisão`
alcança um valor de 0,7870 na acurácia e 0,8719 no F1-Score. Já a `Floresta Aleatória`,
0,7970 e 0,8810, respectivamente, o que a coloca como o classificador com os maiores
valores nessas duas métricas. A `Regressão Logística` obtém valores levemente menores na
acurácia e F1-Score, com 0,6630 e 0,7622, respectivamente. Na precisão, ela consegue uma
leve melhora, atingindo o valor de 0,9424.

![tabela_exp2](https://github.com/user-attachments/assets/320cf52c-b35b-4378-95d2-e7864c316e7b)

Analisando todo o `experimento 2` conjuntamente, destacam-se os resultados obtidos
pela `Floresta Aleatória` no cenário com `oversampling`. Ela obteve uma acurácia de
0,7980, um recall de 0,8863 e um F1-Score de 0,8810, sendo esses os maiores valores dessas
métricas no experimento. A `Regressão Logística` se destaca com a maior precisão de todas,
com um valor de 0,9427, no cenário com `undersampling`.

A Tabela a seguir apresenta os resultados do `experimento 3`, incluindo a medida
TF-IDF com os 50 unigramas mais frequentes. No `experimento 3`, ao utilizar do `undersampling`, a acurácia, recall e F1-Score de
todos os modelos são inferiores em relação ao cenário de `oversampling` A precisão dos
modelos, contudo, foi superior. A `Regressão Logística`, novamente, apresenta destaque
com sua alta precisão de 0,9472.

![tabela_exp3](https://github.com/user-attachments/assets/638174f2-a937-430c-b07d-248ba5fc3afc)

Com a aplicação do balanceamento por `oversampling`, todos os classificadores apresentam
melhoria na acurácia, recall e F1-Score. Novamente, a `Floresta Aleatória` demonstra um desempenho superior em relação aos outros classificadores, atingindo a maior
acurácia, com 0,8130, e o maior F1-Score, com 0,8894. Já a `Árvore de Decisão`, dessa vez,
ultrapassa a `Regressão Logística` e atinge o segundo maior F1-Score entre os classificadores,
com um total de 0,8680 contra 0,7700 da `Regressão Logística`. Porém, novamente,
a `Regressão Logística` se destaca com sua alta precisão, obtendo um valor de 0,9433,
levemente inferior ao que obteve no cenário com `undersampling`.

Analisando o `experimento 3` como um todo, o maior destaque vai para a `Floresta
Aleatória` com balanceamento por `oversampling`. Ela apresenta os maiores valores de acurácia,
recall e F1-Score para todo o `experimento 3`, se destacando com o valor de 0,8894
na medida F1-Score.

Observando todos os 3 experimentos, podemos ver resultados muitos próximos entre
eles, com a `Floresta Aleatória` apresentando os melhores resultados no cenário com
`oversampling` do `experimento 3`. Ela alcançou uma acurácia de 0,8130, um recall de 0,8910
e um F1-Score de 0,8894. Foram os maiores valores para essas métricas entre todos os
classificadores em todos os experimentos realizados. Porém, ao levarmos em consideração
a proximidade dos resultados, é interessante considerar o `experimento 1` como o melhor
entre eles, pois trata-se de um cenário em que os atributos gerados pela engenharia de
características são de maior simplicidade e melhor entendimento. Além disso, embora a
`Floresta Aleatória` apresente o melhor desempenho, também é válido notar que os resultados
com `Árvore de Decisão` foram bastante próximos. A `Árvore de Decisão` é um modelo interpretável e é de fácil entendimento o processo feito por ela para classificar uma nova
observação. Então, por uma questão de maior poder interpretativo, seus resultados neste
trabalho possuem um destaque em relação aos outros. Já a `Regressão Logística` obteve
a maior precisão de todos os experimentos no cenário com `undersampling`, também no
`experimento 3`, alcançando um valor de 0,9472.

#### Comparação com Modelos Gerados sem Balanceamento de Classes

Os resultados apresentados na seção anterior, onde foram aplicadas técnicas de
balanceamento de classes, evidenciam uma tentativa de melhoria dos resultados originais,
sem balanceamento. Uma base desbalanceada pode levar o modelo a favorecer previsões na classe
majoritária (CRUZ; ROCHA; CARDOSO, 2019), sendo esse o caso da base de treino
utilizada neste trabalho.

O `experimento 1`, com os atributos gerados pela engenharia de características e
sem considerar a medida TF-IDF, alcança resultados próximos aos outros experimentos.
Porém, é o experimento de mais fácil entendimento, pois são atributos facilmente interpretáveis
que foram extraídos do texto. Portanto, esse experimento será utilizado como base
de comparação ao cenário sem balanceamento. A Tabela a seguir exibe os resultados do
`experimento 1` sem nenhum balanceamento de base.

![tab_exp1_desbalanceado](https://github.com/user-attachments/assets/3cced60c-a8ee-4487-a59a-b3221de92175)

Ao analisar os resultados e comparar com os cenários onde `undersampling` e `oversampling`
foram aplicados, pode se ter a conclusão de que o cenário sem balanceamento
algum é melhor e mais promissor, dado que os valores de acurácia, recall e F1-Score são
superiores. Contudo, pode se tratar de uma interpretação equivocada. Neste cenário, é importante
analisar não só os valores das métricas, mas o contexto em que esse experimento
ocorreu.

Ao realizar o experimento em uma base que não passou pelo processo de `undersampling`
ou `oversampling`, há um forte desbalanceamento. A base de treino possui um
total de 78% das observações com textos de memes classificados como persuasivos, contra
22% de textos não persuasivos. Conforme apontado por Cruz, Rocha e Cardoso (2019),
isso tende a favorecer previsões na classe majoritária, nesse caso, criando um viés para
classificar novos textos de memes como persuasivos.

Assim como a base de treino, a base de teste também possui a maior parte das
observações com textos persuasivos, representando 84% das observações. Essa alta proporção,
aliada com um viés dos modelos para classificar textos como persuasivos, tendem
a levar a um cenário em que os modelos terão um alto índice de acertos. Porém, dado o
contexto, isso não representa um bom resultado.

De forma a ilustrar esta análise, a Tabela a seguir apresenta a matriz de confusão
gerada para a `Regressão Logística`, modelo com o maior F1-Score no cenário sem
balanceamento.

![matriz_confusao_sem_balanceamento](https://github.com/user-attachments/assets/9b9eff9a-4750-4b89-8adb-1da321cfb264)

Na matriz de confusão, as linhas representam a classe verdadeira e as colunas
representam a classe predita. Como se pode observar, quase todas as observações da base
de teste foram preditas como texto persuasivo. Com 84% da base sendo de fato texto
persuasivo, a quantidade de acertos é bastante alta. Porém, isso não indica um bom
modelo, mas apenas evidencia o viés gerado pela base não balanceada. A Tabela 9 a
seguir evidencia a forte diferença na matriz de confusão para a `Regressão Logística` no
cenário com balanceamento por `oversampling`. Foi escolhido o cenário com `oversampling`
para a comparação por este ter apresentado os melhores resultados.

![matriz_confusao_RL_oversampling](https://github.com/user-attachments/assets/28d0742a-6585-4b73-816e-341c58c86657)

Portanto, embora apresente métricas elevadas, conclui-se que não se trata de uma
boa classificação e que o balanceamento da base é uma importante estratégia para se ter
resultados mais promissores e confiáveis.

#### Análise da Importância dos Atributos com Árvore de Decisão

Os modelos treinados com `Árvore de Decisão` obtiveram um desempenho preditivo
muito próximo da `Floresta Aleatória`. Diferentemente da `Floresta Aleatória`, a `Árvore de
Decisão` gera um modelo diretamente interpretável, em uma estrutura gráfica, de forma é
apresentado de forma clara o que levou o modelo a fazer uma determinada classificação.
Esta seção tem por objetivo analisar a importância dos atributos da `Árvore de Decisão`
do `experimento 1`, no cenário com `oversampling`. Este experimento foi escolhido pela
maior simplicidade nos atributos utilizados e por seu bom desempenho. O cenário com
`oversampling` foi escolhido por apresentar os melhores resultados do experimento.

A `Árvore de Decisão` gerada possui diferentes regras, onde cada regra leva a classificação
do texto do meme como persuasivo ou não persuasivo. Uma elevada quantidade
de regras foi gerada, onde 1.263 regras possuem 100% de confiança, ou sejam, classificam
perfeitamente um texto como persuasivo ou não persuasivo. Dado o elevado número de
regras definidas, serão apresentadas as duas regras com maior cobertura para os textos
persuasivos e as duas regras com maior cobertura para os textos não persuasivos, todas
com 100% de confiança.

Como a análise está sendo feita para o cenário com `oversampling`, é importante
lembrar que estamos lidando com uma base de treino que contém mais observações do
que teria sem a aplicação dessa técnica de balanceamento. Nesse contexto, a base de
treino possui um total de 11.472 textos de memes, devido à replicação de textos da classe
minoritária.

Primeiramente, apresentam-se as regras com maior cobertura para a classificação
de textos como persuasivos. A primeira regra cobre em 525 textos persuasivos, enquanto
a segunda, cobre 187 textos persuasivos, todos provenientes da base de treino.

* SE (total de caracteres > 125,5) e (4,005 < média de caracteres por palavra
<= 5,544) e (média de caracteres por frase < 27,829) e (1,349 < variância de
caracteres por palavra <= 7,933) e (3,5 < frequência de pontuação <= 9,5) e
(frequência de letras maiúsculas > 6,5) e (proporção de tokens sobre palavras
lematizadas > 0,489), ENTÃO (Texto = “Persuasivo”).
* SE (total de caracteres > 325,5) e (média de caracteres por palavra > 4,005)
e (média de caracteres por frase > 27,829) e (variância de caracteres por frase
<= 51.948,834) e (frequência de pontuação > 9,5) e (proporção de tokens sobre
palavras lematizadas > 0,489), ENTÃO: (Texto = “Persuasivo”).

Por fim, apresentam-se as regras com maior cobertura para a classificação de textos
como não persuasivos. A primeira regra foi baseada em 78 textos não persuasivos,
enquanto a segunda, cobre 70 textos não persuasivos, todos provenientes da base de
treino.

* SE (total de caracteres <= 32,5) e (4,9 < média de caracteres por palavra <=
5,708) e (variância de caracteres por palavra <= 10,32) e (frequência de pontuação
<= 4,5) e (1,5 < frequência de letras maiúsculas <= 8,5) e (frequência de
pontuação > 0,5) e (variância de caracteres por frase <= 44,5), ENTÃO (Texto
= “Não persuasivo”).
* SE (total de caracteres <= 32,5) e (frequência de letras maiúsculas <= 0,5) e
(frequência de pontuação <= 4,5) e (variância de caracteres por frase <= 44,5),
ENTÃO (Texto = “Não persuasivo”).

Essas regras cobrem um total de 860 textos de memes, o que representa um total de
aproximadamente 7,5% da base de treino balanceada por `oversampling`. Podemos ver pelas
regras a diferença entre textos persuasivos e não persuasivos, por exemplo, no atributo
“total de caracteres”. As regras exibidas nos mostram que um elevado valor de caracteres
tende a levar o texto a ser persuasivo.

Para uma análise comparativa, as tabelas a seguir apresentam as principais estatísticas
dos atributos para os textos persuasivos e para os textos não
persuasivos, respectivamente.

* Textos persuasivos:
  
![estatisticas_memes_persuasivos](https://github.com/user-attachments/assets/c96405f9-b1cb-4fe3-b2d1-d36feb5145ed)

* Textos não persuasivos:
  
![estatisticas_memes_naopersuasivos](https://github.com/user-attachments/assets/073ecc26-3d07-429a-8898-cd0770451d7e)

Alguns atributos possuem diferenças mais significativas entre os textos persuasivos
e não persuasivos. Conforme as regras apresentadas da `Árvore de Decisão` sugeriram, textos
persuasivos possuem, em média, 126% mais caracteres do que textos não persuasivos.
Essa diferença também pode ser vista na quantidade máxima de caracteres, onde os textos
persuasivos representam um aumento de 195% em relação aos textos não persuasivos. O
desvio padrão desse atributo em textos não persuasivos, menor que a metade para textos
persuasivos, indica uma dispersão menor dessa variável nesse contexto, fortalecendo a regra
de que quanto menor for o total de caracteres no texto, mais propenso ele é a ser não
persuasivo.

O atributo “frequência de letras maiúsculas” também apresenta diferenças mais
notáveis entre as duas classificações. Textos persuasivos possuem, em média, quase o
dobro da quantidade de letras maiúsculas de textos não persuasivos. O valor máximo
desse atributo, por exemplo, aumenta em 220% nos textos persuasivos. Essas estatísticas também reforçam as regras da `Árvore de Decisão`, que indicam que um número maior de
letras maiúsculas no texto os aproxime da classificação como persuasivo.

### Conclusão

Este trabalho abordou a classificação de persuasão em textos de memes, utilizando
uma abordagem baseada em engenharia de características. Para isso, utilizou-se dos modelos
de `Árvore de Decisão`, `Floresta Aleatória` e `Regressão Logística`. A exploração do
problema de classificação de persuasão em textos de memes é algo novo, levando este
trabalho a realizar este estudo em um contexto mais desafiador do que a classificação de
persuasão em outros tipos de texto, como artigos de notícias, por exemplo.

A engenharia de características foi empregada para extrair atributos numéricos
dos textos presentes nos memes, visando sua aplicação em algoritmos de classificação. Os
atributos utilizados foram baseados na metodologia descrita por Cruz, Rocha e Cardoso
(2019), que realizaram a classificação de persuasão em textos de artigos. No contexto dos
textos de memes, estamos lidando com conteúdos mais curtos e informais.

Os experimentos realizados apontaram que os resultados alcançados pela `Árvore
de Decisão` e `Floresta Aleatória` foram, em geral, superiores do que a `Regressão Logística`.
A `Regressão Logística` obteve um desempenho melhor apenas na precisão, enquanto a
`Árvore de Decisão` e `Floresta Aleatória` tiveram melhores acurácia, recall e F1-Score. A
`Árvore de Decisão` e a `Floresta Aleatória` tiveram desempenhos aproximados entre si.
Neste caso, a vantagem da `Árvore de Decisão` se dá pelo fato de se tratar de um modelo
facilmente interpretável, com regras claras para a classificação.

Três diferentes experimentos foram realizados, com diferentes atributos e balanceamentos.
O `experimento 3`, no cenário com `oversampling`, apresentou três métricas de
avaliação com os maiores valores entre todos os experimentos. Esses resultados foram
alcançados com a `Floresta Aleatória`, que obteve uma acurácia de 0,8130, um recall de
0,8910 e um F1-Score de 0,8894. Contudo, por terem desempenhos próximos entre si, o
experimento 1 apresenta destaque em relação aos demais, por sua maior simplicidade e
clareza nos atributos utilizados. Neste caso, utilizaram-se os atributos propostos por Cruz
et al. (2019), mas sem a inclusão da medida TF-IDF. Neste experimento, o cenário com
balanceamento por `oversampling` se saiu melhor.

No `experimento 1`, com `oversampling`, a `Floresta Aleatória` aparece com o melhor
desempenho, alcançando uma acurácia de 0,8020 e um F1-Score de 0,8833. A `Árvore de
Decisão` alcança valores próximos, com uma acurácia de 0,7730 e um F1-Score de 0,8638.
A `Regressão Logística` se destaca na precisão, com um valor de 0,9337. Embora a `Floresta
Aleatória` tenha um desempenho levemente melhor do que a `Árvore de Decisão`, destaca-se
a vantagem da `Árvore de Decisão` por sua interpretabilidade.

O balanceamento de classes se mostrou uma importante estratégia para gerar um
equilíbrio nos dados, dividindo a base de treino com 50% de observações como textos
persuasivos e 50% de observações como textos não persuasivos. Isso gerou um maior
equilíbrio entre falsos positivos e falsos negativos, uma vez que diminuiu a tendência do
modelo em classificar novas observações como persuasivas. Antes do balanceamento, a
maioria das observações da base de teste era classificada como persuasiva. Como a maior
parte de base de teste é, de fato, persuasiva, isso gerava um alto valor de falsos positivos,
bem como de verdadeiros positivos.

Por fim, apresenta-se a seguir ideias para trabalhos futuros, tais como:

* Criação de um sistema em duas etapas. A primeira etapa, realizada neste trabalho,
classifica o texto como persuasivo ou não. A segunda etapa, então, consiste
em classificar qual ou quais técnicas de persuasão foram utilizadas nos memes
classificados como persuasivos na primeira etapa.
* Gerar novos atributos preditivos a partir do texto, como por exemplo, elementos
semânticos. Desta forma, pode-se incluir atributos como total de adjetivos, total
de verbos, entre outros.
* Na geração de novos atributos pode-se, ainda, criar listas com palavras positivas
ou negativas, gerando uma contagem para cada caso e utilizando esses valores
como atributos. Essas listas podem ser criadas a partir de adjetivos ou de palavras
específicas que façam parte do contexto do problema.
* Avaliação de embeddings semânticos como atributos, método que já apresentou
bons resultados em outros trabalhos recentes. Contudo, neste caso, há a desvantagem
de não ser um método interpretável, diferentemente da Árvore de Decisão,
por exemplo.
* Criação de um léxico com unigramas e bigramas frequentemente presentes em
textos persuasivos, podendo utilizar a frequência absoluta de cada caso como
atributo preditivo.
* Balancear a base de treino com diferentes proporções entre as duas classes, além
da divisão realizada de 50% para persuasão e 50% para não persuasão.

