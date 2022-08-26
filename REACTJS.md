# **<center><font size=10 color="lightblue">REACT</font></center>**

## <center> [Documentação React.js](https://pt-br.reactjs.org/docs/getting-started.html)

* ## Consiste numa biblioteca de JavaScript para a criação de interfaces de usuário (UI's).

* ## Utiliza bastante o paradigma de **_programação funcional_** 

***

* ## **<font color=orange size=5>[Criando projeto]</font>**

    * ### Para a criação do diretório do projeto em ReactJS, pode ser usado no terminal o comando <kbd>npx create-react-app</kbd> ou então usando a ferramenta Vite, mais eficiente:

        > ### <font color=cyan>npm create vite@latest nome-do-projeto --template react</font>

    * ### Após isso, é necessário instalar as dependências do projeto com um:

        > ### <font color=cyan>npm install</font>

    ***

* ## **<font color=orange size=5>[Executando projeto]</font>**

    * ### Para executar o projeto criado, utiliza-se o comando:

        > ### <font color=cyan>npm run dev</font>

    ***

* ## **<font color=orange size=5>[JSX]</font>**

    * ### Trata-se da sintaxe utilizada por aplicações ReactJS para criar as interfaces de forma declarativa

    * ### É sempre uma **função**, cujo retorno é um componente **HTML** a ser renderizado

    * ### Exemplo (navbar.jsx):

        ```jsx
        function Navbar() {
            return (
                <nav>
                    <p>Exemplo</p>
                </nav>
            )
        }
        export default Navbar
        ```

    * ### Existem duas formas de escrever comentários num arquivo **JSX**:

        * ### Na parte da lógica do componente:

            ```jsx
            import React from 'react'

            // Algum comentário
            
            const component = () => {
              return (
                <div>Exemplo</div>
              )
            }
            
            export default component
            ```

        * ### No próprio JSX (retorno do componente):

            ```jsx
            import React from 'react'
            
            const componente = () => {
              return (
                { /* Algum comentário */}
                <div>Exemplo</div>
              )
            }
            
            export default componente
            ```

    * ### Também é possível renderizar componentes de forma declarativa, ou seja, como uma tag HTML, uma vez que os tenha importado:

        ```jsx
        import Navbar from './Navbar'

        function Header() {
            return (
                <Navbar />
                <p>lorem ipsum</p>
            )
        }
        export default Header
        ```

    * ### Arquivos JSX não precisam ser importados com sua extensão ".jsx"

        ```jsx
        import Navbar from './navbar'
        ```

    * ### Para definir uma classe no retorn HTML do JSX, o react utiliza-se de "className" no lugar do convencional "class":

        ```jsx
        function Home() {
            return (
                <div className="nomeDaClasse">
                    Lorem Ipsum 
                </div>
            )
        }
        ```

    ***

* ## **<font color=orange size=5>[Template Expressions]</font>**

    * ### trata-se do recurso que permite executar **javascript dentro do JSX** e também interpolar variáveis.

    * ### A sintaxe é: { algumCódigoEmJS }

        * #### Tudo que está entre chaves é processado em javascript e retorna um resultado

    * ### **Exemplo:**

    ```jsx
    import React from 'react'
    
    const name = "Kaik"

    const componente = () => {
      return (
        <div>Olá, {name}! Tudo bem?</div>
      )
    }
    
    export default componente
    ```

    > #### Neste caso, o conteúdo da div seria: **Olá, Kaik! Tudo bem?**

    ***

* ## **<font color=orange size=5>[Eventos]</font>**

    * ### São essenciais para o desenvolvimento front-end, uma vez que compoem a interação da aplicação com o usuário.

    * ### No React, os eventos já estão 'prontos', podemos utilizar, por exemplo, o evento **OnClick** para ativar uma função ao clicar em um elemento.

    ## **<font color=orange>[Funções nos eventos]</font>**

    * ### Esta função será realizada ao acionar o evento como o OnClick e deve ser criada no próprio componente. 

    * ### Por padrão seu nome é do tipo: <font color="cyan">**handleAlgumaCoisa**</font>

    * ### Estas funções sempre recebem como parâmetro o evento acionado, geralmente abreviado por "e"

        ```jsx
        const handleClick = function(e){
            console.log(e)
        }

        return (
            <button 
            OnClick={handleClick}>
                Clique aqui
            </button>
        )
        ```
            
        * > #### ao clicar neste botão, a função handleClick será ativada, logando no console o evento em si.

        ***

    * ### Também é possível passar uma arrow function diretamente no elemento do JSX:

        ```jsx
        return (
            <div>
                <button onClick=>{(e) = console.log(e)} >
                    Clique aqui também
                </button>
            </div>
        )
        ```

        * > #### ao clicar neste botão, a função handleClick também será ativada, logando no console o evento em si.

    ***

* ## **<font color=orange size=5>[Funções de renderização]</font>**

    * ### Podemos criar funções que retornam JSX

    * ### Isto serve para criar situações que **dependam de outras condições**.

    * ### Ou seja, o JSX a ser renderizado pode mudar a depender de uma variável.

    * ## **Exemplo:**

        * ### Uma função que retorna um parágrafo dizendo "Ímpar" se o número passado como parâmetro for ímpar e "Par" caso for par.

            #### <center>Definindo a função 

            ```jsx
            const parOuImpar = function(numero) {
                if(numero % 2 == 0) {
                    return <p>Par</p>
                } 
                else if (numero % 2 == 1) {
                    return <p>Ímpar</p>
                }
            }
            ```

            #### <center>Utilizando a função

            ```jsx
            // ... definição do componente

            return (
                <p>O número 5 é... {parOuImpar(5)}!</p>
            )
            ```

            > #### <center> a frase do parágrafo seria: <font color=cyan>**O número 5 é... Ímpar!**</font> 

    ***

* ## **<font color=orange size=5>[Estrutura de pastas e arquivos]</font>**

    * ### Os arquivos possuem uma estrutura flexível, porém com uma base comum:

    <center>

    ![Imagem estrutura de pastas React](./img/react-folder-structure.png)

    </center>

    * ### O diretório **src** também pode receber outros diretórios para imagens, componentes, estilos etc.:

    <center>

    ![Imagem estrutura de pastas React 2](img/react-folder-structure2.png)

    </center>

    ***

* ## **<font color=orange size=5>[Fragment]</font>**

    * ### Trata-se de uma pequena regra sobre como deve ser o retorno dos componentes <kbd><font color=cyan>.jsx</font></kbd>

    * ### Expressões JSX pode ter apenas um único elemento filho. (Uma tag vazia ou uma div encapsulando todo o resto  servem)

    * ### <font color=lime>Certo:</font>

        ```jsx
        function Home() {

            return (
                <>
                    <h1>Lista de presença</h1>
                    <input type="text" />
                    <button>Adicionar</button>
                </>
            )
        }

        export default Home
        ```

    ***

* ## **<font color=orange size=5>[Importando CSS]</font>**

    * ### <font color=ligblue>CSS</font>

        ### global.css

        ```css
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        ```
    
    * ### <font color=tomato>JSX</font>

        ### main.jsx

        ```jsx
        import React from 'react'
        import ReactDOM from 'react-dom/client'

        import './styles/global.css'

        import Home from './pages/Home'

        ReactDOM.createRoot(document.getElementById('root')).render(
            <React.StrictMode>
                <Home />
            </React.StrictMode>
        )
        ```


    ***

* ## **<font color=orange size=5>[Separando CSS]</font>**

    * ### Refatorando um pouco a estrutura de arquivos dentro das pastas do projeto em React, é possível separar os estilos de cada componente.

    <center>

    ![Pastas React Componentes](./img/react-folder-components.png)

    </center>

    * ### O arquivo que antes era Home.jsx passa a ser de um diretório chamado Home e se chamar index.jsx, assim, não é necessário alterar importações. Uma vez que na pasta Home o componente **index.jsx** importa os estilos de **styles.css**, o componente Home será exportado já com estes estilos.

    ***

* ## **<font color=orange size=5>[Componentes]</font>**

    * ### O uso da componentização está diretamente associado à boa manutenção do código, uma vez que, com os elementos separados, é fácil a visualização e alteração de comportamento de cada elemento de uma aplicação.

    * ### Ao utilizarem-se partes fragmentadas de uma aplicação, torna-se possível a reutilização de componentes, como, por exemplo, um rodapé que se repete em múltiplas (quiçá todas) páginas da aplicação.

    * ### **Exemplo:** 

        ### Componente

        ```jsx
        function Card() {
            return (
                <div className="card">
                    <strong>Kaik Barreto</strong>
                    <small>10:15:24</small>
                </div>
            )
        }

        export default Card
        ```

        ### Reutilização do component **_Card_** (3x)

        ```jsx
        import Card from  '../../components/Card'

        function Home() {
            return (
                <div>
                    <Card />
                    <Card />
                    <Card />
                </div>
            )
        }
        export default Home
        ```

    ***

* ## **<font color=orange size=5>[Props (Propriedades/Parâmetros)]</font>**

    * ### Componentes JSX (que são funções) podem receber parâmetros, dinamizando a declaração de um componente na aplicação.

    * ### Exemplo: Imprimir na tela um cartão com nome e data, os quais serão recebidos como parâmetros/propriedades.

        ***

        ### <font color=cyan>Criação do componente dinâmico</font>

        ```jsx
        import './styles.css'

        function Card(props) {
            return (
                <div className="card">
                    <strong>{props.name}</strong>
                    <small>{props.time}</small>
                </div>
            )
        }

        export default Card
        ```

        * ### A keyword **props** permite que as propriedades sejam ilimitadas, cujos nomes venham após **<font color=lime>"props."</font>**
            
        ***

        ### <font color=cyan>Utilização dinâmica do componente, atribuindo valores na declaração do componente</font>

        ```jsx
        import Card from  '../../components/Card'

        function Home() {

        return (
            <div>
                <Card name="Kaik Barreto" time="10:55:25" />
                <Card name="João Feliciano" time="11:00:10" />
            </div>
        )
        }

        export default Home
        ```

        ***

    * ### **Também é possível passar propriedades/parâmetros específicos no componente**

        ### <font color=cyan>Criação do componente dinâmico</font>

        ```jsx
        function Card({ name, time }) {
            return (
                <div>
                    <strong>{name}</strong>
                    <small>{time}</small>
                </div>
            )
        }
        ```
        ***

        ### <font color=cyan>Utilização dinâmica do componente, atribuindo valores na declaração do componente</font>

        ```jsx
        import Card from  '../../components/Card'
        function Home() {
        return (
            <div>
                <Card name="Fulano" time="08:50:38" />
            </div>
        )
        }
        export default Home

        ```

        ***

* ## **<font color=orange size=5>[A prop hildren]</font>**

    * ### é um recurso utilizado para quando um componente **precisa ter JSX dentro dele, porém este JSX vem do componente pai**.

    * ### Então o componente age como um **container**, abraçando estes elementos.

    * ### E children é considerada uma **prop do componente**.

    * ### **Exemplo:**

        #### <center> Um Container que possa receber html dentro de si ao ser utilizado e imprima este html interior atraves da **prop children**.


        * #### Criação do componente

            ```jsx
            const Container = ({children}) => {

                return <>
                    <h2>Título</h2>
                    {children}
                </>
            }
            ```

        * #### Utilização do componente Container no componente pai

            ```jsx
            const App = () => {

                return (
                    <Container>
                        <p>conteúdo interno</p>
                    </Container>
                )
            }
            ```

        * #### <center> <font color=cyan>Será renderizado o seguinte:</font>

            ```jsx
            <Container>
                <h2>Título</h2>
                <p>conteúdo interno</p>
            </Container>
            ```

        #### <center> <font color=cyan>Observe que o "{children}" do componente Container foi substituído pelo que estava dentro da tag Container.</font>

    ***

* ## **<font color=orange size=5>[Função como prop]</font>**

    * ### As **funções podem ser passadas como argumento/parâmetro** para um componente filho **via props**.

    * ### Basta criar uma função no componente pai e **enviar como prop** para o componente

    * ### **No componente filho ela pode ser ativada por um evento**.

    * ### **Exemplo:**

        ### <center> No componente pai:

        ```jsx
        const Pai = () => {

            function mostrarMensagem() {
                console.log("Evento do componente pai!")
            }

            return <div>
                <Filho funcaoHerdada={mostrarMensagem}/>
            </div>
        }
        ```

        ### <center> No componente filho:

        ```jsx
        const Filho = ({funcaoHerdada}) => {

            return <div>
                <button onClick={funcaoHerdada}>
                    Clique aqui para disparar a função herdada.
                </button>
            </div>
        }
        ```

        #### <center> A função **mostarMensagem( )** foi passada do componente **[Pai]** para o componente **[Filho]**. Assim, o componente **[Filho]** consegue acessar e executar essa função através da Prop **[funcaoHerdada]**

    ***

* ## **<font color=orange size=5>[Estado/State]</font>**

    * ### Trata-se de onde se guardam os dados, o estado do componente

    * ### A diferença do **Estado/State** para uma variável comum é que o estado, ao ser alterado, renderiza novamente o componente

    * ### O estado possui 2 elementos em forma de vetor/array: o primeiro é o conteúdo/valor do estado e o segundo é uma função que atualiza o valor do estado pelo parâmetro recebido:

        ```jsx
        const [nome, setNome] = useState()

        setNome("Kaik") // nome se torna Kaik
        setNome("João") // nome se torna João
        ```
    
    * ### O método **useState()** pode receber como argumento um valor inicial para o estado

        * #### Exemplo, um nome que é atualizado baseado no estado, porém que começa sendo Kaik

            ```jsx
            const [idade, setIdade] = useState(29) 
            // idade começa como 29
            setIdade(30) // idade se torna 30
            ```

    * ### Por exemplo, pode-se guardar o valor de um input e atualizá-lo a cada vez que for alterado

        ```jsx
        import React, { useState } from 'react'
        import Card from '../../components/Card'

        function Home() {
            const [personName, setPersonName] = useState()

            function handleNameChange(name) {
                setPersonName(name)
            }

            return (
                <div className="container">
                    <h1>Nome: {personName}</h1>
                    <input
                        type="text"
                        placeholder="Digite o nome..."
                        onChange={e => handleNameChange(e.target.value)} />
                </div>
            )
        }
        export default Home
        ```

        * ### * Note-se que a importação <font color=lime>[import React, { useState } from 'react']</font> é indispensável para a utilização do estado

        * ### Resultado: O "{personName} do H1 será atualizado para o valor do input a cada vez que ele for alterado.


    ***

* ## **<font color=orange size=5>[Imutabilidade]</font>**

    * ### É o princípio que os estados do ReactJS respeitam

    * ### Faz parte do paradigma de **programação funcional**

    * ### **_O conteúdo não deve ser alterado, mas sim substituído_**

        * #### Esse conceito torna a aplicação mais performática

        * #### Por isso não se atualiza o valor do estado diretamente, mas sim utiliza-se uma função para substituí-lo

        * ### **Exemplo:**

            ### <font color=lime>**Certo**</font>

            ```jsx
            const [cityName, setCityName] = useState()

            setCityName("Nova York") // substituição do valor
            // cityName torna-se Nova York
            ```

            ### <font color=red>**Errado**</font>

            ```jsx
            const [cityName, setCityName] = useState()

            cityName = "Nova York" // atualização do valor
            ```
        
    ***

* ## **<font color=orange size=5>[useState]</font>**

    * ### O **useState** é o mais utilizado e serve para **gerenciar o estado de algum dado**, sendo esta a única forma de alterar uma varíavel e re-renderizá-la no React.

    * ### Para guardar o dado, utilizamos o retorno da função useState( ), que é uma lista com a variável e uma função para alterar o estado da variável.

    * ### O hook useState recebe como parâmetro o estado inicial da variável a ser criada.

    * ### **Exemplo:**

        #### <center> variável **nome**, cujo valor inicial é **"Kaik"**

        ```jsx
        // importação do useState
        import { useState } from 'react'


        // criação da variável 
        const [nome, setNome] = useState("Kaik")

        // alteração do estado usando a função retornada pelo useState
        setNome("Matheus")
        // nome passa a ser "Matheus"

        console.log(nome) // Matheus
        ```

        #### <center> `A cada vez que é alterado o valor da variável com a função setVariável(), o componente é renderizado novamente, sem dar reload na página.`

        ***

    ## **<font color=orange>previous state</font>**

    * ### **Previous state** é um recurso que nos permite pegar o dado em seu valor original dentro de um **set** de dado.

    * ### Isso é muito utilizado para **modificar listas**, transformando o valor antigo em um novo valor.

    * ### O **primeiro argumento** de um **set** sempre será o **previous state**, ou seja, o estado prévio (anterior) do dado.

    * ### **Exemplos:**

        #### <center><font color=yellow>**1. mudar o estado do número para o sucessor do mesmo**</font>

        ```jsx
        // iniciando uma variável numero com o estado 0.
        const [numero, setNumero] = useState(0)

        setNumero((prevNumero) => {
            return prevNumero + 1
        })        
        ```

        #### <center>O set da variável número recebe como parâmetro uma outra função que usa o valor original do número para retornar seu sucessor e alterar o estado para este novo número.

        ***

        #### <center><font color=yellow>**2. Alterar o estado de uma lista ao passar seu valor original por um filtro**</font>

        ```jsx
        // iniciando uma variável nomes
        const [nomes, setNomes] = useState([
            "Kaik",
            "Matheus",
            "Rafaella",
            "Maicon",
            "Maria"
        ])

        setNomes((prevNomes) => {
            return prevNomes.filter(nome => nome.startsWith("M"))
        })      
        ```

        #### <center>O set da variável nomes recebe como parâmetro uma outra função que usa o array original de nomes para retornar um novo array apenas com nomes que comecem com "M".

    ***

* ## **<font color=orange size=5>[State Lift / Elevação de estado]</font>**

    * ### Elevação de estado ou state lift **é quando um valor é elevado do componente filho para o componente pai**.

    * ### Geralmente, tem-se **um componente que usa o state e outro que o altera**.

    * ### Então, precisa-se **passar a alteração para o componente pai, e este passa para o componente que usa o state**.

    * ### **Exemplo:**

        ### <center> No componente pai:

        ```jsx
        const Pai = () => {

            const [message, setMessage] = useState("")

            function handleMessage(msg) {
                setMessage(msg)
            }

            return <div>
                <Message msg={message} />
                <ChangeMessage handleMessage={handleMessage} />
            </div>
        }
        ```

        * #### <center> `Neste exemplo, o componente [Pai] administra o estado da variável message.`

        * #### <center> O componente [Message] <font color=cyan>**recebe a variável message para consumí-la**</font>

        * #### <center> O componente [ChangeMessage] <font color=red>**recebe a variável message para alterá-la**</font> e elevar este novo estado para o componente pai, renderizando novamente todos os componentes que consomem esta variável.

    ***

* ## **<font color=orange size=5>[useEffect]</font>**

    * ### É um Hook utilizado para realizar uma função passada como parâmetro toda vez que um estado do array de dependências (também passado como parâmetro) for alterado.

    * ### O **useEffect** é executado automaticamente **_assim que a interface é renderizada_**

    * ### **Sintaxe**:

        * ### recebe como parâmetros uma função **_(corpo)_** e um array **_(dependências)_**

            ```jsx
            useEffect(() => {
                // corpo do useEffect
            }, []) // array de dependências
            ```

        * ### O array de dependências recebe os estados de que o useEffect depende.

            * #### O array vazio significa que o useEffect será realizado uma única vez

            * #### Ao inserir um estado nas dependências, toda vez que este estado for atualizado o useEffect será executado novamente

            * #### **Exemplo:**

                ```jsx
                useEffect(() => {
                    console.log("Alguém entrou na lista")
                }, [lista])
                // toda vez que um estado da lista é alterado, o useEffect é disparado, imprimindo no console que "Alguém entrou na lista"
                ```

        ***

    * ### **Exemplos de uso:** 

        ### <center> Imprimir no console uma mensagem assim que a interface for renderizada

        ```jsx
        useEffect(() => {
            console.log("useEffect foi chamado!")
        }, [])
        ```

        ***

        ### <center> Imprimir no console uma mensagem toda vez que o estado da variável **Nome** for alterado

        ```jsx
        useEffect(() => {
            console.log("O estado da variável Nome foi alterado!")
        }, [Nome])
        ```

    ***

* ## **<font color=orange size=5>[Renderização de Listas]</font>**

    * ### É possível, com uma sintaxe específica, renderizar dados de um array ou object literal (e muitas vezes arrays de objetos) numa estrutura de repetição dentro do template em React.

    * ### Por padrão, utiliza-se o método **map** para iterar sobre o array.

    * ### Além dos dados, é possível **inserir JSX** em cada iteração.

    * ### **Ex.:**

        #### <center> Adicionar à ul (lista) um li (list item) **para cada fruta no array frutas**.

        ```jsx
        import { useState } from 'react'

        const componente = () => {
            const [frutas] = useState(["Maçã", "Banana", "Melancia", "Morango"])

            return <div>
                <ul>
                    {frutas.map((fruta) => (
                        <li>{item}</li>
                    )}
                </ul>
            </div>
        }
        ```

    ## <font color="orange">**Renderização de componentes em loop**</font>

    * ### Utilizando dos conceitos de **renderização de listas**, **reaproveitamento de componentes** e **props**, podemos utilizar uma estrutura de repetição como o **map** para exibir múltiplas instâncias de um componente, dinamicamente.

    * ### **Exemplo:**

        ```jsx
        const carros = [
            {id: 1, marca: "Ferrari", modelo: "F8"},
            {id: 2, marca: "Lamborghini", modelo: "Gallardo"},
            {id: 3, marca: "Rolls Royce", modelo: "Phantom"},
        ]

        return (
            <ul>
                {carros.map((carro) => (
                    <li key={carro.id}>
                        <Carro 
                            marca={carro.marca} 
                             modelo={carro.modelo} 
                        />
                    </li>
                ))}
            </ul>
        )
        ```

        #### <center> Neste caso, para cada carro no array de carros, é renderizado um **li (list item)**, cuja **key** é o **ID** do carro, contendo um componente **Carro** que recebe as props **marca** e **modelo**. 

    ***

* ## **<font color=orange size=5>[Renderização Condicional]</font>**

    * ### Trata-se da **impressão de uma parte do template baseada em uma condição**, ou seja, utilizando as estruturas condicionais do Javascript **if** e **else**.

    * ### Um uso comum deste tipo de renderização é, por exemplo, um determinado componente ser mostrado caso o usuário esteja logado e não ser mostrado caso não esteja.

    * ### **Exemplo:**

        #### <center><font color=yellow>**exibir um nome no template caso ele comece com a letra K (condicional simples)**</font>

        ```jsx
        const nome = "Kaik"

        const [começaComK] = useState(nome.startsWith("K")) 

        return (
            <div>
                {começaComK && <p>{nome}</p>}
            </div>
        )
        ```

        #### <center>Como a variável nome é uma string que começa com K, a variável "começaComK" inicia-se com o estado true. Sendo true, o paragrafo contendo o nome é renderizado. 

        ***

    ## <font color=orange>**Condicional Composta**</font>

    * ### Para expressar uma condicional com if e else no JSX, utilizam-se os operadores ternários, da seguinte maneira:

        <center>

        <font color=cyan size=4>condição <font color=yellow>?</font> <font color=lime>blocoSeVerdadeiro</font> <font color=yellow>:</font> <font color=red>blocoSeFalso</font></font>

    * ### **Exemplo:**

        ```jsx

        ```

        #### <center>

    ***

* ## **<font color=orange size=5>[Key Prop]</font>**

    * ### Ao utilizar uma estrutura de repetição **_[.map(), .forEach() etc.]_** para gerar componentes dinâmicos, há a necessidade de acrescentar uma propriedade chamada "key", que seja única, ou seja, que não se repita.

    * ### A necessidade da atribuição desta propriedade é para que o react use esta chave para identificar os elementos da lista corretamente

    * ### **Exemplo:**

        #### <center> um Card **para cada fruta no array de frutas**, onde a key prop é um ID de cada fruta e a name prop é o nome de cada fruta.

        ```jsx
        {
            frutas.map(fruta => (
                    <Card
                        key={fruta.ID}
                        name={fruta.nome}
                    />
                )
            )
        }
        ```

        * ### Neste exemplo, a chave é o próprio horário, que, neste caso, não se repetirá entre as gerações de componentes

    ***

## <center>**<font color=orange size=7>[Hooks]</font>**

* ### São recursos do React que têm diversas funções, como, por exemplo, guardar e alterar o estado de algum dado na aplicação etc.

* ### Eles permitem que usem-se o state e outros recursos do React sem escrever uma classe

* ### Geralmente seus nomes começam com <font color=lime>**use**</font> e então o nome do **Hook**. 

    * #### Ex.: **[<font color=lime>useState, useEffect</font>]**

* ### É possível criar nossos próprios hooks, que ganham o nome de **Custom Hook**

* ### Hooks precisam ser importados e são usados em praticamente toda aplicação React atual.

***

* ## **<font color=orange size=5>[Consumindo API]</font>**

    ```jsx
    import React, { useState, useEffect } from 'react'

    function Home() {
        const [user, setUser] = useState({ name: '', avatar: '' })

        useEffect(() => {
            fetch("https://api.github.com/users/kaikbarreto")
                .then(response => response.json())
                .then(data => {
                    setUser({
                        name: data.name,
                        avatar: data.avatar_url
                    })
                })
        }, [])

        return (
            <header>
                <h1>Lista de presença</h1>
                <div>
                    <strong>{user.name}</strong>
                    <img src={user.avatar} alt="Foto de perfil" />
                </div>
            </header>
        )

    export default Home
    ```

    ***

* ## **<font color=orange size=5>[useEffect Async]</font>**

    ```jsx
    useEffect(() => {
        async function getUser(userUrl) {
            const url = userUrl
            const response = await fetch(url)
            const data = await response.json()

            setUser({
                name: data.name,
                avatar: data.avatar_url
            })
        }

        getUser("https://api.github.com/users/kaikbarreto")
    }, [])
    ```

***










***

# **<center><font color=cyan size=8>[React Router]</font>**

* ## O <font color=tomato>**React Router**</font> é um pacote para mudanças de URLs da aplicação

* ## Assim, é possível acessar outras páginas **sem o page reload**, trocando apenas uma parte do layout, ou seja, o que muda de página para página

* ## É necessário instalar esse pacote no projeto e também realizar algumas mudanças em como o App é estruturado

* ## Para instalar: 
    ```bash
    npm install react-router-dom
    ```

* ## Para o bom funcionamento das rotas, é necessário importar os elementos do pacote instalado:

    ```jsx
    import { BrowserRouter as Router, Routes, Route, Link } from 'react-router-dom'
    ```

    ***

## **<font size=6 color=orange>Estabelecendo rotas</font>**

* ## **Elementos:**

    * ### BrowserRouter (importado como Router)

        * #### Engloba toda a estrutura do roteador (sistema de rotas)

    * ### Routes

        * #### Engloba as rotas da aplicação

    * ### Route

        * #### Especifica a rota em si, com seu caminho e o componente que representa

        * #### path

            * #### representa a URL de acesso ao componente

        * #### element

            * #### representa o elemento que será renderizado ao acessar o caminho da rota

            * #### Recebe a declaração do componente entre chaves

            	```jsx
                <Route path="/" element={<Home />} />
                ```

    * ### Link

        * #### Possui sintaxe semelhante a uma tag `<a>` do HTML, porém, no lugar do `href`, usamos o **to**

            ```jsx
            <Link to="/">Home</Link>
            <Link to="/Sobre">Sobre</Link>
            <Link to="/Contato">Contato</Link>
            ```

* ## **Aplicação:**

    ```jsx
    <Router>

        <Routes>

            <Route path="/" element={<Home />} />

            <Route path="/Sobre" element={<Sobre />} />

            <Route path="/Contato" element={<Contato />} />

        </Routes>

    </Router>
    ```

    * ### Também é possível aplicar Route Params nas rotas:

        ```jsx
        <Route path="/pessoa/:id" element={<Pessoa />} />
        ```

        * ### Assim, há uma rota para cada pessoa, baseada no ID passado na rota.

        * ### De forma que, ao acessar `"/pessoa/10"`, encontra-se a pessoa de ID 10.

    ***

## **<font size=6 color=orange>[Imagens]</font>**

* ## Imagens públicas no React

    * ### As imagens públicas do projeto podem ficar na pasta public

    * ### De lá, elas podem ser chamadas pelas tags img diretamente pelo <font color=cyan>**/nomeDaImagem.jpg**</font>, pois **a pasta public fica linkada com o src** das imagens.

        * ### **Exemplo:**

            #### <center> importação via public

            ```jsx
            return (
                <div>
                    <img src="/nomeDaImagem.jpg">
                </div>
            )
            ```

            > #### Uma vez que a imagem está na pasta public, não é necessário especificar o caminho da imagem.

    ***

* ## Imagens em src

    * ### Também é muito comum, em projetos React, deixar imagens, por padrão, em uma pasta chamada <font color=cyan>**assets**</font> dentro de **src** do projeto.

    * ### Utilizando esta abordagem, é necessário especificar o caminho da imagem, dinâmicamente, baseado em onde a tag img está sendo utilizada, igual a um componente.

    * ### **Exemplo:**

        #### <center> importação via path em src
    
        ```jsx
        import Imagem from '.assets/imagem.jpg'

        return (
            <div>
                <img src={Imagem} />
            </div>
        )
        ```

    ***

## **<font size=6 color=orange>[]</font>**
