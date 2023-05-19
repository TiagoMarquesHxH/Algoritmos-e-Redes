# Experimentos de redes neurais artificiais

Aqui, se encontram diversos experimentos utilizando Redes Neurais para se compreender como estas funcionam e os mais diversos métodos que podem ser construídas.
A construção deste README tem como base o livro do [StatQuest](https://statquest.org/statquest-store/ "StatQuest Store")

## O que são Redes Neurais?

Antes de sua construção e a realização dos experimentos, é fundamental a compreensão do que será trabalhado. 

As Redes Neurais recebem dados e com estes dados tentam aprender seu comportamento para que consiga trabalhar melhor e fazer previsões com dados futuros, logo, faz parte de um dos métodos de `Aprendizado de Máquinas` e são o cerne do método de `deep learning`.
Estas redes, assim como os `Algoritmos Genéticos`, derivam de conceitos elaborados pela Biologia, os quais envolvem neurônios, sinapses e sinais mandados/recebidos por estes neurônios. Este sistema de comunicação neuronal pode ser representado na forma de grafos, onde os vértices representam os neurônios, as arestas representam as sinapses e os sinais transmitidos são os dados da rede. Porém, neste âmbito de Redes Neurais, é conveniente de nomear os vértices de `Nódulos` e as arestas de `Setas`.

### Os Neurônios (Nódulos)

Os neurônios são os responsáveis por armazenar os dados que serão passados por toda a rede, sendo divididos em três tipos:

- `Neurônios de Input`: Recebem os dados iniciais a serem passados para toda a rede, e seu conjunto forma a `camada de inputs`

- `Neurônios de Funções de Ativação`: Tratam os dados recebidos, adequando-os para sua finalidade. O conjunto destes neurônios formam a `camada oculta`.

- `Neurônios de Output`: Devolvem os dados após estes serem mandados pelos neurônios de input e tratados pelas funções de ativação. Seu conjunto forma a `camada de output`

### Funções de Ativação (g(x))

As funções de ativação se encontram nos neurônios da camada oculta, sendo responsáveis por transformar/fitar os dados recebidos. Existem inúmeras funções de ativação com cada uma tendo um formato diferente, fazendo com que uma rede neural que possua vários neurônios da camada oculta seja capaz de fitar quase qualquer dado que lhe seja passado.
Matematicamente, podemos visualizar da forma que, os dados recebidos (x) são passados para o neurônio da camada oculta, e ao recebê-los, o neurônio irá aplicá-los em uma função g(x), retornar o valor do dado quando aplicado em g(x) e adicionar um `viés` **b** específico daquele neurônio.

### Sinapses (Setas)

As sinapses tem a importante função de transportar os dados que os neurônios carregam, e durante o processo de transporte, um valor `peso` é atribuído. Os dados transportados podem então serem passados para os neurônios ocultos (que contém as funções de ativação), retornados como output, ou então sofrerem alterações matemáticas por meio de `operadores` matemáticos, como soma, multiplicação e divisão por exemplo.

## EM CONSTRUÇÃO

## Elaboração dos Experimentos
### Experimento R.02 - Introdução à Classes

Este experimento é voltado à aprendizagem de como se trabalhar com `classes`e entender seu funcionamento, bem como vinculá-la à construção de Redes Neurais Artificiais.

São abordados neste experimento os métodos `dunder`, definições de propriedades e métodos que não são dunder, e como alterar o estado da classe internamente e externamente.

#### Conclusão do Experimento

Neste primeiro experimento de Redes Neurais, abordamos o conceito de classes, que serão fundamentais para a construção de redes neurais desde as mais simples até as mais complexas.
Ao criarmos uma classe, podemos vê-la como uma `receita de bolo`, contendo todos os ingredientes para que o alimento seja preparado. Estes ingredientes são chamados de `objetos` da classe, e são funções especiais que contém argumentos como `self` (ela mesma), `métodos dunder` (double underscore) e argumentos ordinários, e as variáveis definidas em uma função são conhecidas como propriedades daquele objeto de sua classe.

Estas propriedades podem ser alteradas, fazendo com que assim alteramos o estado de uma classe. Estas alterações podem ser realizadas dentro dela mesma (preferencialmente) ou fora (não recomendável).

A partir dos vários testes realizados dentro deste experimento, vemos a importância de se compreender como funcionam as classes para que assim sejam utilizadas na construção de redes neurais. As classes nos permitem trabalhar com diversas `receitas` em um só algoritmo, facilitando a sua construção dado o grau de complexidade em se trabalhar com valores e dados da rede.

### Experimento R.03 - Construindo um grafo automaticamente

Este experimento aborda as etapas inicias para a construção de uma `rede neural` artificiall, e para isso, devemos construir um `grafo computacional` que permite que sejam realizadas as operações ao computar um valor da rede.

São abordados neste experimento, definições de métodos dunder como operadores, construção de `progenitores`, definição de `um operador mãe` e a plotagem de um grafo.

#### Conclusão do Experimento

Neste experimento, foi trabalhada a construção de grafos a partir de classes, incluindo alguns novos métodos necessários para se trabalhar com operações matemáticas. 

Nota-se que trabalhar com `grafos computacionais`é essencial para compreender como uma rede neural é articulada, e também é fundamental para o cálculo do `gradiente local`, permitindo assim que seja realizado um `back propagation`. A construção dos grafos é realizada de maneira automática, sendo necessário apenas informar os valores e rotular os vértices, pois todas as operações e passagem dos dados são realizadas automaticamente pelos operadores e métodos da classe `Valor`.

### Experimento R.04


