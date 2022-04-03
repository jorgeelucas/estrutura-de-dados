# Conjuntos (set)

> Para um correto uso da interface _Set_ em objetos particulares é necessário sobrescrever o método `equals`

Quando você só precisa de uma grande coleção de objetos sem se importar com a ordem desses objetos, você pode usar um conjunto, nas lingagens de programação é chamado de _SET_


> É uma coleção não ordenada de itens de elementos únicos. Ou seja, não é possível repetir o mesmo valor dentro de um array.

Não ordenada significa que não temos index como nos arrays básicos.

> Documentação da implementação de SET na oracle: https://docs.oracle.com/javase/tutorial/collections/implementations/set.html

&nbsp;
##### Exemplo
É perfeitamente possível criar um array com os seguintes valores:
```java
int[] numeros = {1, 1, 1, 2, 7, 5, 7, 8}
```

Porém, em um conjunto, não é possível repetir os valores. Não importa a ordem dos elementos.
A maioria das linguagens tem uma api nativa para lidar com conjuntos, no caso do Java é a interface _Set_ com alguma implementações, a mais conhecida delas é o _HashSet_

```java
Set<Integer> conjuntoDeNumeros = new HashSet<>(numeros);
// O resultado é {1, 2, 5, 7, 8}
```


&nbsp;
### Implementação dos _sets_
_Sets_ geralmente usam a mesma ideia das _hash tables_ na maioria das vezes, porém sem o conceito de chave-valor quando está usando um _set_ a chave é também considerada o valor

Então quando precisa buscar algum elemento específico dentro do _set_ é necessário ter o objeto que deseja buscar, a única razão para isso é verificar se o elemento existe ou não na coleção.

As implementações do _set_ podem conter uma árvore de busca binária para _sets_ ordenados ou _hash table_ para _sets_ não ordenados.


&nbsp;
### Vantagens dos _sets_
Diferente das outras estruturas o _set_ não aceita valores duplicados.

_sets_ são desenhados para serem rapidamente varridos para buscar um elemento ou verificar a existencia de um elemento dentro dele.

Ainda pode-se iterar sobre todos os elementos do _set_, só não temos garantia de ordem


&nbsp;
### Implementação própria de um conjunto

> Não é necessário ter sua própria implementação do conjunto, uma vez que, a maioria das linguagens já possuem sua própria implementação usando os melhores algoritmos e as melhores estratégias.

Para fins didáticos uma simples implementação do conjunto com java seria:

```java
public class ConjuntoDePessoas {
    private ArrayList<LinkedList<Pessoa>> espalhamento = new ArrayList<>();
    
    public ConjuntoDePessoas() {
        for (int i = 0 ; i < 26 ; i++) {
            espalhamento.add(new LinkedList<>());
        }
    }
    
    @Override
    public void adicionar(Pessoa pessoa) {
        if (!contem(pessoa)) {
            int indice = calculaIndiceTabela(pessoa.getNome());
            LinkedList<Pessoa> lista = espalhamento.get(indice);
            lista.add(pessoa);
        }
    }
    
    private boolean contem(Pessoa pessoa) {
        int index = calculaIndiceTabela(pessoa.getNome());
        return espalhamento.get(index).contains(pessoa);
    }
    
    @Override
    public Pessoa buscar(String nome) {
        int indice = calculaIndiceTabela(nome);
        for (Pessoa pessoa : this.espalhamento.get(indice)) {
            if (pessoa.getNome().equalsIgnoreCase(nome))
                return pessoa;
        }
        throw new RuntimeException("Pessoa não encontrada");
    }
    
    // O espalhamento é feito de acordo com as letras
    private int calculaIndiceTabela(String nome) {
        return nome.toLowerCase().charAt(0) % 26;
    }
}
```

> Apoio: https://www.devmedia.com.br/diferencas-entre-treeset-hashset-e-linkedhashset-em-java/29077