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

O algoritmo cumpre razoávelmente o objetivo de atingir os melhores candidatos através das gerações sucessivas, juntamente com as etapas de cruzamento, mutação e seleção, mesmo se o número de gerações não for muito grande. Porém, o fator mutação que pode ser benéfico ao mutar um gene 0 para 1 e facilitar a etapa de cruzamento, apresenta um risco bem relevante em seu funcionamento, pois pode interferir negativamente no algoritmo ao alterar o valor de um gene para 0 ao decorrer das gerações ou ao final da última geração, o que dificultaria a obtenção dos melhores candidatos finais;

Este algoritmo é probabilístico, pois se baseia muito em chances de variações ocorrerem (como a criação das gerações iniciais e probabilidades de mutação/cruzamento), e a população resultante, apesar de aparentar ser determinística após um grande número de gerações, irá variar quando o número de gerações for pequeno;

Ele é capaz encontrar os mínimos e máximos da função objetiva desde que haja um grande número de gerações;

Sem a etapa de mutações a população final seria obtida exclusivamente pelo cruzamento e seleção, e no caso onde a população inicial apresenta muitos indivíduos com genes 0, a população final não teria bons candidatos, que poderiam ter sido melhores caso as mutações pudessem acontecer e alterar genes beneficamente ao longo das gerações;

Com a mutação muito alta, obter uma população resultante na qual todos os indivíduos apresentam todos os genes possíveis como 1 seria impossível, pois como as mutações podem tanto beneficiar como prejudicar, alterações consecutivas nos genes tornariam as populações resultantes completamente aleatórias, aumentando conforme o número de gerações aumenta.

## Experimento A.04 - Problema das caixas não-binárias

Este experimento é diferente dos demais, pois aqui não consideramos caixas com valores de gene de apenas 0 ou 1, e sim qualquer valor inteiro que pertença ao conjunto [0, 100]. A finalidade ainda é a mesma, encontrar a melhor combinação de valores onde a soma destes deve ser a máxima possível.

Para isso, criamos novas funções semelhantes às dos problemas envolvendo caixas binárias, como as funções de gene, mutação, indivíduos e a função objetivo, com a diferença de incluirmos o método `.randint` selecionando valores aleatórios de 0 até o valor máximo da caixa (100). Também foram adicionados na função objetivo a soma dos genes do indivíduo para que assim seja possível obter o valor máximo.

<h4> Conclusão do Experimento </h4>

Este algoritmo também apresenta caráter probabilístico, pois ainda depende de um grande número de gerações para obter uma solução. Para este algoritmo tentar encontrar uma solução com valor máximizado de 400, ele necessitaria de gerações ainda maiores do que as caixas binárias visto os valores possíveis e a interferência das mutações nestes valores. Logo, não é um algoritmo muito eficiente para encontrar uma solução de máximização.

## Experimento A.05 - Descobrindo a senha

Agora, o problema o qual analisaremos será o de se descobrir uma senha qualquer, que inclua apenas as letras do alfabeto, e levando em consideração que nossa função objetivo já sabe qual a senha correta. 

Podemos construir funções que façam uma quantificação da distância entre o nosso palpite de senha e a senha correta, e para isso, definimos que cada letra da senha seja um gene, e então comparamos gene a gene a distância entre estes, baseado em uma variável que passa todas as letras possíveis para um gene poder assumir. Como queremos encontrar a senha, logo é fácil ver que estamos analisando um problema de `minimização`, pois queremos que a distância entre as letras palpitadas e as corretas sejam as menores possíveis, até o ponto em que seja zero, representando que aquela letra corresponde à letra da senha original naquela posição.

<h4> Conclusão do Experimento </h4>

Este experimento teve um grau de complexidade mais elevada do que os anteriores, necessitando que novas funções fossem criadas para atender os requisitos para a solução do problema. O método da função objetivo desta vez foi o contrário do que o do experimento anterior, pois neste comparamos as letras candidatas e as letras originais, e desejamos que a distância seja 0 entre elas, significando que a letra candidata corresponde à letra original. Ou seja, tratamos aqui de um problema de minimização, pois queremos a menor distância possível entre as letras, e no experimento anterior o problema tratado envolvia maximização. O algoritmo também apresenta caráter probabilístico, pois apesar de não termos um gerador de populações, temos um loop que irá gerar um indivíduo contendo letras aleatoriamente, e assim irá comparar com a senha original.

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
