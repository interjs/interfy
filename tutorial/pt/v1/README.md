## Esse é o tutorial da versão 1, para a versão 2 aceda [v2](https://github.com/DenisPower1/interfy/edit/main/tutorial/pt/v2/README.md)
###### Esse tutorial pressupõe que você tenha pelo menos conhecimento intermediário em Javascript.

### Esse tutorial está completamente desatualizado, aprenda a versão 2 do Interfy!

Para começar a usar o **Interfy** é muito simples, basta você importar ele em sua página a partir de uma tag script.

## Instalação

 ### Usando CDN

```Javascript
<script src="https://cdn.jsdelivr.net/gh/DenisPower1/interfy@1.0.1/interfy.js"></script>
```

Você também pode baixar o arquivo js para poderes usar localmente, clique em [baixar](https://github.com/DenisPower1/interfy/releases/download/v1.0.1/interfy.min.js)

## Usando

O Interfy dá para nós um constructor, chamado **Interfy** e quando nós instanciarmos ele, teremos os seguintes métodos.

* createRouter() - É usado para criar o roteador, ele apenas aceita uma função como o seu argumento, a referida função será executada toda vez que uma requisição for feita.
* setPath() - Esse método é usado para mudar de rota, e a rota deve ser o argumento desse método, a rota deve começar com /.
* useHash() - Esse método tem um funcionamemnto idêntico ao *setPath()*, a diferença é que usamos ele quando queremos que as rotas tenham cerquilha (#), ex:/#/user/93939.

### Exemplo

```Javascript

const int=new Interfy();

// Cria o router.

int.createRouter((req)=>{

alert(req.url) // Exibe a url requisitada.

//req.url == /paises/angola.

})

int.setPath("/paises/angola")


```

Isso que nós vimos é o básico da biblioteca.

### Varíaveis.

No Interfy variável é usada para ler rotas dinámicas.

Por exemplo temos a seguinte rota: */africa/pais* a rota principal é */africa* e a sub rota(rota filha) é */pais*, só que essa sub rota
será variável(vai alternando). Ela pode ser:

* /africa/angola
* /africa/mozambique
* /africa/zambia

Então, para nós sabermos qual é a sub rota dinámica (rota filha) de uma determinada rota devemos usar a váriavel.



```Javascript


const int=new Interfy();

int.createRouter((req)=>{

const sub_rota=req.is("/africa/(pais)");

if(sub_rota){

const oPais=req.getVar("/africa/(pais)").pais.

alert(oPais) // Vai exibir o valor da variável pais.

// opais == angola

}

})

int.setPath("/africa/angola")


```


Tá tudo explicíto né? Agora vamos conhecer profundamente o parámetro **req** que está sendo muito usado aqui.

O req seria uma abreviação para requisição ou request, ele é um objecto que tem alguns métodos e propriedade que vão nos fornecer mais informações sobre a url requisitada.

### url 

É uma propriedade só de leitura, que nos permite obter a rota requisitada.

### is() 

É um método que nos permite verificar a estrutura da rota(quando ela tem sub rotas váriaveis), se a estrutura for verdadeira retorna true caso o contrário retorna false.



```Javascript



int.createRouter((req)=>{

const id_do_usuario=req.is("/user/(id)");
// Se a rota for /user/38849 ou user/48894 ou qualquer mas que tenha  esssa estrutura(/user/qualquerValor) 
// o método vai retornar true.

})
```

E nós podemos usar o asterístico para significar qualquer coisa.

```Javascript



int.createRouter((req)=>{

const rota=req.is("/info/*");

if(rota){

// A rota é /info/qualquercoisa por exemplo : info/2021/inter-o-framework-js-simples.

}


})
```


### getVar() 

É um método que nos permite ler as variáveis da rota requisitada, ele recebe apenas um argumento, que deve ser a rota com as variáveis e esse método vai retornar um objecto em que as propridades são os nomes das váriaveis e os valores são os valores das variáveis.

O nome da variável deve estar entre parênteses ex:(nome).


```Javascript

const int=new Interfy()

int.createRouter((req)=>{

const id_do_usuario=req.is("/user/(id)");

if(id_do_usuario){

const id=req.getVar("/user/(id)").id;

alert(id) // vai exibir o valor da variável id.

//id == 38849444

}

})

int.setPath("/user/38849444");

```

As rotas podem ter quantas variáveis quiseres, e as variáveis devem estar em letras minúsculas.

## Conclusão

Viu como o Interfy é simples, intuitivo, pequeno e divertido? Gostou? Então deixe-me saber estrelando esse repositório e você também pode dar uma olhada no [Inter](https://github.com/DenisPower1/inter).


## Seja feliz.


