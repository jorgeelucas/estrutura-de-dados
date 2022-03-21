# Api de Collections do Java
> Esse material tem como base o seguinte artigo: http://www.universidadejava.com.br/java/java-collection/

Com todas as estruturas de dados que conhecemos, o Java nos fornece uma api pronta para trabalhar com essas coleções de dados e suas diferentes estruturas.

<center><img src="https://differbetween.com/storage/img/images_3/java_collections_interview_questions.png"></center>

> Em azul as Interfaces e em amarelo as Classes.


Temos 4 os principais tipos de coleções `Set` (conjunto), `List` (lista), `Queue` (Fila) e `Map` (mapa), Que são todas interfaces e a partir delas temos muitas classes concretas que implementam varias formas diferentes de se trabalhar cada coleção.

Todas as Interfaces e Classes são encontradas dentro do pacote (package) `java.util`, embora a interface `map` não ser filha direta da Collection ela também é considerada uma coleção pela sua função.

### java.util.Collection

A interface `collection` define diversos métodos comuns que são implementados pelas classes que as representam, dentro das coleções são adicionados Objetos também chamados de elementos ou itens.

Alguns métodos que devem ser implementados por todas as subclasses da `collection` são:
* `add(Object e)` - Adiciona um objeto na coleção (cada estrutura vai ter sua própria estratégia de adição)
* `addAll(Collection c)` - Adiciona uma coleção de Objetos dentro da coleção
* `contains(Object o)` - Verifica se a coleção já contém o Objeto informado.
* `clear()` - Remove todos os objetos da coleção
* `isEmpty()` - Retorna um `boolean` informando se a coleção está vazia ou não.
* `remove(Object o)` - Remove um Objeto da coleção.
* `size()` - Retorna o tamanho da coleção.
* `toArray()` - Converte uma coleção em um vetor.


&nbsp;
## As principais implementações das interfaces

&nbsp;
### Interface List
> (java.util.List)

Uma lista é uma Coleção ordenada (as vezes chamada sequencia). As listas podem conter elementos duplicados e além dos métodos já existentes na `Collection` a interface `List` ainda incluir as seguintes operações:
*   `Acesso posicional`
    * Manipula um objeto acessado diretamente pelo seu índice. Isso nos métodos `get`, `set`, `add`, `addAll` and `remove`
*   `Busca`
    * Busca um elemento específico na lista e retorna o seu índice, os métodos de busca incluem `indexOf` and `lastIndexOf`
* `Iteração`
    * Herda as semanticas do `Iterator` para obter vantagem da sua busca sequencial, através do método `listIterator`.

Suas principais implementações são: 
* `ArrayList`
    * O mais utilizado
    * Mantém um array dinâmico internamente para performar em ações de acesso direto, sempre que é necessário o seu tamanho aumenta em _50%_ do tamanho da lista.
    * Maior performance nas operações de `get(int index)` - **O(1)** (acesso constante)
    * Não é sincronizada (thread-safe)
```java
List<Usuario> lista = new ArrayList<>();
```
* `LinkedList`
    * Usa um tipo de **Lista duplamente ligada** `(doubly-linked-list)` internamente
    * Maior performance em ações que manipulam algum elemento da coleção
    * Além da interface `List` também implementa a interface `Queue`, pode represetar uma fila também.
    * Não é sincronizada (thread-safe)
```java
List<Usuario> lista = new LinkedList<>();
```

> Em desuso temos também a implementação `Vector` que segue o mesmo princípio do `ArrayList` porém é _thread safe_ o que o torna mais lento nas operações.

> Uma ótima explicação sobre `LinkedList` e `ArrayList` está na resposta nesse link: https://stackoverflow.com/questions/322715/when-to-use-linkedlist-over-arraylist-in-java

&nbsp;
### Interface Set
> (java.util.Set)

A interface Set é uma coleção do tipo conjunto de elementos. As características principais deste tipo de coleção são: os elementos não possuem uma ordem de inserção e não é possível ter dois objetos iguais.

> Para um correto uso da interface _Set_ em objetos particulares é necessário sobrescrever o método `equals`

<center><img src="https://hermes.digitalinnovation.one/articles/cover/c327146b-3c4f-4fe6-8685-b311d9f703d8.png"></center>

Suas principais implementações são: 
* `HashSet`
    * Utiliza uma estratégia de _hash table_ para espalhamento
    * Não garante nenhuma ordem
    * Aceita valores do tipo Null
    * Não é sincronizada (thread-safe)
    * É a implementação mais performática por não ter ordem, natural, nenhuma e nem elementos duplicados
```java
Set<Usuario> conjunto = new HashSet<>();
```
* `TreeSet`
    * Os objetos inseridos nesse tipo de conjunto devem implementar a interface `Comparable`
    * Ordena cada elemento na inserção por elementos únicos
    * Não suporta elementos Nulos, caso tenha um elemento nulo é lançado `NullPointerException`
    * Ação de inserção lenta por ter a necessidade de reordenar, rápida na ação de leitura
```java
Set<Usuario> conjunto = new TreeSet<>();
```
* `LinkedHashSet`
    * Mantém a ordem de inserção dos objetos
    * A mistura com um pouco da performance da `hashset` e um pouco da ordenação do `treeset`
    * Utiliza _hash table_ para espalhamento.
```java
Set<Usuario> conjunto = new LinkedHashSet<>();
```

&nbsp;
### Interface Map
> (java.util.Map)

A interface `Map` é uma coleção do tipo mapa. As principais características deste tipo de coleção são: os objetos são armazenados na forma de chave-valor, não pode haver chaves duplicadas dentro do mapa.

Armazana dois tipo de elementos, um chave e um valor. O valor pode ser repetido mas a chave não

> Ao informar uma chave repetida ele sobrepõe o primeiro valor

Para localizar um objeto dentro do mapa é necessário ter sua chave ou percorra o mapa por completo.

### Uso

Como não herda de collections tem algumas diferenças, mas muita semelhança também.
Os principais métodos são;
*   `put(chave, valor)`
*   `get(chave)`
*   `containsKey(chave)`
*   `containsValue(valor)`
*   `remove(chave)`
*   `size()`
*   `keySet()`
    * Retorna um _set_ com as chaves do mapa, pode ser usado no _forEach_ para percorrer o _Map_
*   `EntrySet()`
    * Retorna um _set_ do objeto `Entry<K,V>` que tem os métodos `.getChave()` e `.getValue()` e também pode ser usado para percorrer o mapa com um _forEach_

Suas principais implementações são: 
* `HashMap`
    * O mais utilizado
    * Usa o conceito de _hash table_ para espalhamento
    * Maior performance nas operações de `get(chave)` - **O(1)** (acesso constante)
    * Permite chaves e valores nulos
    * Use-a quando preferir uma performance maior porém não precisa de ordem
```java
Map<String, Usuario> mapa = new HashMap<>();
```
* `TreeMap`
    * Além de implementar a interface `Map`, também implementa `NavigableMap` e `SortedMap`.
    * Usa o conceito de árvore rubro negra internamente.
    * Mantém a ordem natural dos objetos, ou `Comparator` especificado.
    * Permite somente valores nulos (Chaves nulas lancará `NullPointerException`)
    * Use-a quando preferir uma performance menor porém precisa de uma ordem pre-definida
```java
Map<String, Usuario> mapa = new TreeMap<>();
```
* `LinkedHashMap`
    * Usa o conceito de `(doubly-linked-list)` internamente
    * Maior performance em ações que manipulam algum elemento da coleção
    * Mantém a ordem de inserção dos elementos.
    * Permite chaves e valores nulos
    * Use-a quando preferir uma performance menor porém precisa da ordem de inserção

```java
Map<String, Usuario> mapa = new LinkedHashMap<>();
```

&nbsp;
#### Exemplos
Exemplo de inserir e obter um valor:
```java
// Para inserir um valor no map usa-se
mapaDeUsuarios.put("usuarioAdm", new Usuario("admin"));

// Para obter um valor deve informar a chave e ele retornará o objeto referenciado.
Usuario usuarioAdm = mapaDeUsuarios.get("usuarioAdm");

```

&nbsp;
### Interface Queue
> (java.util.Queue)

A interface `Queue` é uma coleção do tipo fila. As principais características deste tipo de coleção são: a ordem que os elementos entram na fila é a mesma ordem que os elementos saem da fila (FIFO - First In First Out), podemos também criar filas com prioridades.

<center><img src="https://media.geeksforgeeks.org/wp-content/cdn-uploads/20200903183026/Queue-Deque-PriorityQueue-In-Java.png"></center>


Suas principais implementações são: 
* `ArrayDeque`
    * O mais utilizado
    * Usa o conceito de _array dinamico_ internamente tornando as operações de acesso direto mais rápidas
```java
Queue<Usuario> fila = new ArrayDeque<>();
```
* `LinkedList`
    * Usa o conceito de _Doubly-linked-list_ internamente
```java
Queue<Usuario> fila = new LinkedList<>();
```
* `PriorityQueue`
    * Usa o conceito de _fila_ porém pode-se passar algum tipo de prioridade para entrar na ponta da fila.
    * Passa-se a prioridade com um `Comparator`
```java
Queue<Usuario> fila = new PriorityQueue<>();
```







