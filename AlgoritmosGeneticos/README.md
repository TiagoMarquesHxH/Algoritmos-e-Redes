# Experimentos de otimização e algoritmos genéticos

Nesta pasta estão inclusos experimentos de algoritmos genéticos, e uma introdução conceitual ao assunto.

## O que é um Algoritmo Genético?

Um algortimo genético é um algoritmo que visa buscar a melhor solução para um dado problema, sendo assim considerado um algoritmo para `problemas de otimização`.

O nome deriva de uma analogia ao evolucionismo Darwiniano e à Biologia, pois como aqueles mais capazes de encontrarem uma solução para um problema apresentam maior chance de serem selecionados como aptos, e de consequentemente passarem suas qualidades para as próximas gerações, o mesmo vale para um problema de otimização, onde os valores que são candidatos mais fortes de resolverem um problema de otimização, também serão "passados para frente" nos algoritmos genéticos.

## Componentes de um Algoritmo Genético

<h3> Genótipos e Genes </h3>

Na biologia, temos `indivíduos` que são compostos de cromossomos, os quais são compostos de `genes`. Computacionalmente, podemos considerar que os indivíduos são uma `string binária`, compostos pelos seus genes que são os valores binários 0 e 1.

<h3> População </h3>

Ora, se temos diversos individuos logo teremos uma `população`, e para um problema de otimização queremos uma população que contenha os melhores indivíduos candidatos a resolverem o problema em questão.

O algoritmo pode `gerar` diversas populações com indivíduos diferentes e genes diferentes, visando encontrar a melhor população candidata à solução de um problema.

<h3> Função Fitness </h3>

Esta é a função do algoritmo que visamos otimizar/problema que queremos resolver, logo, é ela que irá avaliar o quão bom são nossos indivíduos candidatos.

Novamente, ligando à biologia, indivíduos que são bem avaliados por esta função tendem a ser escolhidos para `reproduzir`e então ter seus genes passados para a `próxima geração`. Quanto mais gerações forem realizadas, maior é a tendencia de ter uma boa avaliação.

<h3> Seleção </h3>

Como dito anteriormente, os indivíduos que forem melhor avaliados pela função fitness serão selecionados, e esta `seleção` é que determinará quais indivíduos irão reproduzir e `gerar` a nova geração de indivíduos.

<h3> Crossover </h3>

Para a geração de novos indivíduos por reprodução, é necessários que dois indivíduos realizem a troca de uma parcela de seus genes, e é através da operação de `crossover` que isto ocorre. Aqui temos que considerar que ao final da operação, são formados dois novos indivíduos, o `pai` com uma parcela de genes da `mae` e vice-versa. A delimitação da quantidade de genes que serão trocados é dada como parâmetro variável no algoritmo, podendo ser alterada e terem mais/menos genes sendo `recombinados`.

<h3> Mutação </h3>

Mutações são alterações aleatórias em um gene, definidas por uma variável probabilística, alterando seu valor binário. Estas mutações procuram `refrescar` a população aleatoriamente a cada etapa do algoritmo, visando trazer novos padrões de alterações no gene, promovendo que sejam feitas novas buscas de soluções com os novos padrões definidos.

# Experimentos

## Experimento A.01 - Busca aleatória

A busca aleatória é uma forma simples de tentarmos solucionar um algoritmo genético, pois o algoritmo irá simplesmente escolher aleatoriamente uma região de soluções possíveis para tentarmos encontrar candidatos que podem solucionar nosso problema.

O problema abordado no experimento foi o das caixas (individuos) binárias, onde cada gene pode assumir um valor 0 ou 1, e o objetivo é de encontrar a combinação a qual a soma destes valores de cada indivíduo seja máximo, ou seja, queremos uma população que apresente indivíduos apenas com o gene 1.

A abordagem inicial foi de definirmos nosso espaço de busca, dado pelas constantes definidas no início do algoritmo, sortearmos um candidato aleatório e analisar o seu desempenho dado pela função fitness, com um critério de parada definido para uma população com indivíduos com apenas o gene 1.

<h4> Conclusões do experimento </h4>

Com relação ao algorítimo, foi notado que seu funcionamento é probabilístico, pois ele tentará buscar o maior valor de soma após um dado número de candidatos, e que este seria uma boa escolha para problemas os quais não temos um limite de tentativas para encontrar o valor esperado. Porém, seria uma má escolha para problemas nos quais temos muitos valores e uma busca aleatória requeriria muito tempo e muitas tentativas para encontrar o valor desejado.

## Experimento A.02 - Busca em grade

