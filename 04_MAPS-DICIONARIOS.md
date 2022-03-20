# Arrays associativos (Maps), Dicionário

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