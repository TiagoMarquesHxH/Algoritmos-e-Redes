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

O método da busca em grade é um método no qual, extensivamente, procura por combinar todas os parâmetros possíveis de um dado algoritmo. Assim, a busca em grade realizará combinações de todos os genes envolvendo todos os indivíduos, até que seja encontrado os melhores candidatos após um dado número de gerações.

Novamente, como para encontrarmos a solução de todo algoritmo, definimos uma abordagem inicial a ser tomada. Para isso, definimos os parâmetros e seus valores, criamos a função fitness que realizará as combinações, e então obteremos a melhor combinação que pode ser obtida enquanto a busca em grade era realizada.

<h4> Conclusões do experimento </h4>

Neste experimento, abordamos o problema das 2 caixas, e desta vez buscamos a solução através da busca em grade. Foi notado que o algorítimo é um algorítimo do tipo determinístico, pois o algorítimo sempre irá encontrar um resultado esperado, e neste caso, o de maior soma.

A busca em grade consegue encontrar os mínimos e máximos da função objetivo, pois ela irá varrer todos os valores possíveis de serem resultados, incluindo os de máximo e mínimo.

Porém, a busca em grade é limitada no quesito de performance, pois com um grande número de parâmetros e itens, seria necessário uma maior varredura de grade, ou seja uma maior quantidade de repetições, tendo maior demanda computacional e de tempo.

## Experimento A.03 - Algoritmo genético

Aqui será abordado, de forma em prática, um algoritmo genético. Os conceitos abordados previamente neste texto serão utilizados no decorrer do algoritmo, e para cada um dos conceitos, foram criadas funções em um arquivo de nome `funcoes.py`, presente nesta pasta.

O problema abordado é, novamente, das caixas binárias, considerando 4 caixas, e a solução deve ser encontrado por via de um algoritmo genético. Para facilitar a construção do algoritmo, o ideal é dividir o problema em partes, permitindo a articulação do pensamento durante a sua construção. 

- Primeiro, define-se a criação da população inicial, que será de caráter aleatório.
- Em seguida, criamos a função objetivo incluindo nela que o cálculo será feito para todos os indivíduos da população inicial, e que irá atualizar um `hall da fama` (um conjunto dos indivíduos da população final os quais apresentaram melhor score durante a busca).
- Depois, foi feita a criação de uma função que seleciona os indivíduos mais aptos a passarem para a próxima geração, e outra que realiza o cruzamento destes (onde ocorre a troca dos genes).
- A próxima etapa consiste em criar a função que trás para o algoritmo as `mutações`, que alteram o valor do gene, permitindo que novas informações cheguem ào sistema gerado.
- Após isso, calculamos a função fitness para todos os indivíduos da população gerada por último e então a enviamos para o hall da fama.
- Por fim, checamos os critérios de parada do algoritmo, e também passamos que caso estes critérios não sejam atingidos, teremos de realizar uma nova seleção, e então é retornado o hall da fama.

<h4> Conclusão do Experimento </h4>

Aqui abordamos os conceitos iniciais sobre um algoritmo genético e como construir um algoritmo deste tipo, e para entender melhor como realizar esta construção, analisamos um problema simples, o das caixas binárias.
Este problema constitui em encontrarmos uma população que contenha individuos no qual o resultado da soma seja o maior possível, caracterizando um problema de maximização.
O algoritmo cumpre razoávelmente o objetivo de atingir os melhores candidatos através das gerações sucessivas, juntamente com as etapas de cruzamento, mutação e seleção, mesmo se o número de gerações não for muito grande.
É um algorítimo probabilístico, pois se baseia muito em chances de variações ocorrerem (como a criação das gerações iniciais e probabilidades de mutação/cruzamento), e a população resultante, apesar de aparentar ser determinística após um grande número de gerações, irá variar quando o número de gerações for pequeno.
A função objetivo pode encontrar os mínimos e máximos da função objetiva desde que haja um grande número de gerações, e, sem a etapa de mutações a população final seria obtida exclusivamente pelo cruzamento e seleção, e no caso onde a população inicial apresenta muitos indivíduos com genes 0, a população final não teria bons candidatos, que poderiam ter sido melhores caso as mutações pudessem acontecer e alterar genes beneficamente ao longo das gerações. 
Com a mutação muito alta, obter uma população resultante na qual todos os indivíduos apresentam todos os genes possíveis como 1 seria impossível, pois como as mutações podem tanto beneficiar como prejudicar, alterações consecutivas nos genes tornariam as populações resultantes completamente aleatórias, aumentando conforme o número de gerações aumenta.

## Experimento A.04 - Problema das caixas não-binárias

Este experimento é diferente dos demais, pois aqui não consideramos caixas com valores de gene de apenas 0 ou 1, e sim qualquer valor inteiro que pertença ao conjunto [0, 100]. A finalidade ainda é a mesma, encontrar a melhor combinação de valores onde a soma destes deve ser a máxima possível.

Para isso, criamos novas funções semelhantes às dos problemas envolvendo caixas binárias, como as funções de gene, mutação, indivíduos e a função objetivo, com a diferença de incluirmos o método `.randint` selecionando valores aleatórios de 0 até o valor máximo da caixa (100). Também foram adicionados na função objetivo a soma dos genes do indivíduo para que assim seja possível obter o valor máximo.

<h4> Conclusão do Experimento </h4>

Este experimento aborda a construção de um algoritmo genético para a resolução do problema das caixas não-binárias. O problema das caixas não-binárias é bem similar ao problema das caixas binárias, com a exceção de que cada caixa (cada gene) pode assumir qualquer valor dentro do conjunto estipulado [0,100], e não apenas 0 ou 1. 

Dado o problema, foi necessária a criação de novas funções para atender a esta diferença, como a criação de uma nova função de mutação, pois agora o gene pode ser mutado para qualquer valor do conjunto, e de população.

Após a implementação destas alterações, notamos que o algoritmo apresenta caráter probabilístico, pois ainda depende de um grande número de gerações para obter uma solução. Para este algoritmo tentar encontrar uma solução com valor máximizado de 400, ele necessitaria de gerações ainda maiores do que as caixas binárias visto os valores possíveis e a interferência das mutações nestes valores. Logo, não é um algoritmo muito eficiente para encontrar uma solução de máximização.

## Experimento A.05 - Descobrindo a senha

Agora, o problema o qual analisaremos será o de se descobrir uma senha qualquer, que inclua apenas as letras do alfabeto, e levando em consideração que nossa função objetivo já sabe qual a senha correta. 

Podemos construir funções que façam uma quantificação da distância entre o nosso palpite de senha e a senha correta, e para isso, definimos que cada letra da senha seja um gene, e então comparamos gene a gene a distância entre estes, baseado em uma variável que passa todas as letras possíveis para um gene poder assumir. Como queremos encontrar a senha, logo é fácil ver que estamos analisando um problema de `minimização`, pois queremos que a distância entre as letras palpitadas e as corretas sejam as menores possíveis, até o ponto em que seja zero, representando que aquela letra corresponde à letra da senha original naquela posição.

<h4> Conclusão do Experimento </h4>

Agora, abordamos o problema de descobrirmos uma senha. Aqui, no entanto, teremos a senha correta passada para a função objetivo, para que as senhas que o algoritmo encontrar como candidato, seja comparada com a senha original e assim dê um valor de fitness baseado na diferença entre as senhas.

Logo, fica claro que o que estamos analisando é um problema de minimização, pois queremos a menor distância entre o indivíduo conténdo os genes (letras) e as letras da senha original.

E assim, enquanto o critério de parada não for atingido, realizamos a construção de novas populações de indivíduos e checamos o fitness (distancia) da senha que o individuo representa, até quando a distância entre todos os genes dos individuos seja 0, que representa que o individuo candidato corresponde ao individuo que é a senha correta

Com isso, vimos que este experimento teve um grau de complexidade mais elevada do que os anteriores, necessitando que novas funções fossem criadas para atender os requisitos para a solução do problema. O método da função objetivo desta vez foi o contrário do que o do experimento anterior, pois neste comparamos as letras candidatas e as letras originais, e desejamos que a distância seja 0 entre elas, significando que a letra candidata corresponde à letra original. Ou seja, tratamos aqui de um problema de minimização, pois queremos a menor distância possível entre as letras, e no experimento anterior o problema tratado envolvia maximização. O algoritmo também apresenta caráter probabilístico, pois apesar de não termos um gerador de populações, temos um loop que irá gerar um indivíduo contendo letras aleatoriamente, e assim irá comparar com a senha original.

## Experimento A.06 - Caixeiro viajante

O problema do caixeiro viajante é um problema relativamente conhecido na área de algoritmos e computação, principalmente pelo fato de ser um problema do tipo `NP` (Polinomial não-determinístico) onde sua verificação só pode ser obtida em tempo polinomial. O problema constitui, resumidamente, no caixeiro andar por todas as cidades de uma região, sem passar pela mesma cidade novamente, percorrendo o caminho com a menor distância possível. Nota-se que temos muitas possibilidades de caminho dependendo da quantidade de cidades, o que explica a quantidade de tempo necesária para se encontrar uma solução.

Sua aplicação em um algoritmo genético terá algumas novidades, pois no problema do caixeiro viajante, não podemos passar pela mesma cidade, logo um indivíduo que apresenta genes repetidos será `inválido`. Então, para a geração de indivíduos válidos, teremos que reconsiderar as funções de cruzamento e mutação, para que atendam a este novo requisito.
No experimento, consideraremos que o caixeiro visitará apenas 5 cidades, e deverá visitar todas, sem visitar a mesma novamente, e retornará à cidade inicial. Para isso ele deve descobrir o caminho que terá menor distância entre `n = 5` pontos de um plano cartesiano `(x,y)`.

A função mutação teve seu modo de funcionamento alterado, pois, a fim de gerarmos indivíduos válidos, não podemos alterar o valor do gene, mas podemos trocá-los de posição no índice da lista indivíduos. Esta troca permite que novos indivíduos possam ser cruzados, trazendo novas possibilidades para o algoritmo trabalhar sobre.
A função cruzamento também foi alterada, pois poderíamos acabar cruzando indivíduos com genes que ambos pai e mãe possuem, gerando uma prole inválida. Para evitar isso, a alteração fez com que a função agora realize um cruzamento `ordenado`, ou seja, ela define `pontos de corte` dentre o indivíduo, e então seleciona os genes dentro deste ponto de corte, passando-os para os filhos. A função basicamente passa os genes do pai e da mãe para outras 2 proles, mas em uma ordem diferente da ordem presente no pai e na mãe ou na outra prole.

Por ultimo, realizamos a permutação entre os caminhos possíveis e calculamos a função fitness para cada caminho, e selecionamos aquele com o melhor fitness.

<h4> Conclusão do Experimento </h4>

Neste experimento, foi trabalhado o problema do caixeiro viajante, onde tentamos desenvolver uma solução para o algoritmo encontrar o caminho mais curto ao percorrer por todas as cidades de uma região/estado, sem que haja a repetição das cidades percorridas. Vale ressaltar que o problema do caixeiro viajante é um problema NP (Polinomial não-determinístico), logo, não utilizaremos um grande número de cidades visando obter uma solução em tempo polinomial. A estratégia utilizada para a implementação deste algoritmo consistiu em utilizarmos funções de minimização, já que queremos obter a menor distância percorrida ao percorrermos todas as cidades. Também realizamos permutações para encontrarmos todos os caminhos possíveis e suas respectivas distâncias percorridas, e comparamos as distâncias encontradas durante as permutações a fim de encontrarmos o melhor caminho.
Após alguns testes variando o número de gerações, percebe-se que o algoritmo apresenta um caráter probabilístico, pois encontrará candidatos com distâncias variadas, não sendo necessariamente o melhor caminho a ser percorrido. Esta diferença entre o melhor caminho dos candidatos é devido à condições como as mutações, o número de gerações e a ordem dos genes dos indivíduos.

## Experimento A.07 - Aplicando restrições na busca

Neste experimento nós tratamos o problema da mochila, onde queremos armazenar itens em uma mochila e ter um maior lucro no final baseado nos valores do item. Porém, não podemos considerar apenas os valores dos itens para armazenar, pois a mochila tem um ***limite*** de peso que pode suportar, logo é necessário criar uma nova função de suporte que compute o peso e o valor de cada item para o cálculo da função objetivo, verificando se o indivíduo contendo os genes que representam os itens é um indivíduo ***válido*** para ser um candidato do nosso problema.

Logo de início, adotamos a estratégia de criarmos um dicionário contendo valor e peso de cada item que pode ser colocado na mochila, e definimos que um indivíduo será composto por genes binários (ou seja, que assumem o valor 0 ou 1). Os genes representarão se um item está presente naquele individuo (1) ou não (0), e assim teremos diversos indivíduos contendo itens variados.
Foram utilizadas diversas funções do problema das caixas binárias como mutação e seleção, e esta ultima realizará a seleção baseando-se na condição se o indivíduo é válido (não excede o peso).
Na função objetivo, aplicamos uma ***restrição*** aos valores de mochila encontrados, pois se temos um valor de mochila maior que o limite de peso desta, o valor de fitness retornado será de 0.01, convidando o algoritmo a não utilizar este valor durante a seleção, pois o candidato viola a restrição.

Por fim, como temos um problema de maximização, a variável ***menor_fitness_já_visto*** tem valor -float ("inf"), para que esta seja facilmente substituida pelo primeiro valor de fitness que o algoritmo achar.

<h4> Conclusao do Experimento </h4>

Após correr o algoritmo, podemos ver que este consegue resolver o problema da mochila respeitando as restrições impostas, mas pode não ser o método mais efetivo visto que realiza uma busca aleatória utilizanod os genes sorteados pelo módulo .random contendo valores e pesos. O estatabelecimento uma restrição para a execução do algoritmo foi crucial para que conseguíssemos encontrar um candidato válido para a resolução do problema, visto que sem ela, poderíamos facilmente cair em um candidato com itens de muito valor, mas excedendo o peso da mochila.

# Experimentos Extras

Nesta seção, temos alguns experimentos extras realizados, sua problemática e sua conclusão. Estes experimentos também se encontram neste repositório, nesta mesma pasta de Algoritmos Genéticos.

## Experimento GA.06 - Himmelblau e sua função

A função Himmelblau é uma função que possui 4 mínimos globais, e é utilizada justamente para o teste de algorítmos de otimização.

Esta função possui 4 mínimos, e o objetivo deste experimento é encontrar estes pontos mínimos, através de algorítmos genéticos.

Como tratamos de um problema de minimização, e vamos querer encontrar a distancia mínima dos pontos com o ponto mínimo global, podemos utilizar funções semelhantes às do experimento de senha e para minimização

Um ponto muito importante, é entender que **a própria função Himmelblau, quando receber os valores de X e Y, retornará um valor que será o fitness** usado para calcular o quão bom é aquele indivíduo para resolver nosso problema. Assim, passamos um indivíduo para a função Himmelblau, esta retornará um valor de fitness, e baseado em comparações dos fitness dos indivíduos que formam a população, encontraremos uma função na qual o fitness será 0, representando o mínimo global da função. 

<h4> Conclusão do Experimento </h4>

**O problema abordado neste experimento envolve o desenvolvimento de um método, via algoritmos genéticos, para se encontrar o mínimo global da função Himmelblau, função esta que possui 4 pontos de mínimo global idênticas. De inicio, percebe-se que o problema se trata de um problema de minimização, visto que queremos minimizar o valor de f(x) para até um par de pontos X e Y onde a derivada segunda seja igual a zero, caracterizando o ponto mínimo global. Com isso, tive como base um experimento já abordado anteriormente sobre descobrir uma senha devido à similaridade com este problema de minimização.**

**Para encontrar o mínimo, primeiro considerei que os valores que os genes podem assumir devem ser *.float*, o qual multipliquei por 10 para poder ter o valor dentro do range possível onde podem estar os valores de ponto mínimo.**

**Também alterei um pequeno parâmetro nas mutações para que o gene do indivíduo mutado seja um valor válido (.float multiplicado por 10)**

**Ao final, vemos que neste problema de minimização, o algoritmo consegue encontrar o ponto mínimo da função porém necessita de um número não tão baixo de gerações para que isto ocorra, mostrando que este algoritmo é probabilístico.
Outros métodos, como calcular a derivada segunda da função podem ser mais eficientes, dada a ordem e a complexidade da função
