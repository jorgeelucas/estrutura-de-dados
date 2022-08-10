# Api de Collections do Java

Com todas as estruturas de dados que conhecemos, o Java nos fornece uma api pronta para trabalhar com essas coleções de dados e suas diferentes estruturas.

> Segundo a [documentação](https://docs.oracle.com/javase/8/docs/api/java/util/Collection.html), uma `Collection` representa um grupo de objetos, conhecido por seus elementos. Em que algumas permitem elementos duplicados e outras não, algumas são ordenadas e outras não.

<center><img src="https://differbetween.com/storage/img/images_3/java_collections_interview_questions.png"></center>
**Figura 1** – _https://differbetween.com/storage/img/images_3/java_collections_interview_questions.png_ 

&nbsp;
> Em azul as Interfaces e em amarelo as Classes.

Temos quatro tipos de coleções: `Set` (conjunto), `List` (lista), `Queue` (Fila) e `Map` (mapa). Todas são interfaces, e a partir delas, temos muitas classes concretas que implementam várias formas diferentes de trabalhar cada coleção.

Todas as interfaces e classes são encontradas dentro do pacote `java.util`. Embora a interface `map` não seja filha direta da `Collection`, ela também é considerada uma coleção pela sua função.

### Iterable

A interface `Iterable` nos ajuda a iterar sobre a nossa coleção. Ela tem quatro métodos:

* `hasNext()` - Retorna _true_ enquanto a coleção ainda tem elementos a serem iterados.
* `next()` - Retorna o próximo elemento da coleção.
* `remove()` - Remove o último elemento retornado da coleção.
* `forEachRemaining(Consumer<? super E> action)` - Dada uma ação, esse método a executa para os elementos restantes até que todos os elementos sejam processados.

> documentação: https://docs.oracle.com/javase/8/docs/api/java/util/Iterator.html

### Collection

Logo abaixo, herdando de `Iterable` temos a interface `Collection`. Segundo a documentação, ela é a interface raiz na hierarquia da **API de Collections do java**, portanto ela contém os principais métodos comuns. A JDK não fornece nenhuma implementação direta dessa interface ainda, portanto teremos implementações somente de suas sub-interfaces.

* `add(E elemento)` - Adiciona um elemento à coleção;
* `addAll(Collection c)` - Adiciona uma coleção inteira na coleção;
* `clear()` - Remove todos os elementos da coleção;
* `contains(Object elemento)` - Retorna _true_ se a coleção já contém o elemento especificado;
* `isEmpty()` - Retorna _true_ se a lista não contém elementos;
* `remove(Object elemento)` - Remove o elemento especificado da coleção;
* `size()` - Retorna o tamanho da coleção;

Essa é a lista de alguns dos principais métodos da interface `Collection`. Todos os seus métodos e mais detalhes são encontrados na [documentação oficial](https://docs.oracle.com/javase/8/docs/api/java/util/Collection.html)

## List, Queue, Set

Essas três interfaces herdam os métodos comuns que tem na `Collection`, porém a partir de agora elas começam a se especializar, ou seja, cada uma tem sua própria forma de armazenar os elementos e podem fazer sobrecarga de alguns métodos.

### List

`List` é usada quando a necessidade é uma coleção ordenada que aceita elementos duplicados. Além dos métodos herdados de `Collection` é adicionado novos métodos, através de sobrecarga, com base em índices, por exemplo o método `add(int indice, E elemento)` que adiciona um elemento no índice especificado.
*   `Acesso por posição`
    * Manipula um objeto acessado diretamente pelo seu índice. Isso nos métodos `get`, `set`, `add`, `addAll` and `remove`;
*   `Busca`
    * Busca um elemento específico na lista e retorna o seu índice, os métodos de busca incluem `indexOf` and `lastIndexOf`;
* `Iteração`
    * Herda as semânticas do `Iterator` para obter vantagem da sua busca sequencial, através do método `listIterator`.

As duas principais implementações dessa interface são:

* `ArrayList` - É implementada usando um `array` redimensionável como estrutura, e toda vez que o seu limite é atingido, todos os elementos são copiados, automaticamente, para um novo array com maior capacidade. Essa implementação é bem performática para encontrar elementos, pois todos estão armazenados ordenadamente pelo índice, já a operação de **adicionar** ou **remover** pode não ser tão performática pois para adicionar, talvez seja necessário fazer uma cópia de todo _array_ para um maior, e para remover é necessário reordenar todos os elementos. 

```java
List<String> lista = new ArrayList<>();
```

> mais detalhes podem ser encontrados [na documentação do ArrayList.](https://docs.oracle.com/javase/8/docs/api/java/util/ArrayList.html)


&nbsp;
* `LinkedList` - Essa classe implementa `List` e `Queue`, e é implementada usando uma estrutura conhecida como [`Doubly-linked list`](https://en.wikipedia.org/wiki/Doubly_linked_list). É uma boa opção quando a necessidade é adicionar ou remover elementos constantemente, porém todas as operações que atuem em algum índice específico é necessário percorrer a lista desde o começo ou a partir do fim, dependendo de qual esteja mais perto da posição solicitada.

```java
List<String> lista = new LinkedList<>();
```

> Essa interface também é utilizada para estruturas do tipo **Fila**.

> [documentação da LinkedList.](https://docs.oracle.com/javase/7/docs/api/java/util/LinkedList.html)


&nbsp;
* Em desuso temos também a implementação `Vector` que segue o mesmo princípio do `ArrayList` porém é _thread safe_ o que o torna mais lento nas operações.

### Queue

> (java.util.Queue)

A interface `Queue` é uma coleção do tipo **fila**. As principais características deste tipo de coleção são: a ordem em que os elementos entram na fila é a mesma ordem que os elementos saem da fila (_FIFO - First In First Out_)e podemos também criar filas com prioridades.

<center><img src="https://media.geeksforgeeks.org/wp-content/cdn-uploads/20200903183026/Queue-Deque-PriorityQueue-In-Java.png"></center>
**Figura 2** – (Fonte da imagem: [geeksforgeeks](https://media.geeksforgeeks.org/wp-content/cdn-uploads/20200903183026/Queue-Deque-PriorityQueue-In-Java.png))


Os métodos principais para fazer bom uso dessa interface são um pouco diferentes dos comuns, segue:

* `offer(E elemento)` - Insere um elemento no final da fila;
* `poll()` - Retorna o primeiro elemento da fila e o remove;
* `peek()` - Somente retorna o primeiro elemento da fila sem removê-lo.

Suas principais implementações são: 
* `ArrayDeque`
    * O mais utilizado;
    * Utiliza o conceito de _array dinâmico_ internamente tornando as operações de acesso direto mais rápidas.
```java
Queue<String> fila = new ArrayDeque<>();
```
* `LinkedList`
    * Utiliza o conceito de _Doubly-linked list_ internamente.
```java
Queue<String> fila = new LinkedList<>();
```
* `PriorityQueue`
    * Utiliza o conceito de _fila_, porém permite passar algum tipo de prioridade para entrar na ponta da fila.
    * Passa-se a prioridade com um `Comparator`.
```java
Queue<String> fila = new PriorityQueue<>();
```

> [Documentação de Queue.](https://docs.oracle.com/javase/8/docs/api/java/util/Queue.html)

### Set

Similar à `List` porém nesse tipo de coleção não é permitido elementos duplicados e os elementos não têm ordem garantida. Representa um conjunto de elementos, e também não possuem uma ordenação no armazenamento dos dados.

> [Documentação de Set.](https://docs.oracle.com/javase/8/docs/api/java/util/Set.html)

Suas principais implementações são:

* `HashSet` - Utiliza uma estratégia de _HASH TABLE_ para espalhamento dos elementos armazenados, portanto utiliza o método `hashcode()` para encontrar os objetos com maior eficiência. Não garante ordem alguma dos seus elementos. Se houver necessidade de garantir a ordem dos elementos nessa estrutura usa-se `LinkedHashSet`, onde a ordem de inserção é garantida.

```java
Set<String> conjunto = new HashSet<>();
```
```java
Set<String> conjunto = new LinkedHashSet<>();
```

* `TreeSet` - Essa estrutura implementa a interface `SortedSet`. Usa-se quando há necessidade de armazenar os objetos em uma ordem específica, por exemplo ordem alfabética, para isso todos os elementos dessa coleção devem implementar a interface `Comparable` e definir a forma de ordenação. Não podemos ter elementos nulos nesse tipo de estrutura, caso contrário é lançada uma exceção (**NullPointerException**) na inserção. A ação de inserir é lenta pela necessidade de uma ordenação específica. 

```java
Set<String> conjunto = new TreeSet<>();
```

### Map

O `Map` é um tipo de coleção especial usado quando é preciso armazenar elementos em um formato de chave-valor, um exemplo seria salvar alguns CPF`s, poderíamos identificar cada cpf com o nome da pessoa.

> cpf -> chave, nome -> valor

O valor pode ser repetido mas a chave não, para localizar um objeto dentro do mapa é necessário ter sua chave ou percorrê-lo por completo.

> Ao informar uma chave repetida ele sobrepõe o primeiro valor.

Como não herda de `collections` os métodos são diferentes. Os principais métodos são;
*   `put(chave, valor)` - Insere o elemento e sua chave na coleção;
*   `get(chave)` - Obtém o elemento daquela chave da coleção.
*   `containsKey(chave)` - Retorna _true_ se a coleção contém aquela chave;
*   `containsValue(valor)`- Retorna _true_ se a coleção contém aquele valor;
*   `remove(chave)` - Remove o elemento e sua chave da coleção.
*   `size()` - Retorna a quantidade de elementos na coleção.
*   `keySet()` - Retorna um _set_ com as chaves do mapa, pode ser usado no _forEach_ para percorrer o _Map_
*   `EntrySet()` - Retorna um _set_ do objeto `Entry<K,V>` que tem os métodos `.getChave()` e `.getValue()` e também pode ser usado para percorrer o mapa com um _forEach_


&nbsp;
Assim como as outras interfaces, `Map` tem suas próprias implementações, que são:

* `HashMap` - Utiliza uma estratégia de _HASH TABLE_ para espalhamento dos elementos armazenados, portanto utiliza o método `hashcode()` para encontrar os objetos com maior eficiência. Não garante ordem alguma dos seus elementos. Se houver necessidade de garantir a ordem dos elementos nessa estrutura usa-se `LinkedHashMap`, onde a ordem de inserção é garantida.

```java
Map<String, String> mapa = new HashMap<>();
```
```java
Map<String, String> mapa = new LinkedHashMap<>();
```


* `TreeMap` - Utiliza um algoritmo conhecido como `Red-Black tree` para gerenciamento dos objetos. Mantém a ordem dos elementos pela chave, portanto é necessário que as chaves implementem a interface `Comparable` ou segue a ordem natural passada por um `Comparator` na sua criação. Essa implementação garante um custo de tempo linear (_O log(n)_) para as operações `containsKey`, `get`, `put` e `remove`

```java
Map<String, String> mapa = new TreeMap<>();
```


> [Documentação de Map.](https://docs.oracle.com/javase/8/docs/api/java/util/Map.html)


## Referências

[Java Collection.](http://www.universidadejava.com.br/java/java-collection/) Universidade java. Acesso em: 10/08/2022.

[Java Util API.](https://docs.oracle.com/javase/8/docs/api/index.html) Oracle. Acesso em: 10/08/2022.
. Acesso em: 9/06/2022.

[O básico sobre Collections no Java.](https://brs-caique.medium.com/o-b%C3%A1sico-sobre-collections-no-java-dd2240605522) Medium. Acesso em: 10/08/2022.

[Java Collections Framework - Collections in Java With Examples.](https://medium.com/edureka/java-collections-6d50b013aef8) Medium. Acesso em: 10/08/2022.
