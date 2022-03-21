# Arrays associativos (Maps), Dicionário e Hashing

Os arrays associativos nos dão a opção de usar um index customizado, são estruturas de conceito chave-valor, quando não queremos que os nossos index sejam somente numeros.


> É uma coleção de pares CHAVE-VALOR


&nbsp;
Essa descrição pode confundir um pouco com o conceito de objeto que já conhecemos, mas há algumas diferenças entre mapas e objetos;
* É possível definir o tamanho máximo de um mapa
* Os _maps_ podem aceitar qualquer tipo de dado para a chave (Objetos aceitam apenas strings ou symbols)
* Os _maps_ também podem ter uma performance melhor em buscas e manipulação de dados do que objetos pois utilizam referências para as chaves - semelhante aos ponteiros, as chaves apontam para o endereço de memória dos seus valores.


&nbsp;
```java
private final Map<Usuario> mapaDeUsuario = new HashMap<>();
```

&nbsp;
Para adicionar um objeto em um mapa no java temos o método _put(chave, objeto)_, e para buscar esse objeto temos o método _get(chave)_ que retorna o objeto associado àquela chave.

```java
mapaDeUsuario.put(1, usuario1);
Usuario usuario = mapaDeUsuario.get(1);
```


&nbsp;
#### A ordem dos elementos
Diferente de um array básico, no array associativo as chaves não ficam em uma ordem específica, porque ordem não é um conceito dos arrays associativos.

#### Chaves duplicadas
Da mesma forma que não tem um mesmo índice se repetindo num array básico, o array associativo também não tem suporte para isso, as chaves devem ser únicas em um mapa. No caso do Java quando é repetido a chave em um _map_ ele sobrepõe o primeiro item.

> A maioria dos arrays associativos, tanto chamados de _maps_ ou _dicionarios_ ou até mesmo _hashes_ são implementados usando uma estrutura de tabela de hash (hash table). Então vamos passar por hashing para poder entender um pouco mais.


&nbsp;
### Hashing
> Uma tabela de hash em português seria o equivalente á uma tabela de espalhamento.

&nbsp;
O conceito de hashing é muito valioso em computação, não somente para estrutura de dados mas também para segurança, criptografia, gráficos, audios e etc.

> É uma forma de transformar o nosso dado através de uma função, que vai retornar uma referência pequena e simples do nosso dado original.

> O hash é muito usado para senhas.

> A referência pode ser um Inteiro, ou letras e numeros etc.

##### Por que usar HASH
porque ser capaz de transformar nossos objetos em uma representação simples dele pode nos ajudar a encontra-lo em alguma localização de estrutura de dados.


&nbsp;
###### Exemplo
Pense que você tem que guardar milhares de certidões de nascimento, se você colocar todas em uma pilha gigantesca quando for solicitado alguma específica de uma determinada pessoa, você terá que passar de uma por uma em toda a pilha até encontrar, isso vai te consumir muito tempo e trabalho, não é? 

<center><img src="https://img.freepik.com/vetores-gratis/mulher-de-negocios-esta-carregando-documentos-mulher-de-negocios-carregando-uma-pilha-de-papel-o-conceito-de-negocio-tambem-sobrecarrega-o-trabalho-ilustracao-de-personagem-de-desenho-animado-em-vetor-plano_77116-812.jpg"></center>

A solução de espalhamento significa você, ao invés de guardar todas em uma pilha gigante, você separa (espalha) em varias pilhas e escolhe uma estratégia para as pilhas (hashing), no caso, você poderia separar pela letra inicial do nome de cada pessoa na certidão. 

<center><img src="https://files.construfacilrj.com.br/2015/10/arquivo-arquivador-arquivista.jpg"></center>

Agora quando for solicitado de alguma pessoa específica você não precisa procurar mais em todas as pilhas de certidões e sim somente na que é da letra do nome da pessoa solicitada, isso reduziria abtuptamente o seu trabalho. E quando mais você espalhasse, por uma estratégia bem definica, menor ficariam as pilhas de certidões e mais rápido você encontraria uma solicitada.


&nbsp;
##### Hash não é criptografia!

Funções _hash_ não são reversíveis; somente ida. Significa que você não pode converter um valor hash de volta ao seu original, algumas informações são perdidas quando faz o _hashing_ e tudo bem, é intencional.

<center><img src="https://miro.medium.com/max/1400/1*sKuWKnrNtBotrnTax9m83w.png"></center>


&nbsp;
##### Implementações de funções de _hashing_
Digamos que temos uma classe Pessoa definida, e queremos um hash dela. A função de hash deve retornar uma referência simples e específica desse objeto (geralmente um numero) para o objeto específico dessa classe. Esse número é gerado usando os dados do objeto pessoa (nome, sobrenome, idade e etc).

##### Regras do _hashing_
1. Se tivermos o objeto exatamente igual, com os mesos dados e fizermos o _hash_ mais de uma vez, espera-se que sempre seja gerado o mesmo valor de _hash_.
2. Se há dois objetos diferentes que você considera iguais, então eles devem retornar o mesmo valor de _hash_
3. Enquanto dois objetos iguais geram o mesmo valor _hash_ não é verdade que dois valores _hashs_ iguais são do mesmo objeto, pois o calculo pode ter situações específicas onde é gerado o mesmo valor. No nosso exemplo das certidões de nascimento, as letras são os nossos _hashs_ e as certidões os objetos - na pilha das certidões com a letra "A" temos André e Anna - são objetos diferentes mas geraram o mesmo _hash_ (no nosso caso a letra "A")


### Hash tables (tabelas de espalhamento)

&nbsp;
##### Hash table vs Arrays vs Listas ligadas
Uma grande diferença entre estruturas de _hash table_ e arrays e listas é que as estruturas que utilizam _hash table_ são extremamente mais rápidas em relação ás outras para buscar se um elemento existe ou não, para encontrar um determinado item ou adicionar e deletar itens.

##### Como funcionam?
<center><img src="https://miro.medium.com/max/1000/1*bDtDJ-JgV8BsxvOQFx7_jQ.png"></center>

Quando uma estrtura de _hash table_ é criada é separado alguns baldes (buckets) internamente separados pelo tipo de hash e cada um tem uma lista dos objetos, quando **adicionamos** um novo elemento ele busca pelo hash a lista dentro daquele balde e adiciona o item naquela lista interna do balde.

##### Exemplo

```java
estruturaHashTable.put(chave, valor);
```

internamente:
```java
int index = buscarHash(chave);

Usuario[] usuariosDoIndice = buscarNosBaldesOArrayDaqueleIndex(index);

adicionaValorNoArray(usuariosDoIndice, valor);
```


&nbsp;
Basicamente a mesma ideia quando vamos **acessar** um elemento, passamos o nosso elemento, ele gera o _hash_ busca o balde correspondente áquele _hash_ e faz uma busca linear somente naquela pequena lista.

<center><img src="https://miro.medium.com/max/1000/1*3Uzpz0rRxGhH_XlsmQyZvQ.png"></center>

> Para um correto uso da _hash table_ é necessário sobrescrever o método `hashcode`


