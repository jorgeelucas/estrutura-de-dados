## Aulas, Carga Horária e Duração

|          |2x na semana|3x na semana|
|----------|:----------:|:-----------:|
|Aulas     |8           |9            |
|Carga     |24h         |27h          |
|Duração   |4 semanas  |3 semanas    |

## Objetivos de Aprendizagem

O objetivo do módulo é que os alunos entendam os conceitos básicos de estrutura de dados,  podendo ser capaz de analisar, implementar e utilizar os principais tipos de estrutura para lidar com coleções de dados de diferentes volumes. Análise e conhecimentos da utilização de conceitos na linguagem de progração Java. Análise e performance de algoritmos.

## Projeto

Crie uma aplicação que receba uma grande quantidade de transações bancarias (agencia, conta, banco, titular, saque ou deposito, operador, data e hora e etc.) e organize todas essas operações por titular, ordene todas as operações por data e hora, elimine as operações duplicadas (quando têm o mesmo valor, tipo (saque, deposito), o mesmo operador e a mesma data e hora exata) e no final mostre o saldo final da conta após todas as transações. (todas as contas iniciam zeradas) 

Decida qual estrutura de dados utilizar para receber todas as transações, a melhor forma de ordena-las, uma boa estratégia para eliminar as operações duplicadas.

As transações viram de um arquivo .csv com tudo desordenado e várias operações duplicadas.

## Avaliação por Rubricas

As habilidades e competências a serem desenvolvidas neste módulo são as descritas a seguir:

- Listas, Pilhas, Filas e Arrays associativos
- Conjunto de dados
- Utilização de diferentes tipos de estruturas
- Algoritmos e estratégias de ordenação
- API de collections do Java
- Análise e complexidade de algoritmos com notação _Big O_


## Tabela de planejamento:

Módulo: [BE-JV-004] Estrutura de dados

<table>
<tr>
<th>Objetivos</th>
<th>Conteúdos</th>
<th>Bibliografia</th>
<th>Metodologia</th>
<th>Avaliação</th>
<th>Observações</th>
</tr>
<tr>
<td>
Introdução a estrutura de dados
<br/><br/>
Entendimento estrutura de dados com Java
<br/><br/>
Uso e implementação de Listas
<br/><br/>
Listas com Java
<br/><br/>
Uso e implementação de Pilhas e Filas
<br/><br/>
Pilhas e Filas com Java
<br/><br/>
Uso e implementação de Mapas, dicionário e árvore
<br/><br/>
Mapas com Java
<br/><br/>
Uso e implementação de Conjunto
<br/><br/>
Conjuntos com Java
<br/><br/>
Java Collections
<br/><br/>
Análise e complexidade de algoritmos com notação _big O_
<br/><br/>
Algotimos de ordenação
<br/><br/>
Ordenação com Java
<br/><br/></td>
<td>
Estrutura de dados e seus principais objetivos e operações
<br/><br/>
Implementações de LISTA LINEAR, LISTA LIGADA (singly linked list), LISTA DUPLAMENTE LIGADA (doubly-linked-list)
<br/><br/>
Array, Vector,ArrayList,LinkedList
<br/><br/>
Implementações e conceitos de Filas e Pilhas
<br/><br/>
Conceitos de LIFO e FIFO
<br/><br/>
Stack, Queue
<br/><br/>
Implementações e utilizações de Mapas, dicionários e Árvores de dados.
<br/><br/>
Map, Hashing e tabelas de Hash, Hash code e Equals
<br/><br/>
Implementações e conceitos de Conjunto de dados.
<br/><br/>
Hashset, LinkedHashSet
<br/><br/>
Análise e complexidade de algotimos com notação Big O
<br/><br/>
Algoritmos de ordenação, Bubble sort, Insertion sort, Selection sort, Recursividade e depois Quick sort
<br/><br/>
Ordenação com TreeSet e TreeMap.
Ordenação de estruturas como LinkedHashSet, HashSet, ArrayList, LinkedList.
<br/><br/>
</td>
<td>
Links:<br/><br/>
*   Data structures: https://medium.com/omarelgabrys-blog/diving-into-data-structures-6bc71b2e8f92
*   algoritmos de ordenação com java: https://www.youtube.com/watch?v=8zVdz6TyV_c&list=PLTLAlheiUm5FRR5BNn4iBFwzYHiNq2Iv2
*   Hash Map com java: https://www.devmedia.com.br/hashmap-java-trabalhando-com-listas-key-value/29811
*   Hashing com java: https://joaoarthurbm.github.io/eda/posts/hashtable/


<br/><br/>

Livros:<br/><br/>
Algoritmos: teoria e prática
<br/><br/>
Fácil Aprendizagem Estruturas De Dados e Algoritmos Java
<br/><br/>
Arquitetura limpa: O guia do artesão para estrutura e design de software
</td>
<td>
Listas de exercícios individuais<br/><br/>
Estudos de Caso em duplas (mini-projeto)<br/><br/>
Pesquisa individual na documentação<br/><br/>
</td>
<td>
Listas de exercícios<br/><br/>
Prova teórico-prática<br/><br/>
Projeto
</td>
<td>

</td>
</tr>
</table>

## Tabela de plano de aula:

<table>
<tr>
<th>Aula</th>
<th>Problema Gerador</th>
<th>Conceitos</th>
<th>Metodologia</th>
</tr>
<tr>
<td>Aula 1</td>
<td>Introdução e implementação de Listas</td>
<td>
Motivações de usar Listas<br/><br />
Conceitos de Listas<br/><br />
Diferentes tipos de listas<br /><br />
</td>
<td>
Estudo de caso:<br />
Como funciona internamente uma Lista Linear?
Como o Java representa uma lista linear?
Funionamento e principais operações do array.
<br /><br />
Expositiva:<br />
Implementação do array<br /><br />
Objeto vs array<br /><br />
Utilizando ArrayList em Java <br /><br />

Pesquisa individual:<br />
Descobrir na documentação/fóruns quando é necessário utilizar um array<br /><br />

Prático:<br />
Exercícios de fixação (Arrays e ArrayList)
</td>
</tr>
<tr>
<td>Aula 2</td>
<td>
Diferentes implementações de listas
</td>
<td>
Definição de lista ligada<br></br>
Definindo de lista duplamente ligada<br></br>
Principais diferenças entre lista linear vs lista ligada<br />
</td>
<td>
Estudo de Caso 1:<br />
Como funciona internamente uma Lista Ligada? <br />
Criando a própria implementação de lista ligada com Java.<br />
Como funciona internamente uma Lista Duplamente Ligada?<br />
Criando a própria implementação de lista duplamente ligada com Java.<br />
<br /><br />
<br /><br />
Expositiva:<br />
Utilizando LinkedList em Java<br />
Diferença entre ArrayList vs LinkedList<br />
<br /><br />
Prático:<br />
Exercícios de fixação (Quando decidir por um ou outro tipo de lista).<br />
</td>
</tr>
<tr>
<td>
Aula 3
</td>
<td>
Pilhas e Filas
</td>
<td>
Principais conceitos de Pilha?<br />
Principais conceitos de Fila?<br />
LIFO vs FIFO<br />
Principais utilizações de Pilhas no mundo real? (Pilha de livros, pilhas de prato)<br />
Desempilhar<br />
Principais utilizações de FILA (Fila de banco)<br />
<br /><br />
</td>
<td>
Estudo de Caso 1:<br />
Criar e desenvolver a nossa própria implementação de PILHA em Java seguindo os conceitos.<br />
Criar e desenvolver a nossa própria implementação de FILA em Java seguindo os conceitos.<br />
<br /><br />
<br /><br />
Expositiva:<br />
Utilizando java.util.Stack<br /><br />
Utilizando java.util.Queue<br /><br />
Utilizando PriorityQueue<br /><br />
Queue com LinkedList<br /><br />
java.util.ArrayDeque<br /><br />

Prático:<br />
Exercícios de fixação (Pilhas e Filas).<br />
</td>
</tr>
<tr>
<td>
Aula 4
</td>
<td>
Arrays associativos/dicionários/Map<br /><br />
</td>
<td>
Pares chave-valor<br />
Arrays associativos vs objeto<br />
Arrays associativos e suas principais atribuições<br />
Arrays associativos vs array<br />
<br /><br />
Estudo de Caso 1:<br />
Implementação do nosso próprio array associativo<br />
Como o Java repressenta arrays associativos<br />
<br /><br />
Expositiva:<br />
Java HashMap<br /><br />

Prático:<br />
Desenvolva uma agenda de contatos telefonicos utilizando um array associativo<br />
</td>
</tr>
<tr>
<td>
Aula 5
</td>
<td>
Hashing e hash tables<br /><br />
</td>
<td>
Por que usar HASH?
<br /><br />
Hash vs criptografia
<br /><br />
Hash table vs Arrays vs Listas ligadas
<br /><br />
</td>

<td>
Estudo de Caso 1:<br />
Implementando nossa própria tabela de dispersão.<br />
Como funciona o conceito de Hash table?<br />
hash table vs arrays e listas<br />
<br /><br />
Expositiva:<br />
hashcode e equals em Java<br /><br />
Java Hashmap<br /><br />

Pesquisa individual:<br />
Pesquisar vantagens e desvantagens da utilização de hash tables.<br /><br />
Prático:<br />
Exercícios de fixação
</td>
</tr>
<tr>
<td>
Aula 6
</td>
<td>
Conjuntos<br /><br />
</td>
<td>
Conceitos de conjuntos de números na matemática.<br /><br />
Diferença entre conjunto e listas<br /><br />
</td>

<td>
Estudo de Caso 1:<br />
Implementação do próprio conjunto de dados com Java.
<br /><br />
Expositiva:<br />
Utilizando Java HashSet<br /><br />
Utilizando Java LinkedHashSet<br /><br />
Utilizando Java TreeSet<br /><br />
ArrayList vs LinkedList vs HashSet<br /><br />
Principais diferenças Hashset vs LinkedHashset vs Treeset<br /><br />
Como o Treeset ordena os dados?<br /><br />
Como o LinkedHashset ordena os dados?<br /><br />
Qual estrutura de conjunto é mais performática na operação de adicionar?<br /><br />
Qual estrutura de conjunto é mais performática na operação de buscar determinado item?<br /><br />
Prático:<br />
Implemente uma agenda de contatos com Java utilizando uma ou mais estruturas de CONJUNTO
</td>
</tr>
<tr>
<td>
Aula 7
</td>
<td>
Java Collection<br /><br />
</td>
<td>
Classes e interfaces da Api de collections
interface Map
Vector
<br /><br />
</td>

<td>
Estudo de Caso 1:<br />
Principais diferenças entre LIST e SET.
interface Map
interface Collection.
java.util.Collections
java.util.Arrays
<br /><br />
Prático:<br />
Pesquisar e ler a documentação do Java collections
</td>
</tr>
<tr>
<td>Aula 8</td>
<td>
Notação Big O e algoritmos de ordenação<br /><br />
</td>
<td>
Classificação dos algoritmos
Análise de complexidade e performance de algoritmos
Algoritmos de ordenação
<br /><br />
</td>

<td>
Estudo de Caso 1:<br />
Análise de algoritmos
Implementação, vantagens e desvantagens BUBBLE SORT
Recursividade
Implementação, vantagens e desvantagens QUICK SORT

<br /><br />
Prático:<br />
Pesquisar e implementar INSERTION SORT e SELECTION SORT
Reduzir a complexidade de um algoritmo de grandeza quadrática (for dentro de for por todas os elementos)
</td>
</tr>
<tr>
<td>Aula 9</td>
<td colspan="3">Aula dedicada à devolutiva da avaliação por rubrica / auto-avaliação</td>
</tr>
</table>
