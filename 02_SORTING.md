# Sorting (ordenar)

Ordenar é sempre uma operação custosa computacionalmente e sempre que for necessária  queremos minimizar esse custo. Então tenha em mente o tamanho coleção e quantas vezes ela será ordenada, isso pode levar a diferentes algoritmos de ordenação.

<center><img src="https://miro.medium.com/max/1400/1*3GQEtOjUcPDPxJMEl5a0kA.png"></center>

### As funcionalidades de ordenação do array
Quando queremos ordenar um array temos que entender como o nosso framework faz isso. Primeiro ele verificará a quantidade de dados que temos e, automaticamente, escolherá o algoritmo de ordenação mais adequado.
Depois temos que saber se será ordenado no array existente ou criado um array cópia para isso, a maioria das lingagens vai tentar ordenar o array já existente, enquanto poucas vão criar uma cópia do original para conter o array ordenado.

### Ordenando nossos próprios objetos
Como o java é uma linguagem orientada a objetos, certamente vamos querer ordenar nossos próprios objetos, não somente arrays de tipos primitivos ou _Strings_

Quando for solicitado para ordenar nossos objetos, a linguagem certamente não vai saber como fazer isso por si só, devemos ensina-la como fazer isso.

Então se precisamos ordenar Usuarios pelo id, nome ou data de nascimento a linguagem não vai saber a ordem que queremos e nem os atributos que queremos.

Em java ao implementar a interface Comparable passando nosso tipo no _generics_ temos um método que ensina o java em qual ordem deve ser colocado os nossos itens.

```java
public class Usuario implements Comparable<Usuario> {
...
@Override
public int compareTo(Usuario other) {
    return other.getNome().compareTo(this.getNome());
}
```

## Buscando em um array

Se quisermos saber se um valor específico existe no nosso array ou não, podemos fazer um _loop_ sobre cada elemento e verificar cada item até encontrar ou não.

No melhor cenário o item vai estar na primeira posição e logo encontraremos ele, para o pior cenário o item pode estar na última posição ou nem mesmo existir isso custaria passar por todos os itens, imagina se tivermos milhoes de dados?

Esse tipo de busca é chamado de busca linear ou sequencial e são metodos de força bruta.

Enquanto buscas lineares são simples de entender e fáceis de escrever elas ficam mais lentas conforme a quantidade de dados aumentam.

### Busca em arrays ordenados
Se não houver ordenação ou nenhuma sequencia pré-definida no array, então não há outra forma do que verificar cada elemento do array.

Mas se estiver ordenado, ou mesmo se tiver alguma sequencia pré-conhecida então temos opções de buscas melhores de buscar do que busca linear, como por exemplo, [busca binária](https://pt.khanacademy.org/computing/computer-science/algorithms/binary-search/a/binary-search#:~:text=A%20busca%20bin%C3%A1ria%20%C3%A9%20um,localiza%C3%A7%C3%B5es%20poss%C3%ADveis%20a%20apenas%20uma.).

Então os dados devem estar ordenados para que possamos usar algum algoritmo de busca mais eficiente do que uma simples busca linear/sequencial

### O desafio das estrutura de dados
Muitas vezes concordamos em usar um simples algoritmo lento, porque a unica forma de melhorar isso é ordenando o nosso array, o que também vai adicionar um custo na performance e, simplesmente, não vale a pena!

Então se é necessário buscar no array uma única vez é melhor ter uma complexidade de **O(n)** para uma busca linear do que **O(NLogN)** para ordenar + **O(LogN)** para buscar. Porém se no lugar de uma única busca, é necessário varias buscas então deve-se ordenar uma vez e agora ficar buscando da coleção ordenada com **O(LogN)** em todas as buscas no lugar de **O(N)** da busca linear

>Não há uma estrutura de dados igualmente boa para todas as situações. Uma estrutura ordenada naturalmente requer menos tempo em buscar um elemento, porém mais tempo para inserir pelo fato de manter a ordenação enquanto um array simples requer mais tempo para buscar e pouquissimo tempo para inserir no final.

> Na seguinte playlist no youtube você encontra mais informação e algoritmos já conhecidos e testados de ordenação; https://www.youtube.com/watch?v=8zVdz6TyV_c&list=PLTLAlheiUm5FRR5BNn4iBFwzYHiNq2Iv2