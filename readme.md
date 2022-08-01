# Anotações JavaScript
Anotações de estudo sobre JavaScript, assuntos que tenho dificuldade, ou novos aprendizados.

# Tópicos
- [Destructuring](#Destructuring)

#### <a name="Destructuring"></a> Destructuring
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

const {name, age} = pessoa;          => Gustavo 21
const {instagram} = pessoa.links     => https://www.instagram.com/
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
  
  const {modelo, registro:{estado}} = veículo  => Uno Amazoanas
 ```
 
 **Exemplo 03:** Pode-se atribuir novos valores a **variáveis**.
 ```javascript
  const person = {
    name: 'Gustavo',
    age: 21
  }
  const {name: 'nome', age: 'idade} = person    => nome: 'Gustavo' idade: 21
 ```
 
 **Exemplo 04:** Destruturando um array, onde um elemento da matriz não seja pega, usa-se (,,).
 ```javascript
 const nome = ['Gustavo', 'Henrique', 'Souza']
 const [indice0,,indice2] = nome      => Gustavo Souza
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
    console.log('Nome :' +n+ ', Pai: ' +p)                => Nome: Gustavo, Pai: Pedro
  }                                                       => Nome: Felipe, Pai: Pedro
 ```
 
 
 
