# Pilhas, Filas e Arvores

## 1. Pilhas
(Stack)
> Pilhas seguem o conceito de **LIFO** - em inglês é a sigla para __last in, first out__ que significa o último a entrar é o primeiro a sair.

Semelhante aos arrays e listas, pilhas e filas são também uma coleção de itens, porém tem o conceito para lidar com a ordem de inserção e remoção.

&nbsp;
Em java a implementação é **Stack**
```java
private final Stack<Usuario> pilha = new Stack<>();

pilha.push(usuario);
pilha.pop();
pilha.peek();
```

Pense em uma pilha de pratos no restaurante, quando colocamos um prato na pilha, na ordem natural, colocamos em cima do último prato colocado, quando queremos desempilhar removemos também o prato de cima.

<center><img src="https://miro.medium.com/max/960/1*VvQLK70kFScVO6CN9VoBPg.jpeg"></center>

> São coleções de itens onde adicionamos e removemos itens do topo da pilha

### Uso

A pilha é bastante usada na área de ciência da computação, um uso bem comum da pilha é o famoso Ctrl + Z nos editores de código por exemplo. Você escreve um codigo e ele coloca a sua última ação no topo da pilha, se você fizer um ctrl+z ele só remove o que foi adicionado por último, ou seja, o que está no topo da pilha.

### Operações básicas da Pilha
As operações básicas da pilha são: _push()_, _pop()_, _peek()_

**PUSH** = Para adicionar um elemento ao topo da pilha.
**POP** = Para retornar (e remover) o elemento do topo.
**PEEK** = Enquanto _peek_ apenas retorna o último elemento sem remove-lo.

### Implementação
As pilhas são facilmente implementadas usando um array ou uma lista ligada

```java
public class PilhaDeUsuarios {

    private final LinkedList<Usuario> usuarios = new LinkedList<>();
    
    public void push(Usuario usuario) {
        this.usuarios.add(usuario);
    }
    
    public Usuario pop() {
        Usuario usuarioDoTopoRemovido = this.usuarios.removeLast();
        return usuarioDoTopoRemovido;
    }
    
    public Usuario peek() {
       Usuario usuarioDoTopoSemRemover = this.usuarios.get(this.usuarios.size() - 1);
        return usuarioDoTopoSemRemover;
    }
}
```

## 2. Filas
> (Queue)
A grande diferença da Fila para a Pilha é o seu conceito, a Pilha segue _LIFO_ enquanto a fila segue o conceito de _FIFO_, O primeiro a entrar é o primeiro a sair.


&nbsp;
Em java uma implementação valida é **ArrayDeque**
```java
private final Queue<Usuario> fila = new ArrayDeque<>();

fila.add(usuario);
fila.remove();
fila.peek();
```

> Também é possível usar a implementação de **LinkedList** para usar a fila.

Pense como uma fila de pessoas, a pessoa que chegou primeiro será a primeira a ser atendida.

<center><img src="https://img.freepik.com/vetores-gratis/fila-de-caixa-eletronico-desenho-animado-esperando-na-fila-do-caixa-eletronico_181313-593.jpg?size=626&ext=jpg"></center>

### Uso

As filas são muito utilizadas em situações de concorrencia para manter rastro das tarefas que ainda estão esperando para serem consumidas e garantir que sejam utilizadas na ordem que foram chamadas.

<center><img src="https://user-content.gitlab-static.net/22b02c77e6347c0ef9d70956958b731d499958a4/68747470733a2f2f75706c6f61642e77696b696d656469612e6f72672f77696b6970656469612f636f6d6d6f6e732f7468756d622f352f35322f446174615f51756575652e7376672f36303070782d446174615f51756575652e7376672e706e67"></center>

##### - __Priority queues__
O java ainda nos fornece a implementação das filas com prioridade, que segue o mesmo conceito da fila, mas tem, em lingagem popular, aquele caixa eletrônico para pessoas com prioridade. Ou seja, as tarefas seguem sendo feitas em ordem de fila (FIFO) porém se houver alguma tarefa com maior prioridade, ela passa na frente das demais.

```java
private final PriorityQueue<Usuario> filaComPrioridade = new PriorityQueue<>();
```

> Para definir a prioridade o java usa a implementação de alguma função c __Comparator__ ou __Comparable__, assim como quando vamos fazer a ordenação dos elementos, passando nossa própria lógica para definir algum item com prioridade.


### Operações básicas da Fila
As operações básicas da pilha são: add()_, remove()_, _peek()_

**ADD** = Para adicionar um elemento ao final da fila.
**REMOVE** = Para retornar (e remover) o primeiro elemento.
**PEEK** = Enquanto _peek_ apenas retorna o primeiro elemento sem remove-lo.

### Implementação
Assim como as pilhas, as filas podem ser facilmente implementadas usando um array ou uma lista ligada


```java
public class FilaDeTarefas {

    private final LinkedList<Tarefa> tarefas = new LinkedList<>();
    
    public void add(Tarefa tarefa) {
        this.tarefas.add(tarefa);
    }
    
    public Tarefa remove() {
        Tarefa tarefaDoTopoRemovido = this.tarefas.removeFirst();
        return tarefaDoTopoRemovido;
    }
    
    public Tarefa peek() {
       Usuario tarefaDoTopoSemRemover = this.tarefas.get(this.tarefas.size() - 1);
        return tarefaDoTopoSemRemover;
    }
}
```

> No JAVA ainda temos a implementação de **Deque**, pronuncia-se "DEK", ele é usado quando precisamos mesclar o poder da Stack (pilha) e da Queue (fila) e usar juntos. Com ela podemos adicionar ou remover tanto do começo quando do final da estrutura.

## 3. Árvore

A árvore é uma estrutura não-sequencial, muito útil para armazenar dados de forma hierárquica e que podem ser acessados de forma rápida.

Pode-se definir árvore como uma coleção de dados representados por nós e arranjados em níveis hierárquicos (ao invés de sequências como as estruturas vistas anteriormente).

Um exemplo de estrutura em árvore são os organogramas de empresas:

<center><img src="https://www.alura.com.br/artigos/assets/estruturas-de-dados-introducao/imagem3.png"></center>

A estrutura mais comum é a árvore binária, que tem no máximo dois nós-filhos a partir do nó inicial (chamado de raiz ou root). Um nó pode ter pais, irmãos e filhos; nós que têm pelo menos um filho são chamados de nós internos, e nós sem filhos são chamados de externos ou folhas:

<center><img src="https://www.alura.com.br/artigos/assets/estruturas-de-dados-introducao/imagem4.png"></center>

A partir da estrutura de árvore binária (com um nó-filho à esquerda e um à direita da raiz) é possível estruturar a chamada BST, ou árvore de busca binária (binary search tree), que utiliza o princípio do algoritmo de busca binária para estruturar os dados de forma que valores menores estejam à esquerda da raiz e valores maiores à direita. Essa união do algoritmo com a estrutura de dados leva a uma maior eficiência na manipulação de dados, seja para buscar, alterar, incluir ou remover elementos.


> fonte: https://www.alura.com.br/artigos/estruturas-de-dados-introducao


