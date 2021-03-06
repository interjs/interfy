# Esse é o tutorial da versão 2, pretendes ler o da versão 1? Clica em [v1](https://github.com/DenisPower1/interfy/tree/main/tutorial/pt/v1)
#### Esse tutorial pressupõe que você tenha pelo menos conhecimento intermediário em Javascript.

## Introduçao
A Interfy é uma biblioteca Javascript que nos entrega um sistema de roteamento robusto para aplicações web front-end. Ela foi feita especialmente para ser uma opção mais robusta ao [roteador](http://interjs.epizy.com/v1/tutorial/pt/roteador) do [Inter](https://github.com/DenisPower1/inter).
Apesar de fazer parte do ecossistema do Inter, ela pode ser usada sem o Inter!

Ela é:

*	Fácil
*	Divertida
*	Simples
*	Robusta

## Instalação
##### A Intefy deve ser usada em páginas que usam o protocolo http ou https.
Para instalares a Interfy é muito simples, basta importares ela para a tua página a partir de uma tag script:
#### Usando CDN
```html
<script src="https://cdn.jsdelivr.net/gh/DenisPower1/interfy@2.0.1/interfy.g.min.js"></script>
```
#### Usando localmente

Você pode baixar o *source* do Interfy clicando em [baixar](https://github.com/DenisPower1/interfy/releases/download/v2.0.1/interfy.g.min.js).


## Sintaxe.

A Intefy dá-nos um constructor chamado Interfy, quando ele (o constructor) for instanciado vai nos fornecer os seguintes métodos:
*	route() – É usado para registar uma rota. Ele recebe dois argumentos, o primeiro argumento deve ser a rota que será registada, o segundo deve ser a função que será executada quando a rota for requisitada.
*	start() – É usado para anicializar o roteador. Ele aceita opcionalmente uma função como o seu argumento, e a referida função será executada toda vez que uma rota for requisitada, ela será executada com um argumento que vai indicar a rota requisitada.
*	setPath() – É usado para trocar a url, e a mesma url será requisitada(no roteador criado pela biblioteca). Ele apenas aceita um argumento, que deve ser a rota que será requisitada e deve começar com /.
*	useHash – Também é usado para trocar a url, mas a url usará cerquilha, ex: /#/user/8389.
* version - É uma propriedade só de leitura, que retorna a versão do Inter instalada.


### Exemplo:

```javascript

// Instanciando o Interfy()
const int=new Interfy();

// Registando a rota /
int.route("/", ()=>{

console.log("A rota / foi requisitada")

})

int.route("/user/(id)", (o)=>{

// Executa quando a rota /user/qualquerinformação for requisitada

console.log(`Id do user :${ o.var.id}`) 

})

int.route("/?q=*", (o)=>{

console.log(`Pesquisando por: ${o.param.q}`);

})

// Inicializando o roteador.
int.start()

// Trocando a rota
int.setPath("/?q=Interfy") // Pesquisando por: Interfy

```

Está tudo super claro não é? Principalmente se você trabalha com o Javascript no back-end a sintaxe deve ter soado muito familiar para ti!

Na segunda rota registada(/user/(id)), a rota tem uma sub rota variável. A rota pode ser:

* /user/39393
* /user/904093
* /user/020331 

Como você deve ter notado, a sub rota da rota */user* que é a /(id) vai ser dinámica, e para nós obtermos a sub rota dinámica, nós usamos o conceito de variáveis. O (id) indica que aquela sub rota vai estar variando(vai ser dinámica), e aquela sub rota será chamada *id*, a função que será executada quando a referida rota for requisitada, será executada com um argumento, que será um objecto que terá duas propriedades a *var* e a *param* e essas mesmas propriedades serão também objectos. As propriedades do objeto *var* serão os nomes das variáveis e os valores serão obviamente os valores das variáveis. Por exemplo

```javascript

int.setPath("/user/38958") // Id do user: 38958 

```

Na terceira rota(/?q=*) o asterisco significa qualquer coisa, essa rota tem uma queryString, quando uma rota tiver uma queryString, os nomes das propriedades do objecto *param*, serão os nomes dos parámetros da queryString e os valores, serão os valores dos respectivos parámetros. No exemplo, o parámetro é o "q", se nós requisitássemos essa rota da seguinte forma:

```javascript

int.setPath("/?q=routing lib")

``` 

O valor do parámetro "q" seria "routing lib".

E quando uma rota tiver apenas o asterisco, significa que quando for requisitada uma rota que não está registada no roteador a sua função será executada, indicando um NOT FOUND.

```javascript

int.route("*", ()=>{

console.log("A rota não foi encontrada!")

})

```



## Versão Modularizada

A partir da versão [2.1.0](https://github.com/inter-frame/interfy/releases/tag/v2.1.0), nós podemos usar modulos no Interfy basta fazer o seguinte:

#### CDN

```javascript

import {Interfy} from "https://cdn.jsdelivr.net/gh/DenisPower1/interfy@2.1.0/module/interfy.m.js"

const int=new Interfy();

int.route("/", ()=>{})

```

#### Localmente

Baixe a versão modularizada clicando em [baixar](https://github.com/inter-frame/interfy/releases/download/v2.1.0/interfy.m.js)


```javascript

import {Interfy} from "./interfy.m.js"

const int=new Interfy();

int.route("/", ()=>{})

```

Simples né? O nosso tutorial fica por aqui, qualquer dúvida abra um issue descrevendo a tua dúvida, e se você gostou da biblioteca faça o favor de estrelar esse repositório.

Você também pode dar uma olhada no [Inter](https://github.com/DenisPower1/inter).


## Seja feliz!
