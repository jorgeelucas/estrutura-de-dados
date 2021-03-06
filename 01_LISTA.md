# Arrays, Listas ligadas e duplamente ligadas

## 1. Arrays

O array é fundamental e a estrutura de dados mais usada em todas as lingagens de programção.

> Um array é uma coleção ordenada de itens, onde cada item tem um indice

<center><img src="https://docs.oracle.com/javase/tutorial/figures/java/objects-tenElementArray.gif"></center>

Por ordenada, entenda uma lista onde os valores sempre são acessados na mesma ordem, sempre começando do zero, por exemplo, o primeiro elemento sempre será o indice zero, o segundo elemento sempre será o indice um e assim por diante.

Por ser muito usado, o array já vem implementado no java e disponibiliza algumas operações como _length_ para saber o tamanho do nosso array (lembre-se, o tamanho e não a quantidade de objetos). Também em Java o array pode se aplicar para qualquer classe ou tipo primitivo da linguagem.

```java
// Formas possíveis de declarar um array em java
int[] numeros;
int []numeros;
int numeros[];

// Para instanciá-lo é necessário:
numeros = new int[10];
```
> No Java o array possuí um tamanho fixo, passando na sua inicialização e não pode ser alterado posteriormente.

## 2. Listas

Listas são estruturas simples que alocam os itens de forma separada e sequencial

> É uma coleção de itens (nós) ordenados em uma sequencia linear

> Os nós não ficam armazenados próximos uns dos outros na memória como no array.

#### Arrays vs Listas
A lista é um tipo diferente de estrutura de dados do array.

A grande diferença é a ideia do acesso direto vs sequencial, o array permite as duas formas enquanto a lista só permite o acesso sequencial. A lista não suporta indices como o array.

### 2.2 Listas ligadas
> A lista ligada é uma coleção de nós/elementos onde um nó tem um valor e o endereço do próximo nó. (singly linked list)

<center><img src="https://miro.medium.com/max/816/1*CJ27twE8azv289_SNvd0iQ.png"></center>

###### O ultimo elemento deve apontar para nulo.
Veremos como seria representado cada nó/elemento em java:


```java
public class Elemento {
    private Usuario usuario;
    private Elemento proximo;
    ...
}
```

Pela forma como é construído a lista ligada requer bem menos tempo para adicionar ou remover elementos do que no array.

Quando o array adiciona ou remove algum elemento do meio ele tem que __"afastar"__ os elementos para a direita ou esquerda para manter a ordem, até mesmo quando adicionar no final pode ser necessário realocar os dados para um array maior, pois o tamanho dele é imutável, custando bem mais tempo e performance de processamento.

### 2.3 Listas duplamente ligadas
> (doubly linked list)

Semelhante a lista ligada, é separada e sequencial porém além de apontar para o próximo elemento, a lista duplamente ligada também aponta para o elemento anterior, permitindo assim percorre-lá tanto do começo ao fim tanto do modo reverso. 

<center><img src="https://miro.medium.com/max/1220/1*MQXQEng-gv6FDdFozbAsOg.png"></center>

Isso torna as operações de remover ainda mais rápidas que a lista ligada porque na _singly_ você precisa saber o nó/elemento anterior ao elemento atual para poder deletar.

Representamos um elemento de uma _doubly linked list_ em Java com o seguinte código:

```java
public class Elemento {
    private Usuario usuario;
    private Elemento proximo;
    private Elemento anterior;
    ...
}
```

> Esse material foi baseado nos seguintes artigos: 
 - https://medium.com/omarelgabrys-blog/diving-into-data-structures-6bc71b2e8f92
 - https://medium.com/omarelgabrys-blog/data-structures-a-quick-comparison-6689d725b3b0