
Anotações de estudo sobre JavaScript, assuntos que tenho dificuldade, ou novos aprendizados.

# Tópicos
- [Destructuring](#Destructuring)
- [IF-ELSE, ELSE IF](#IF-ELSE)
- [Estrutura de repetição: WHILE, DO WHILE](#WHILE)
- [Estrutura de repetição FOR, FOR...IN, FOR...OF](#FOR)
- [setInterval e clearInterval, setTimeout e cleearTimeout](#setInterval)
- [This](#This)
- [Callback](#Callback)
- [Função Construtora](#FuncoesConstrutoras)
- [Class](#Class)

## <a name="Destructuring"></a> Destructuring
> É uma expressão que permite extrair dados de um array ou objeto de em variáveis distintas. 

**Exemplo 01:** Destruturação de elementos de um objeto.


```javascript
const pessoa = {
  name: "Gustavo",
  age: 21,
    links: {
      instagram: "https://www.instagram.com/",
      site: "https://www.google.com/"
    }
}

const {name, age} = pessoa;         // => Gustavo 21
const {instagram} = pessoa.links    // => https://www.instagram.com/
 ```
 
 **Exemplo 02:** Destruturação de elementos mais profundos de um objeto.

 
 ```javascript
  const veiculo = {
    marca: "Fiat",
    modelo: "Uno",
      registro: {
        cidade: "Manaus",
        estado: "Amazonas",
        país: "Brasil"
      }
  }
  
  const {modelo, registro:{estado}} = veículo 		// => Uno Amazoanas
 ```
 
 **Exemplo 03:** Pode-se atribuir novos valores a **variáveis**.
 ```javascript
  const person = {
    name: 'Gustavo',
    age: 21
  }
  const {name: 'nome', age: 'idade} = person   // => nome: 'Gustavo' idade: 21
 ```
 
 **Exemplo 04:** Destruturando um array, onde um elemento da matriz não seja pega, usa-se (,,).
 ```javascript
 const nome = ['Gustavo', 'Henrique', 'Souza']
 const [indice0,,indice2] = nome     // => Gustavo Souza
 ```
 
 **Exemplo 05:** Destruturação objetos interaveis, qualquer tipo de coisa que conseguimos fazer um laço sobre, exemplo: array, objeto etc.
 ```javascript
  const pessoas = [
    {
    nome: 'Gustavo',
      familia: {
        pai: 'Pedro',
        mae: 'Nilse'
      },
      idade: 21
    },
    {
    nome: 'Felipe',
      familia: {
        pai: 'Pedro',
        mae: 'Regina'
      },
      idade: 25
    }
  ]
  
  for(const {nome: n, familia:{pai: p}} of pessoas){
    console.log('Nome :' +n+ ', Pai: ' +p)               // => Nome: Gustavo, Pai: Pedro
  }                                                      // => Nome: Felipe, Pai: Pedro
 ```
 <hr>
 
 ## <a name="IF-ELSE"></a> IF, ELSE, ELSE IF
 > IF: Para especificar um bloco de código a ser executado se uma condição específica for verdadeira.
 ```javascript
 let idade = 18
    if(idade >= 18){
      return true            // => true
    }
 ```
 > ELSE: Bloco de código a ser executado, se a primeira for condição for falsa.
 ```javascript
 let idade = 17
    if(idade >= 18){
      return true            // => 
    } else {
      return false           // => false
    }
 ```
 > ELSE IF: Especifica uma nova condição a ser testada se a primeira confição for falsa.
 ```javascript
 let idade = 17
 let acompanhado = true
    if(idade >= 18){
      return true                                      // => 
    } else if(idade =< 18 && acompanhado == true){
      return true                                      // => true
    }
 ```
 <hr>
 
 ## <a name="WHILE"></a> Estrutura de repetição: WHILE, DO WHILE.
> WHILE: Pecorre um bloco de código enquanto uma condição específica for verdadeira. While primeiro verifica a condição, e depois executa o código.
```javascript
let contador = 0
  while(contador < 10){
    contador++                   // => 9
  }
```
> DO WHILE: Bloco de código é executado uma vez e repetido enquanto a condição for verdadeira.
```javascript
let i = 0
  do{
  console.log('Olá')
  i++
  } while(i < 10)
```
<hr>

 ## <a name="FOR"></a> Estrutura de repetição: FOR, FOR...IN, FOR...OF.
 > FOR: Pecorre um bloco de código varias vezes.
 
 > Sintaxe: for(inicialização; condição; expressão final) - todas as três expressões na condição do loop são opcionais. No bloco de inicialização, não é necessário inicializar variável por exemplo.
 ```javascript
 let i = 0
  for(; i < 9; i++){
    console.log(i)               // => 0 1 2 3 4 5 6 7 8
  }
 ```
 > FOR...IN: Pecorre as propriedades de um objeto.
 
 > Sintaxe: for(key in object)
 ```javascript
 const monstros = {
  canada: 'sasquatch',
  nepal: 'yeti',
  scotland: 'loch ness monster'
 }
  for(let nomeMonstros in monstrons){              // => sasquatch
    console.log(monstros[nomeMonstros])            // => yeti
  }                                                // => loch ness monster
 ```
 > FOR...OF: Permite fazer um loop sobre estruturas de dados interaveis como arrays, strings, maps, nodelist e etc.
 
 > Sintaxe: for(variavel of iteravel)
  ```javascript
//em Array
  const carros = ['bmw', 'volvo', 'mini']
    for(let nomeCarros of carros){                  // => bwm
      console.log(nomeCarros)                       // => volvo
    }                                               // => mini
// em String
  const stg = 'luana'
    for(letras of stg){
      console.log(letras)                          // => l u a n a 
    }
  }
```

  <hr>
  
 ## <a name="setInterval"></a> setInterval( ) e clearInterval( ), setTimeout( ) e clearTimeout( ).
 
 
>**setInterval( ):** Método chama uma função em intervalos específicos em milissegundos. Função continua até clearInterval( ) ser chamado.
 ```javascript
 //suponha que há uma div criada no HTML com o ID: quadrado, medidas de 100px por 100px. E que tenha dois botões com IDs: btn1, btn2.
 
let temp
function mudarCor(){                                        // muda a cor do quadrado.
    const div = document.getElementById('quadrado')
    let r = Math.floor(Math.random() * 255)                   
    let g = Math.floor(Math.random() * 255)               // gerando cor aleatoria rgb. 
    let b = Math.floor(Math.random() * 255)                                         
    div.style.backgroundColor = "rgb("+r+","+g+","+b+")";
}

function iniciar(){
    temp = setInterval(mudarCor,2000)        // função iniciar vai chamar a função mudarCor a cada 2 segundos.
}

function parar(){
    clearInterval(temp)                     // para de chamar temp que está responsavel por iniciar a função mudarCor.
}

function addEventos(){                     // responsavel por adicionar evento aos botões.
    document.getElementById('btn1').addEventListener('click', iniciar)
    document.getElementById('btn2').addEventListener('click', parar)
}

window.addEventListener('load', addEventos)  // quando a página carregar a função de eventos já estará disponivel.
 ```
> **setTimeout( ):** Executa algo específico assim que o tempo que foi passado expirar.
```javascript
function saudar(){
    console.log('olá gustavo')      
}

const ativar = setTimeout(saudar, 3000)   // executa a função saudar em 3 segundos.

function parar(){
    clearTimeout(ativar)                 // para a constante ativar, que está responsavel por chamar a função saudar.
}

document.getElementById('btn').addEventListener('click', parar)
```

<hr>

 ## <a name="This"></a> This
 > **This:** Em uma função padrão, **this** pode variar seu resultado.
 
 > Referência ao **this** sempre se refere a (e contém o valor de) um objeto.
 
 > Em um método de objeto, this refere-se ao objeto.
 
 > Em uma função, this refere-se ao objeto global.
 
 > Em uma função no strict mode, this é undefined.
 
 > Em um evento, this refere-se ao elemento que recebeu o evento.
 
 > As arrow functions não vinculam seus próprios this, em vez disso, eles herdam o escopo do pai, que é chamado de escopo léxico.
 ```javascript
 const diaAdia = {
  saudacao: 'Bom dia',
    falar(){
      console.log(this.saudacao)    // this está no contexto diaAdia
    }
 }
 ```
 > **This** funciona dentro de contexto. Para dar contexto ao **this**, usa-se .bind( )
 ```javascript
  const diaAdia = {
    saudacao: 'Bom Dia',
        falar(){
            console.log(this.saudacao)
        }
}

const falar = diaAdia.falar.bind(diaAdia)
falar();
 ```
 
 <hr>
 
 ## <a name="Callback"></a> Callback
 > O que caracteriza um uma callback, é passar uma função como argumento para outra função, e executa-la durante o código.
 ```javascript
 function saudacao(nome){
    console.log('Olá', nome);
}

function entradaDoUsuario(callback){
    let nome = prompt('Nome por favor')
    callback(nome)
}

entradaDoUsuario(saudacao)  
 ```
  ```javascript
function exibePrimeiraMensagem (mensagem, callback) {
	console.log(mensagem);
	callback();
}
function exibeSegundaMensagem(){
	console.log('Essa é a segunda mensagem do novo exemplo');
} 
exibePrimeiraMensagem ('Essa é a primeira mensagem do novo exemplo', exibeSegundaMensagem);  
 ```
 
 <hr>
 
 ## <a name="FuncoesConstrutoras"></a> Funções Construtoras
 > A função construtora serve de molde para criação de objetos.
 
 ```javascript
 function CadastroVeiculo(marca, modelo, ano){
	this.marca = marca
	this.modelo = modelo
	this.ano = ano
	this.statusCadastro = () => 'Ativo'
}

const palio = new CadastroVeiculo('Fiat', 'Palio', 2009)		
console.log(palio)

/*CadastroVeiculo {
  marca: 'Fiat',
  modelo: 'Palio',
  ano: 2009,
  statusCadastro: [Function (anonymous)]
}*/
 ```
 
 <hr>
 
 ## <a name="Class"></a> Class
 > Class são modelos para objetos JavaScript
 
 > Class não sofre hoisting.
 ```javascript
 class Livro {
	constructor(nome, editora, paginas){
		this.nome = nome
		this.editora = editora
		this.paginas = paginas
	}
	anunciarTitulo(){
		console.log(`Título: ${this.nome}`)
	}
	descreverTituilo(){
		console.log(`${this.nome} é um livro da editora ${this.editora}, e contém ${this.paginas} páginas`)
	}
}

const mindhunter = new Livro('MindHunter', 'Intrínseca', 374)
mindhunter.anunciarTitulo()					// => Título: MindHunter
mindhunter.descreverTituilo()					// => MindHunter é um livro da editora Intrínseca, e contém 374 páginas
 ```

 
 
 
 


 
 
 
