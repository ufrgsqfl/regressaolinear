
# Usando a regressão linear para previsão de movimento do mercado

Ordinary least squares (OLS) e regressão linear são técnicas estatísticas de décadas que provaram ser úteis em muitas áreas de aplicação diferentes. Esta seção usa regressão linear para fins de previsão de preços. No entanto, ele começa com uma rápida revisão do básico e uma introdução à abordagem básica.

## Uma revisão rápida da regressão linear
Antes de aplicar a regressão linear, uma rápida revisão da abordagem baseada em alguns dados aleatórios pode ser útil. O código de exemplo usa NumPy para gerar primeiro um objeto ndarray com dados para a variável independente x. Com base nesses dados, são gerados dados aleatórios (“dados ruidosos”) para a variável dependente y. O NumPy fornece duas funções, polyfit e polyval, para uma implementação conveniente da regressão OLS baseada em monômios simples. Para uma regressão linear, o grau mais alto para os monômios a serem usados é definido como 1.


Referências
[BOOK]Python for Algorithmic Trading: From Idea to Cloud Deployment