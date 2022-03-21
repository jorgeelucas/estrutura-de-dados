# Notação _Big O_

A notação Big O é uma das ferramentas mais importantes para analisar o custo de um algoritmo. É uma prática recomendada para engenheiros de software entendê-la bem.

Dito de modo um pouco mais simples, a notação Big O descreve a complexidade do seu código usando termos algébricos.

<center><img src="https://user-content.gitlab-static.net/877793a68158701e70cf47b6761414bcafe93d4b/68747470733a2f2f6d69726f2e6d656469756d2e636f6d2f6d61782f313230302f312a355a4c636933537552307a4d5f516c5a4f41447638512e6a706567"></center>

<center><img src="https://miro.medium.com/max/742/1*WBYUz6Lh2Z21DQnEk-MWFQ.png"></center>

<center><img src="https://www.sahinarslan.tech/static/b14f0f927757ce111e7338d849f219a5/17bda/big-o-table.jpg"></center>

### `O(1)`
`O(1)` tem a menor complexidade
Geralmente chamado de "tempo constante", se você pode criar um algoritmo para resolver o problema em O(1), isso é normalmente o melhor que você pode conseguir. 

constantes são funções que independente da quantidade de valores de entrada passados, a performance do tempo de resposta dela se manterá a mesma.

```java
int num = arrayDeNumero[8];
```

<center><img src="https://miro.medium.com/max/924/0*t3jRGWN090LHH92P"></center>

&nbsp;
### `O(log(n))`

**O(log(n))** ou complexidade `Logaritmica` é mais complexo do que **O(1)**, mas menos complexo do que polinômios
Como a complexidade geralmente está associada a algoritmos de dividir e conquistar, **O(log(n))** costuma ser uma complexidade boa que você pode alcançar em algoritmos de ordenação. **O(log(n))** é menos complexo que **O(√n)**, pois a função da raiz quadrada pode ser considerada um polinômio, onde o expoente é 0,5.

<center><img src="https://miro.medium.com/max/1018/0*5a1WQJGJeriFo4RT"></center>

&nbsp;
### `O(n)`

Os algoritmos **O(n)** ou algoritmos lineares ou funções lineares, são caracterizados por realizar uma interação com cada valor passado na entrada. Assim a quantidade de operações realizadas será correspondente ao número de valores informados.


```java
public void passarEmTodoArray(int[] arr, int tamanho) {
    for (int i = 0 ; i < tamanho ; i++) {
    ...
    }   
}
```

<center><img src="https://miro.medium.com/max/916/0*mKcEzZZTAtWuPj90"></center>


&nbsp;
### `Polinômios`
A complexidade dos **polinômios** aumenta de acordo com o aumento do expoente
Por exemplo, **O(n⁵)** é mais complexo que **O(n⁴)**. Devido à simplicidade disso, passamos por vários exemplos de polinômios nas seções anteriores.

&nbsp;
### Complexidades `Exponenciais`
**Exponenciais** têm maior complexidade do que polinômios, contanto que os coeficientes sejam múltiplos positivos de n
**O(2ⁿ)** é mais complexo que **O(n⁹⁹)**, mas **O(2ⁿ)** é, de fato, menos complexo que **O(1).** Geralmente usamos 2 como a base para exponenciais e logaritmos porque as coisas tendem a ser binárias em Ciência da Computação, mas os expoentes podem ser alterados mudando-se os coeficientes. Se não estiver especificada, assume-se que a base para os logaritmos seja 2.


```java
public boolean encontrarDuplicados(int[] numeros) {
    for (int i = 0 ; i < numeros.length ; i++) {
        for (int j = i+1 ; j < numeros.length ; j++) {
            if (numeros[i] == numeros[j]) {
                return true;
            }
        }   
    }
    return false;
}
```

<center><img src="https://miro.medium.com/max/918/0*6Nn_fhWn4KAnIArO"></center>

&nbsp;
### Complexidades `Fatoriais`
Fatoriais têm complexidade maior do que exponenciais
Se tiver interesse no motivo para isso, consulte a função Gama, que é uma extensão analítica de um fatorial. Uma pequena prova disso é que fatoriais e exponenciais têm o mesmo número de multiplicações, mas os números que são multiplicados crescem para os fatoriais, mas permanecem constantes para as exponenciais.


&nbsp;
### Algoritmos de ordenação

#####  `Insertion sort`
_insertion sort_ itera por todos os elementos da lista. Se o elemento for menor que o elemento anterior, ela insere o elemento antes do outro elemento até que ele seja maior que o elemento anterior.

<center><img src="https://www.freecodecamp.org/portuguese/news/content/images/2021/12/0_C9ork5K0ay7_CLBv.gif"></center>

Se o array já estiver ordenado inicialmente, não haverá trocas. O algoritmo vai iterar pelo array apenas uma vez, o que resulta em uma complexidade de O(n). Portanto, diríamos que a complexidade de tempo de melhor caso da insertion sort é O(n). Uma complexidade de O(n) também é conhecida normalmente como complexidade linear.

&nbsp;
#####  `Quick sort`
_quick sort_ terá de percorrer a lista no tempo O(n) se os elementos forem ordenados na ordem oposta, mas, na média, ele ordena o array no tempo O(n * log(n)). Em geral, quando avaliamos a complexidade de tempo de um algoritmo, vemos o seu desempenho no pior dos casos.

<center><img src="https://www.freecodecamp.org/portuguese/news/content/images/2021/12/0_C9ork5K0ay7_CLBv.gif"></center>

Se o array já estiver ordenado inicialmente, não haverá trocas. O algoritmo vai iterar pelo array apenas uma vez, o que resulta em uma complexidade de O(n). Portanto, diríamos que a complexidade de tempo de melhor caso da insertion sort é O(n). Uma complexidade de O(n) também é conhecida normalmente como complexidade linear.


&nbsp;
> Esse material tem como fonte: https://www.freecodecamp.org/portuguese/news/o-que-e-a-notacao-big-o-complexidade-de-tempo-e-de-espaco/#:~:text=1.-,O%20que%20%C3%A9%20a%20nota%C3%A7%C3%A3o%20Big%20O%20e%20qual%20a,valor%20espec%C3%ADfico%20ou%20ao%20infinito.