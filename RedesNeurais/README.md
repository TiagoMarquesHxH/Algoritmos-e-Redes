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

### Sinapses (Setas)
