# Problema-do-Fluxo-maximo  
Trabalho final de Estrutura de dados sobre Grafos.    
Universidade Federal do Pará - UFPA  
Professor : Glauco Gonçalves  
Alunos : Michael André Costa, Fernando Farias Dimas  
O problema do fluxo Máximo (The Maximum Flow Problem)  
Considere uma rede direcionada (dígrafo) conectada, com 2 nós especiais
Denominados Origem e destino, associado a cada arco, a uma distância não negativa. O objetivo e encontrar o fluxo máximo na rede. Além disso o problema de fluxo máximo é uma poderosa ferramenta de modelagem, capaz de representar uma grande variedade de outros problemas.

Exemplos de aplicações:  
1° maximizar o fluxo de uma rede de distribuição (suprimentos) de uma companhia a partir de suas fabricas (fornecedores) para os seus clientes/fabricas.  
2° Maximizar o fluxo de óleo ou água através de um sistema de aquedutos ou oleodutos.  
3°Maximizar o fluxo de veículos através de uma rede de transportes.  
4° Maximizar o fluxo de pacotes em redes de computadores.  

Para resolver esse problema optamos por utilizar o algoritmo de Ford-Fulkerson  
Que consiste basicamente em:  
Dado um grafo que representa uma rede de fluxo onde aresta borda tem uma certa capacidade. Esse algoritmo também tem dois vértices origem ‘s’ e saída ‘t’ no grafo, a partir disso e possível encontrar o fluxo máximo possível de s para t com as seguintes restrições:

O fluxo em uma aresta não excede a capacidade dada da aresta.  
O fluxo de entrada é igual ao fluxo de saída para todos os vértices, exceto s e t.  
Exemplo com origem 0 e saída 5 – suas arestas com a capacidade máxima  
imagem 1

Aplicando o algoritmo de Ford-Fulkerson-fluxo máximo de 23
imagem 2

Para implementar esse algoritmo em Java vamos primeiro definir um conceito de Grafo Residual que é necessário e muito importante para entender a implementação.
O grafo residual de uma rede de fluxo é um grafo que indica o fluxo adicional possível. Se houver um caminho da fonte s ao sumidouro/saida t no grafo residual, é possível adicionar fluxo. Cada aresta de um grafo residual tem um valor denominado capacidade residual que é igual à capacidade original da aresta menos o fluxo de corrente. A capacidade residual é basicamente a capacidade atual da que a aresta consegue suportar depois de inserido ou não um certo fluxo.  
A capacidade residual é 0 se não houver aresta entre dois vértices do grafo residual. Podemos inicializar o gráfico residual como gráfico original, pois não há fluxo inicial e inicialmente a capacidade residual é igual à capacidade original. Para encontrar um caminho de aumento, podemos fazer um BFS do gráfico residual. Usando o BFS, podemos descobrir se há um caminho da fonte ao somidouro/saida. O BFS também constrói o array parent []. Usando o array parent [], percorremos o caminho encontrado e encontramos o fluxo possível por meio desse caminho, encontrando a capacidade residual mínima ao longo do caminho. Posteriormente, adicionamos o fluxo do caminho encontrado ao fluxo geral.  
Outra coisa importante é que precisamos atualizar as capacidades residuais no grafo residual. Nós subtraímos o fluxo do caminho de todas as arestas ao longo do caminho e adicionamos o fluxo do caminho ao longo das arestas reversas.Nosso codigo tambem adiciona o fluxo do caminho ao longo das aresta reversas porque talvez possa ser necessário utilizar o fluxo na direção reversa.
