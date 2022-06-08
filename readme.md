
# Usando a regressão linear para previsão de movimento do mercado

Ordinary least squares (OLS) e regressão linear são técnicas estatísticas de décadas que provaram ser úteis em muitas áreas de aplicação diferentes. Esta seção usa regressão linear para fins de previsão de preços. No entanto, ele começa com uma rápida revisão do básico e uma introdução à abordagem básica.

## Uma revisão rápida da regressão linear
Antes de aplicar a regressão linear, uma rápida revisão da abordagem baseada em alguns dados aleatórios pode ser útil. O código de exemplo usa NumPy para gerar primeiro um objeto ndarray com dados para a variável independente x. Com base nesses dados, são gerados dados aleatórios (“dados ruidosos”) para a variável dependente y. O NumPy fornece duas funções, polyfit e polyval, para uma implementação conveniente da regressão OLS baseada em monômios simples. Para uma regressão linear, o grau mais alto para os monômios a serem usados é definido como 1.


## MODELOS UTILIZADOS
### Linear Regression
Para representar a relação entre uma variável dependente (y) e uma variável independente (x), usamos o modelo:

y=a+bx

Onde:
Y = Alvo
a = Intercepto
b = Inclinação da reta
x = variável independente

Em casos em que existam mais de duas variáveis, este conceito pode ser estendido, temos assim a regressão linear múltipla. Por exemplo, considere um cenário em que você deve prever o preço da casa com base em sua área, número de quartos, renda média das pessoas na área, idade da casa e assim por diante. Nesse caso, a variável dependente (variável de destino) depende de várias variáveis independentes.

### Logistic regression
A regressão logística é um método estatístico para prever classes binárias. O desfecho ou variável alvo é de natureza dicotótica. Dicotos significa que só há duas classes possíveis. Por exemplo, pode ser usado para problemas de detecção de câncer. Ele calcula a probabilidade de uma ocorrência de evento.

É um caso especial de regressão linear onde a variável alvo é categórica na natureza. Ele usa um registro de probabilidades como variável dependente. A Regressão Logística prevê a probabilidade de ocorrência de um evento binário utilizando uma função logit.

Função Sigmoid:

p = l/(l + e^(-y))

Aplique função Sigmoid na regressão linear:

p = l/(l + e^(a+bx))

Propriedades da Regressão Logística:

A variável dependente na regressão logística segue a Distribuição Bernoulli.
A estimativa é feita através da máxima probabilidade.
Sem R Square, o model fitness é calculado através de Concordance, KS-Statistics.


<img src=http://res.cloudinary.com/dyd911kmh/image/upload/f_auto,q_auto:best/v1534281070/linear_vs_logistic_regression_edxw03.png>


### Random forest
Vamos rapidamente passar por cima de árvores de decisão como eles são os blocos de construção do modelo florestal aleatório. Felizmente, eles são muito intuitivos. Eu estaria disposto a apostar que a maioria das pessoas tem usado uma árvore de decisão, conscientemente ou não, em algum momento de suas vidas.

<img src=https://miro.medium.com/max/1262/1*LMoJmXCsQlciGTEyoSN39g.jpeg>

Imagine que nosso conjunto de dados consiste nos números no topo da figura à esquerda. Temos dois 1s e 5 0s (1s e 0 são nossas aulas) e desejamos separar as aulas usando suas características. As características são de cor (vermelho vs. azul) e se a observação é sublinhada ou não. Então, como podemos fazer isso?

A cor parece uma característica bastante óbvia para dividir, pois todos, exceto um dos 0s são azuis. Então podemos usar a pergunta, "É vermelho?" para dividir nosso primeiro nó. Você pode pensar em um nó em uma árvore como o ponto onde o caminho se divide em dois — observações que atendem aos critérios descem o ramo Yes e aqueles que não descem o ramo Não.

O ramo No (o blues) é todo 0s agora, então estamos feitos lá, mas nossa filial Yes ainda pode ser dividida ainda mais. Agora podemos usar o segundo recurso e perguntar: "Está sublinhado?" para fazer uma segunda divisão.

Os dois 1s que são sublinhados descem o subbranch Yes e o 0 que não é sublinhado desce pelo subbranch direito e estamos todos acabados. Nossa árvore de decisão foi capaz de usar os dois recursos para dividir os dados perfeitamente. Vitória!

Obviamente, na vida real, nossos dados não serão tão limpos, mas a lógica que uma árvore de decisão emprega permanece a mesma. Em cada nó, ele perguntará -

Que característica me permitirá dividir as observações em mãos de uma forma que os grupos resultantes sejam tão diferentes um do outro quanto possível (e os membros de cada subgrupo resultante são tão semelhantes uns aos outros quanto possível)?


#

A floresta aleatória, como o nome indica, consiste em um grande número de árvores de decisão individuais que operam como um conjunto. Cada árvore individual na floresta aleatória cospe uma previsão de classe e a classe com mais votos torna-se a previsão do nosso modelo (veja a figura abaixo).

<img src=https://miro.medium.com/max/1052/1*VHDtVaDPNepRglIAv72BFg.jpeg>

O conceito fundamental por trás da floresta aleatória é simples, mas poderoso - a sabedoria das multidões. Na ciência de dados, a razão pela qual o modelo florestal aleatório funciona tão bem é:

Um grande número de modelos relativamente não corrigidos (árvores) operando como um comitê superará qualquer um dos modelos constituintes individuais.

# RESULTADOS

Os modelos modelos nos permite escolher diferentes features como entreada para prever o retorno de 1 dia para um ativo alvo. Utilizamos como exemplo os 5 ativos com maior peso no
indice ibovespa com a finalidade de explicar o movimento do próprio indice.

Embora o exemplo seja extremamente simples, o modelo de Linear Regression e o modelo de Logistic Regression apresentaram um sharpe superior ao buy&hold. Utilizando uma janela de teste de 1000 dias e uma janela de treino de aprox 2500 dias os modelos seguiram com sharpe superior ao B&H.
### Proximos passos
 - Entender o motivo do Random Forest "overfitar" o treino e ter desempenho ruim no teste;
 - Criar saida mostrando quais sao os ativos que mais influenciam na predicao;
 - ...



Referências
[BOOK]Python for Algorithmic Trading: From Idea to Cloud Deployment
