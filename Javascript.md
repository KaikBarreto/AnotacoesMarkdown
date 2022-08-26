# **<center><font size="10"  color="lightblue">JavaScript</font></center>**

## <center> [Documentação JavaScript](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript)

## **Comandos var/let/const: declaração de variável**

* ### Number | converter pra numero
* ### parseInt | converter pra inteiro
* ### parseFloat | converter para Real
* ### String | converter para string 

***

## Estrutura Condicional Simples 

```javascript
if (condição1) {
    ação1()
}
else if (condição2) {
    ação2()
}
else {
    ação3()
}
```

***

## **Condição Múltipla/Switch Case**:

```javascript
switch (expressão) {
    case valor1:
        ação1()
        break

    case valor2:
        ação2()
        break

    case valor3:
        ação3()
        break

    default:
        ação4()
        break

}

(BREAK OBRIGATORIO)
```

***

## **Estrutura de Repetição**:

* ### **Teste Lógico no Início**

```javascript
while (condição=True) {
    realizarAção()
}
```

* ### **Exemplo**: 

    ```javascript
    var c = 1
    while (c <= 5) {
        console.log(`Passo ${c}`)
    }
    ```

* ### **Teste Lógico no Final**

    ```javascript
    do {
        realizarAção()
    } while (condição=True)
    ```

* ### **Exemplo**:

    ```javascript
    var c = 1
    do {
        console.log(`Passo ${c}`)
        c++
    } while (c <= 5)
    ```

### **Estrutura de repetição com variável de controle**

```javascript
for (inicio; teste; incremento) {
    realizarAção()
}
    ex: 
        for (var c=1; c <= 10; c++) {
            console.log(c)
        }
```

***

 ## **VETORES/ARRAYS EM JAVASCRIPT**

### Vetor/Array = Lista = [ ]

* ### Composto por elementos, os quais possuem keys (índices) e valores (conteúdo).

    ```javascript
    array.indexOf(valor) 
    ```

* ### Retorna o índice do array que possui o elemento 'valor'

***

## **OBJETOS EM JAVASCRIPT**

* ### Objetos são variáveis que contém propriedades e métodos 
    
* ### **Exemplo**:

    ```javascript
    dados = {
        nome:'Kaik', 
        idade: 16, 
        sexo: 'M', 
        nacionalidade:'Brasileiro',
        tossir: function() => {console.log("Cough Cough!")}
    }

    console.log(dados.) //  <= Retorna 'Kaik'
    dados.tossir() // Retorna 'Cough Cough!'
    ```

***

## **FUNÇÕES COM PARÂMETROS E RETORNO**

```javascript
function parimp(n) {    //função
    if (n % 2 == 0) {   // ação
        return 'PAR!'
    } else {
        return 'ÍMPAR!' // retorno
    }
}
let resultado = parimp(11)  // chamada, retorno = "ÍMPAR!"
```

***

## **CONDIÇÃO TERNÁRIA**

```javascript
(boolean) ? valor 1 : valor 2

(condição) seVerdadeiro retorna valor1 seFalso retorna valor 2
```

***

##  **THROW - TRY/CATCH** 

* ### **throw** = usado na função para exportar um erro.

* ### **try** = bloco onde será chamada a função que pode conter um erro

* ### **catch** = bloco onde o erro será recebido e utilizado

* ### **Exemplo**:

    ```javascript
    function sayMyName(name) {
        
        if(name === '') { // Validação
            throw "Nome não digitado" // O que será "jogado"
        }

        console.log(name)
    }

    try {
        sayMyName('')
    } catch(e) { // Capta o que foi jogado pelo throw
        console.log(e) // Imprime o que foi captado 
    }
    ```    

***

# <center><font color="orange">**Estrutura de dados com JavaScript**</font></center>

* ## O que é Estrutura de dados?

    * ### É uma maneira de organizar e ordenar informações como textos, números, booleanos etc. e registrá-los na memória do computador.

        ```javascript
        // Array
        [1, 2, 3] // elementos 1, 2, 3

        // Object
        { name: "Fulano", idade: 20 } // elementos name: "Fulano", idade: 20
        ```
## **<font color="pink">Gerenciando dados</font>**

### **_Estrutura de dados tem a ver com a gestão das informações da aplicação._**

### Para esse **gerenciamento**, podemos dividir em **3** etapas:

1. ### Modelar a estrutura;

2. ### Dar vida à estrutura (instanciar essa estrutura);

3. ### Criar as funcionalidades dessa estrutura
    * ### Exemplo: inserir, excluir, buscar, exibir, contar...

## <font color="orange">**Arrays**</font>

### Array, vetor ou arranjo, é uma estrutura amplamente utilizada e implementada em quase todas as linguagens de programação.

### Uma das estruturas mais básicas, simples de criar e utilizar.

```javascript
    ['a', 10, 'd', true] // total de 4 elementos
//    0   1    2    3     Index
```

### <font color="orange">**Características**</font>

* ### Acesso pelo índex

* ### Respeita a ordem de inserção dos elementos

* ### Aceita valores duplicados

* ### Dependendo do tamanho dos Arrays, para encontrar e/ou deletar um elemento, será necessário um uso maior de performance.

### <font color="orange">**Arrays no JavaScript**</font>

* ### São dinâmicos (todas as características já são definidas em sua declaração)

* ### Você poderá ter dados de diferentes tipos misturados dentro de um Array. Strings, numbers, booleans, objects, functions e até outros Arrays.

* ### Existem muitos métodos (funções) já implementados 

    * ### <font color="pink">push( ), pop( ), find( ), filter( )</font>

### <font color="orange">**Arrays no código**</font>

```javascript
const pilotos = ["Senna", "Prost", "Schumacher", "Hamilton"]

// A indexação (index) começa pelo número 0
console.log(pilotos[0]) // Senna
console.log(pilotos[3]) // Hamilton

// Acessar o tamanho do array
console.log(pilotos.length) // 4

// iterável
for(let piloto of pilotos) {
    console.log(piloto) 
} // Imprime, linha a linha, o nome de cada piloto.

// Adicionar elementos no array
pilotos.push("Alonso") // Agora a lista de pilotos conta com"Alonso na última posição

// Encontrar um elemento
const Senna = pilotos.find(piloto => piloto === 'Senna')
console.log(Senna) // Senna
```

## <font color="orange">**Matriz**</font>

### **_Matrix ou vetor multidimensional_**

### Nada mais é do que um Array que contém outros Arrays

* ### Podem ter muitos níveis, hierarquicamente.

```javascript
const students = [["Joseph", 23, "MG"], ["Briana", 22, "SP"], ["Priscilla", 23, "PR"]] 
// students = matriz

console.log(students[0][1]) // 23  (idade de Joseph (students[0]) )
```

## <font color="orange">**Stack**</font>

### **Tradução: Pilha**

### Como uma pilha de livros.

* ### Linear, um após o outro

* ### O último a entrar na pilha é o primeiro a sair

## <font color="orange">**Stack no código**</font>

### **Métodos fundamentais:**

* ### **push()**: adicionar um elemento à pilha

* ### **pop()**: remover o elemento do topo da pilha

* ### **peek()**: obter o elemento do topo da pilha

### **Outros métodos poderão ser implementados, como <font color="magenta">size()</font> para mostrar o tamanho da pilha**

```javascript
// Passo 1: modelando
class Stack() {
    constructor() {
        this.data = []
        this.top = -1
    }

    push(value) {
        this.top++
        this.data[this.top] = value
        return this.data
    }

    pop() {
        if (this.top < 0)  return undefined
        const poppedTop = this.data[this.top]
        delete this.data[this.top]
        this.top--
        return poppedTop
    }
    
    peek() {
        return this.top >= 0 ? this.data[this.top] : undefined
    }
}
// Passo 2: Utilizando
const stack = new Stack()

// adicionar dados
stack.push('learning')
stack.push('data')
console.log(stack.push('structures')) // ["learning", "data", "structures"]

console.log(stack.peek()) // "structures"
```

## <font color="orange">**Queue**</font>

### **Tradução: Fila**

* ### **Linear**
  
* ### **Conceitos:**

    * ### **FIFO [First In First Out]:**

      * ### O primeiro a entrar na fila é o primeiro a sair

    * ### **Front (Frente)**

      * ### é a referência do primeiro elemento a entrar na fila

    * ### **Back (Fundo)**

      * ### é a referência do último elemento a entrar na fila

    * ### **Enqueue**

      * ### entrando na fila

    * ### **Dequeue**

      * ###  saindo da fila

## <font color="orange">**Queue no código**</font>

### **Métodos Fundamentais**

* ### **enqueue()**: adicionar um elemento ao final da fila **_(Back)_**

* ### **dequeue()**: remover o primeiro elemento a entrar na fila **_(front)_**
  
### Outros métodos poderão ser implementados, como **<font color="cyan">size()</font>** para mostrar o tamanho da fila ou **<font color="cyan">front()</font>** para pegar o primeiro elemento da fila.

```javascript
// Passo 1: Modelando
class Queue {
    constructor() {
        this.data = []
    }

    enqueue(item) {
        this.data.push(item)
        console.log(`${item} chegou na fila!`)
    }
    
    dequeue(item) {
        this.data.shift()
        console.log(`${item} saiu da fila!`)
    
    }
}

// Passo 2: Utilizando
const fila = new Queue()

console.log(fila) // []

fila.enqueue("Mariana") // Mariana chegou na fila! =>   ["Mariana"]
fila.enqueue("João") // João chegou na fila! =>   ["Mariana", "João"]
fila.enqueue("Ariel") // Ariel chegou na fila! =>   ["Mariana", "João", "Ariel"]

fila.dequeue() // Mariana saiu da fila! =>   ["João", "Ariel"]
fila.dequeue() // João saiu da fila! =>   ["Ariel"]
fila.dequeue() // Ariel saiu da fila! =>   []
```

***

# <font color="orange"><center>**Programação Orientada a Objetos** _(POO)_<center></font>

### aka (Also known as) **Object-oriented  Programing** _(OOP)_ 

### O Termo refere-se a um <font color="cyan">Paradigma de desenvolvimento</font>

* ### Uma maneira de resolver um problema, um modo de pensar 

* ### Não está ligado somente à linguagem de programação, mas a um entendimento amplo e atemporal para criação de softwares.

## <font color="orange">**Qual a utilidade do paradigma de orientação a objetos?**</font>

* ### Aplicação de padrões de projetos;

* ### Organização do código;

* ### Melhor entendimento do código, pensando nele como um conjunto de objetos;

* ### Reutilização de código;

* ### Separar a complexidade, abstrair e expor de forma mais simples o código;

* ### Classificar as rotinas e trechos do código



# <center>**<font color="orange">Conceitos da POO</font>**</center>

## <font color="magenta">[**OBJETOS**]</font>

* ### **Todo objeto possui:**

    * ### Propriedades e Funcionalidades;

    * ### Estado e Comportamentos;

    * ### Atributos e Métodos

* ### **Exemplo:**

    * ### Uma caneta é um objeto: possui Propriedades (peso, cor da tinta etc.), Funcionalidades (escrever, rolar etc.), Estado (vazia, cheia, tampada, destampada et cetera).
  
***

## <font color="magenta">[**CLASSES**]</font>

* ### As classes na orientação a objetos funcionam como um molde para os objetos. Os objetos são criados a partir de uma classe e muitos deles podem ser feitos da mesma classe.

    * ### **Exemplo: Máquina de biscoitos**

        * ### Instâncias

        * ### Nesta analogia, a **_classe_** seria a máquina de biscoitos, que recebe ingredientes e prepara os biscoitos e os **_objetos_** são os biscoitos.

## <font color="orange">**Classes e objetos no JavaScript**</font>

* ### Syntactical sugar

* ### Prototype

* ### Os objetos em JavaScript são uma cadeia de protótipos, herdando as características e métodos de seus protótipos

    * ### **Exemplo:** Uma característica do tipo string de um objeto possui as características e métodos do protótipo string, como comprimento, entre outros.

* ## **Encapsulamento**

    * ### Dirigir carro vs conhecer o motor do carro

    * ### Significa colocar numa cápsula;

    * ### Agrupamento de funções e variáveis;

    * ### Esconder detalhes de implementação;

    * ### Camada de segurança para os atributos e métodos

* ## **Encapsulamento no código**

```javascript
// Código Estrutural

let altura = 50
let largura = 60

function calcularArea() {
    return altura * largura
}

let area = calcularArea()

// Código Orientado a Objetos

class Poligono {
    constructor(altura, largura) {
        this.altura = altura
        this.largura = largura
    }
    
    get area() {
        return this.#calcularArea()
    }

    #calcularArea() {
        return this.altura * this.largura
    }
}

//  criar o objeto

let poligono = new Poligono(50, 60)
console.log(poligono) // retorno: {"altura": 50, "largura": 60}
console.log(poligono.area) // retorno: 3000   (50 * 60)
```

## <center>**_<font color="orange">Programação Estruturada vs Orientação a Objetos</font>_**</center>

## **Programação Estruturada**

1. ### Processa a entrada e manipulação dos dados, até a saída

2. ### Uso de sequências, estruturas de repetição e condições

3. ### Uso de uma rotina maior, ou sub-rotinas

4. ### Não existem restrições às variáveis

***

## **Programação Orientada a Objetos**

1. ### Surge para trazer um cuidado ao uso estruturado

    * ### **Não elimina por completo o uso estruturado**

2. ### Conceitos como Objetos e Classes

3. ### Cuidados com variáveis e rotinas (Encapsulamento)

4. ### Melhor reutilização de código (Herança)

***

## **<font color="magenta">[Herança]</font>**

* ### Pais e filhos (hereditariedade)

* ### Objetos podem herdar ou estender características base

* ### Uma cópia de atributos e métodos de outra classe

* ### Palavra-chave <font color="cyan">**SUPER( )**</font>:

  * ### Refere-se à classe mãe (superclasse) e busca a característica ou método pré-definidos na mesma

    * ### Ou seja, ao digitar <font color="orange">super(name)</font> no constructor de uma subclasse, se estará herdando a característica nome da superclass

  * ### Muito similar à palavra-chave <font color="orange">**this**</font>

  * ### Exemplo: 

    ```javascript
    class Person{ // superclass
        constructor(name, age) {
            this.name = name
            this.age = age
        }

        hello() {
            console.log(`Hello, ${this.name}!`)
            console.log(`You are ${this.age} years old!`)
        }
    }

    class Student extends Person{ // subclass
        constructor(name, age, nota) {
            super(name, age)
            this.nota = nota
        }

        hello(){
            super.hello()
            console.log(`Sua nota é ${this.nota}`)
        }
    }

    class Teacher extends Person{ // subclass
        constructor(name, age, classSize) {
            super(name, age)
            this.classSize = classSize
        }

        hello(){
            super.hello()
            console.log(`Sua turma tem ${this.classSize} alunos.`)
        }
    }
    ```

## **<font color="orange">Herança no JavaScript</font>**

```javascript
class Veiculo {
    rodas: 4
    
    mover(direcao){}
    virar(direcao){}
}

class Moto extends Veiculo {
    constructor() {
        super()    // puxar atributos e métodos do pai
        this.rodas(2)
    }
} // A classe Moto é uma classe filha de Veiculo, onde Moto possui todas as características e funcionalidades de Veiculo, porém alterando a caracteristica "rodas" para 2.
```

***

## **<font color="magenta">[Polimorfismo]</font>**

* ### Significa "**muitas formas**"

* ### Quando um objeto estende de outro (**Herança**) talvez haja a necessidade de reescrever uma ou mais características (**Atributos e Métodos**) nesse novo objeto. 

## **<font color="orange">Polimorfismo no JavaScript</font>**

### **Construção da classe mãe**

```javascript
class Atleta {
    let peso 
    let categoria

    constructor(peso) {
        this.peso = peso
    }

    definirCategoria() {
        if (this.peso <= 50) {
            this.categoria = "Infantil"
        }
        else if(this.peso <= 65) {
            this.categoria = "Juvenil"
        }
        else {
            this.categoria = "Adulto"
        }
    }
}
```

### **Construção da classe filha**

```javascript
class Lutador extends Atleta {
    constructor(peso){
        super(peso)
    }

    definirCategoria() {
        if (this.peso <= 54) {
            this.categoria = "Pluma"
        }
        else if(this.peso <= 60) {
            this.categoria = "Leve"
        }
        else if(this.peso <= 75) {
            this.categoria = "Meio-Leve"
        } 
        else {
            this.cateooria = "Pesado"
        }
    }
}
```

***

## **<font color="magenta">[Abstração]</font>**

### Template ou identidade de uma classe que será construída no futuro

* ### Atributos e métodos podem ser criados na classe de Abstração (Superclasse) **MAS**

* ### A implementação dos métodos e atributos só poderá ser feita na classe que irá herdar essa Abstração

## **<font color="orange">Abstração no JavaScript</font>**

```javascript
class Parafuso { // Superclasse - Abstrata
    constructor() {
        if (this.constructor === Parafuso){
            throw new Error("Classe abstrata não pode ser instanciada")
        }
        get tipo() {
            throw new Error('Método "get tipo()" precisa ser implementado')
        }
    }
}

class Fenda extends Parafuso { // classe filha
    constructor() { super() }

    get tipo() { // retorna a característica "tipo" do objeto criado pela classe filha
        return "Fenda"
    }
}

class Phillips extends Parafuso { // classe filha
    constructor() { super() }

    get tipo() {
        return "Phillips"
    }
}

class Allen extends Parafuso {}

// Criar e usar
new Parafuso() // "Classe abstrata não pode ser instanciada"
let fenda = new Fenda()
let phillips = new Phillips()
let allen = new Allen()

console.log(fenda.tipo, phillips.tipo) // Fenda Phillips
console.log(allen.tipo) // 'Método "get tipo()" precisa ser implementado'
```

***

# <font color="orange"><center>**Programação Funcional**<center></font>

### É um paradigma de programação como a Orientação a Objetos: uma forma de raciocinar e resolver um problema.

## **<font color="magenta">[Funções]</font>**

* ### Pequenas tarefas dentro de uma função

* ### Abstrair um problema e resolvê-lo dentro da função

* ### Não modificar dados fora dela

* ### Pequenas e bem específicas no que fazem

## **<font color="cyan">Características principais</font> da função**

1. ### Um <font color="cyan">**dado**</font> (ou mais) <font color="cyan">**entra**</font> em uma função e um <font color="cyan">**novo dado sai**</font> dessa função

2. ### Não altera dados

3. ### Não guarda estado (<font color="red">**stateless**</font>)

## **Pontos positivos do paradigma funcional**

1. ### Fácil manutenção

2. ### Fácil uso de testes

    * ### Funções isoladas e consistentes 

3. ### Códigos mais confiáveis

***

# **<font color="orange">Princípios</font>**

## **Paradigmas**

* ### Programação Imperativa

* ### Programação Declarativa

## **Dados**

* ### Imutabilidade 

* ### Stateless

## **Funções**

* ### Independentes

* ### Puras

* ### Higher-order

* ### First-class

* ### Composição

***

## **<center><font color="cyan">PARADIGMAS</font>**

# <font color="orange">Programação Imperativa vs Declarativa</font>

## [**Programação <font color="cyan">Imperativa</font>**]

* ### O código é <font color="magenta">**pensado e gerado em sequência**</font>

* ### O código é pensado como um passo a passo, como uma <font color="magenta">**receita de bolo**</font>

* ### Uma coisa depende da outra

* ### O estado de um dado é <font color="magenta">**alterado constantemente**</font> causando mutação nas variáveis

* ### <font color="magenta">**Orientação a Objetos**</font> é um paradigma imperativo

***

## [**Programação <font color="cyan">Declarativa</font>**]

* ### O código é gerado para <font color="magenta">**fazer algo**</font>, não importa <font color="magenta">**como**</font>

* ### <font color="magenta">**O quê fazer**</font> e não **como fazer**

* ### Não há necessidade de um <font color="magenta">**passo a passo**</font> no código

* ### <font color="magenta">**Programação Funcional**</font> é um paradigma declarativo

## **Exemplo prático**:

* ### Função que eleva número ao quadrado

    ```javascript
    // Imperativa: "Faça da seguinte forma"
    let number = 2
    function square() {
        return number * number
    }

    number = square()

    // Declarativa: "O QUÊ fazer e não COMO fazer"
    const square = n => n * n
    ```
***

# **<center><font color="cyan">DADOS</font>**

## <font color="magenta">[**Imutabilidade**]</font>

* ### Uma variável não pode variar

* ### Se for preciso mudar uma variável, **cria-se uma nova**, ao invés de mudá-la.

* ### **Uso de constantes**

    ```javascript
    // exemplo em JS
    const cart = {
        quantity: 2,
        total: 200
    }

    // errado
    cart.quantity = 3

    // certo
    const newCart = {...cart, quantity: 3}

    // exemplo em ReactJS
    const [amount, setAmount] = useState(0)

    // errado
    amount = 2

    // certo
    setAmount(2)
    ```

## <font color="magenta">[**Stateless**]</font>

* ### Não guarda **<font color="cyan">estado</font>**

* ### A função só conhece dados entregues a ela

* ### A resposta não poderá variar


    ```javascript 
    let number = 2

    // stateful function
    function square() {
        return number * number
    }
    number = square()

    // stateless function
    const square = n => n * n
    ```

***

# **<center><font color="cyan">FUNÇÕES</font>**

## <font color="magenta">[**Independentes**]</font>

* ### Deverão ter ao menos 1 **argumento**

* ### Deverão **retornar** algo

* ### Representam um ciclo de vida curto para uma função

* ### Nada do que acontecer no seu interior afetará o exterior

    * ### dados imutáveis

    * ### não guardar estado

* ### Não far-se-á uso de loops (<font color="cyan">for, while</font>), mas se houver necessidade de tal, usaremos recursão (a função chama ela mesma)

```javascript
const random = (number, Math) => Math.floor(Math.random() * number)

// recursive
// Find the fatorial of a number
const factorial = x => {

    // if number is 0
    if(x === 0) {
        return 1
    }
    return x * factorial(x - 1)
}
```
***

## <font color="magenta">[**Funções Puras**]</font>

* ### Não deverá <font color="cyan">depender de nenhum dado externo</font> a não ser o que foi passado como argumento

* ### Não deverá sofrer <font color="cyan">nenhuma interferência</font> do exteriro a ela

* ### Se o argumento é o mesmo, <font color="cyan">o retorno não poderá ser diferente</font> quando a função for chamada novamente

* ### Não terá <font color="cyan">efeito colateral nenhum</font> no código

    * ### Não irá modificar nenhum dado

    * ### Não irá guardar nenhum estado

* ## **Função Impura**

    ```javascript

    // exemplo 1: está dependendo de dado externo que não foi passado como parâmetro
    function calculateCircumference(radius) {
        return Math.PI * (radius + radius)
    }

    // exemplo 2: está alterando um dado externo
    let person = {
        name: "Rafael Camarda",
        age: "Jovem"
    }

    function changeName(name) {
        person.name = name
    }
    ```

* ## **Função Pura**

```javascript
// exemplo 1:
const calculateCircumference(radius, pi) {
    return pi * (radius + radius)
}

// com arrow function:
const calculateCircumference(radius, pi) => pi * (radius + radius)

// exemplo 2:
const changePersonName = (person, name) => ({....person, name})
```

***

## <font color="magenta">[**First-class function**]</font>

* ### Podem estar em qualquer lugar da aplicação, inclusive como parâmetro de outras funções

* ### A função poderá ser <font color="cyan">entendida como uma variável</font>
  
    ```javascript
    const sayMyName = () => console.log("Mayk")
    const runFunction = fn => fn()

    runFunction(sayMyName) // Mayk
    runFunction(() => console.log("Discover")) // Discover

    console.log(runFunction(Math.random))
    ```

***

## <font color="magenta">[**Higher-order function**]</font>

* ### São funções que <font color="cyan">recebem funções</font> como argumentos

* ### Essas funções poderão <font color="cyan">retornar outras funções</font>

```javascript
// Exemplo com .map() JS
const numbers = [2, 4, 8, 16]

const square = n => n * n

const squaredNumber = numbers.map(square)//[4, 16, 64, 256]

// Exemplo de retorno de função
// (currying ou aplicação parcial de função)
const pause = wait => fn => setTimeout(fn, wait)

pause(600)( () => console.log('waiting 600ms') )

const wait200 = pause(200)
const wait1000 = pause(1000)

wait200(() => console.log("waiting 200ms") )
wait1000(() => console.log("waiting 1s") )
``` 

***

## <center><kbd><font color="lime" size="10">Composição de funções</font></kbd></center>

* ### Um <font color="cyan">**encadeamento**</font> de funções, ou seja, uma sendo executada atrás da outra

* ### Uma função que retorna um dado e vai para outra função, que retorna um dado e vai para outra função, que retorna...

    ```javascript
    const people = ["Rafa", "Diego", "Dani", "Rod"]
    const upperCasePeopleWhoseNameStartsWithD = people.filter(person => person.startsWith("D")).map(dperson => dperson.toUpperCase()) // ["DIEGO", "DANI"]
    ```

***

# **<center><font size=6 color="cyan">Assincronismo/JS Assíncrono</font>**

## **<font size=5 color="orange">[Síncrono X Assíncrono]</font>**

* ## **Sistema síncrono** (_synchronous_): uma tarefa é concluida logo após a outra.

    * ### A tarefa anterior precisa ser concluída, para então iniciar a próxima.

    * ### Por padrão, o JavaScript é um sistema síncrono.

    * ### Exemplo: Uma coleção de 3 imagens, em que uma carrega logo após a anterior ter sido carregada.

    ***

* ## **Sistema assíncrono** (_assynchronous_): uma tarefa é executada independentemente da outra.

    * ### O JavaScript poderá usar o assincronismo a seu favor

    * ### Exemplo: Uma coleção de 3 imagens, em que todas são carregadas independentemente do carregamento das outras.

***

## **<font size=6 color="orange">[Callback]</font>**

* ## Significa **_"Chamada de volta"_**

* ## Refere-se a uma função que é passada como argumento para outra função, para que seja _chamada de volta_ em algum momento.

***

## **<font size=6 color="orange">[setTimeout]</font>**

* ### É uma função JavaScript que recebe como argumentos uma outra função (callback function) e um delay em milissegundos. A função passada será chamada e executada após o fim do delay especificado

    ```javascript
    // setTimeout(function, delay)

    // Exemplo: Escrever algo depois de um segundo
    setTimeout(function() {
        console.log("Depois de 1s")
    }, 1000) 
    ```

***

## **<center><font size=6 color="orange">[Promise]</font>**

* ### A promessa de que algo irá acontecer, podendo dar certo ou errado, mas que irá acontecer.

* ### Trata-se de um objeto JavaScript com a promessa de que algo será realizado

* ### É usado para operações assíncronas

    * ### Carregar um arquivo

    * ### Leitura de dados de uma API

    ***

* ## Uma promessa poderá ser:

    * ### <font color="lightgrey">**Pending**</font>: Estado inicial, pendente, assim que o Objeto da promessa é iniciado

    * ### <font color="lime">**Fulfilled**</font>: A promessa foi concluída com sucesso

    * ### <font color="scarlet">**Rejected**</font>: A promessa foi rejeitada, houve um erro.

    * ### <font color="skyblue">**Settled**</font>: Seja com _sucesso_ ou _erro_, ela foi finalmente concluída.

    ***

## **<font size=6 color="orange">Promise no código</font>**

* ### Exemplo de sintaxe de uma promessa

    ```javascript
    let aceitar = true

    console.log("Pedindo uber")
    // Criando uma promise
    const promessa = new Promise((resolve, reject) => {

        if(aceitar){
            return resolve("O carro chegou")
        } 

        return reject("Pedido negado!")

    })

    console.log("Aguardando...")

    promessa
    .then(result => console.log(result))
    .catch(erro => console.log(erro))
    .finally(() => console.log("Finalizado."))

    // Saída:
    "
    Pedindo uber
    Aguardando...
    O carro chegou!
    Finalizado.
    "
    ```

    * ### Recapitulando o exemplo: a promessa consiste em pedir um uber, podendo retornar uma solução ("O carro chegou!") ou um erro ("Pedido negado!").

    * ### A callback function da promessa precisa receber os parâmetros **"resolve"** e **"reject"** para solucionar a promessa.

    * ### Os métodos **then()** e **catch()** recebem uma callback function como argumento e servem, respectivamente, para chamá-la no caso de **_fulfilled(resolve)_** ou **_rejected(reject)_**. Já o método **finally()** é responsável por chamar uma função independentemente do resultado.

    ***

## **<font size=6 color="orange">Promises com Fetch</font>**

* ### O comando fetch traz algo de uma url passada como parâmetro

* ### Exemplo:

    ```javascript
    fetch('https://api.github.com/users/kaikbarreto')
    ```

    * ### O fetch tem uma estrutura de promise.

        * ### Ou seja, é possível utilizar, sobretudo o método **then()**, assim como os outros.

* ### Também é possível encadear o método **then()**

    ```javascript
    fetch('https://api.github.com/users/kaikbarreto')
    .then( resposta => resposta.json())
    .then( dados => console.log(dados.login))
    ```

* ### Resultado: acha-se, dentro do JSON da resposta oriunda da URL especificada, os dados, do qual se imprime o login.

* ### Saída: "KaikBarreto" (login do user da URL)

***

## **<font size=6 color="orange">_Axios_</font>**

* ### Trata-se de um **HTTP Client** baseada em promessas, podendo ser usada tanto no browser quanto no Node.js

* ### O método get da biblioteca **Axios** se comporta semelhantemente ao fetch do browser, como uma promise

    ```javascript
    axios.get("https://api.github.com/users/kaikbarreto")
    // é semelhante a
    fetch("https://api.github.com/users/kaikbarreto")
    ````

***

## **<font size=5 color="orange">_Promises com Axios_</font>**

* ### Exemplo

    ```javascript
    import axios from 'axios'

    axios
    .get('https://api.github.com/users/kaikbarreto')
    .then( response => axios.get(response.data.repos_url))
    .then( repos => console.log(repos.data))
    .catch( error => console.log(error))
    ```

* ## **Promises em paralelo** com Promise all

    ```javascript
    Promise.all([
        axios.get("https://api.github.com/users/kaikbarreto"),
        axios.get("https://api.github.com/users/kaikbarreto/repos")
    ])
    .then( responses => {
        console.log(responses[0].login)
        console.log(responses[1].length)
    })
    ```

    * ### Saída: ["KaikBarreto", 4] (respectivamente o login do usuário e a quantidade de repositórios)

***

## **<center><font size=6 color="orange">Async/Await</font>**

* ### É uma maneira de escrever promessas, tornando mais fácil a visualização por meio de uma função assíncrona.

* ### Syntatic Sugar

* ### Async é uma keyword para declaração de funções assíncronas

* ### Await significa a espera de uma promise.

* ## Sintaxe: 

    * ### Usando **_Async/Await_**

        ```javascript
        const promessa = new Promise(function(resolve, reject) => {
            return resolve('ok')
        })

        
        ```

    * ### Da forma antiga, faria-se:

        ```javascript
        const promessa = new Promise(function(resolve, reject) => {
            return resolve('ok')
        })

        promessa
        .then(function(response) {
            console.log(response)
        })
        .catch(function(error) {
            console.log(error)
        })
        .finally(function() {
            console.log("Isto é impresso sempre.")
        })
        ```

    ***

## **<font size=5 color="orange">_Async/Await com Fetch_</font>**

* ### Permite a remodelação de um fetch atribuindo a variáveis o await de promises

    ```javascript
    async function start() {

        try{
            const url = "https://api.github.com/users/kaikbarreto"
            const user = await fetch(url).then(res => res.json())
            const userRepos = await fetch(user.repos_url).then(repo => repo.json())
            console.log(userRepos) // imprime a lista de repositórios 
        } catch(erro) {
            console.log(erro)
        } finally {
            console.log("Isto é impresso sempre.")
        }
    }

    start()
    ```

***

## **<font size=5 color="orange">_Async/Await com Axios_</font>**

```javascript
import axios from 'axios'

async function fetchRepos() {
  try {
    
    const url = "https://api.github.com/users/kaikbarreto"
    const user = await axios.get(url)
    const repos = await axios.get(user.data.repos_url)
    console.log(repos.data)


  } catch(error) {
    console.log(error)
  } finally {
    console.log("Isto é impresso sempre.")
  }
}

fetchRepos()
```