# **<center><font size="10" color="lightblue">TYPESCRIPT</font></center>**

## <center> [Documentação Typescript](https://www.typescriptlang.org/docs/)

## TypeScript é um superconjunto de JavaScript, ou seja, um conjunto de ferramentas e formas mais eficientes de escrever código JavaScript, permitindo que seja estabelecida uma tipagem estática.

## O código TypeScript compila um novo, desta vez em JavaScript

## O TypeScript torna possível que, por exemplo, um parâmetro de uma função aceite apenas números

* ### **Exemplo**:

    ```javascript
    function sum(a, b) {
        return a + b
    }

    console.log(sum("1", "2")) // 12
    ```

    > ### Neste caso, o retorno desejado seria 3, porém, como os parâmetros recebidos eram do tipo texto, houve uma concatenação

* ### Para solucionar este problema, pode-se atribuir aos parâmetros a e b uma tipagem estática, ou seja, definir o tipo que eles poderão ter:

    ```typescript
    function sum(a: number, b: number) {
        return a + b
    }

    console.log(sum("1", "2")) // desta vez, essa linha resultará num erro, uma vez que os parâmetros devem ser do tipo number

    console.log(sum(3, 4)) // 7

    console.log(sum(7, 19)) // 26
    ```

***

## **<font size=6 color="orange">[Tipagem Explícita]</font>**

* ### Trata-se de quando a tipagem é definida de forma clara, explícita.

* ### **Exemplo**:

    ```typescript
    function helloNewUser(name: string, age: number) {
        console.log(`Olá, ${name}! Sua idade é ${age}.`)
    }
    ```

    > ### Neste caso, os parâmetros "name" e "age" estão sendo tipados de maneira explícita

***

## **<font size=6 color="orange">[ANY]</font>**

* ### Por padrão, uma variável em TypeScript é do tipo **_any_**, ou seja, pode receber valores de qualquer tipo.

* ### **Exemplos**:

    ```typescript
    let info: any

    info = [1, 2, 3]
    info = "Kaik"
    info = true
    info = 10.50
    ```

    ```typescript
    function sum(a: any, b: any) {
        console.log(a + b)
    }

    sum(1, 3) // 4
    sum("1", "3") // 13
    ```

***

## **<font size=6 color="orange">[Inferência de Tipos]</font>**

* ### Trata-se do reconhecimento automático por parte do TypeScript do tipo da variável baseado no conteúdo atribuído a ela.

* ### **Exemplo**:

    ```typescript
    // Tipagem Explicita
    let user: string = "Rodrigo"

    // Inferência de Tipos
    let user = "Rodrigo"
    ```

    > ### Ao declarar user como uma String, o TypeScript já **infere** que esta seja do tipo String.

***

## **<font size=6 color="orange">[Tipos Primitivos]</font>**

* ### **Boolean:**

    ```typescript
    let loading: boolean
    loading = false
    ```

    ***

* ### **String:**

    ```typescript
    let email: string
    email = "kaik@email.com"
    ```

    ***

* ### **Number:**

    ```typescript
    let price: number = 10.50
    ```

***

## **<font size=6 color="orange">[Matrizes]</font>**


* ### Também é possível estabelecer tipagem para vetores/arrays.

* ### **Exemplos:**

    ```typescript
    // declaração de um array de números
    let numbers: number[]
    numbers = [1, 2, 3, 4, 5, 6]

    // declaração específica de um array de strings
    let users: Array<string>
    users = ["Rodrigo", "João"]
    ```

***

## **<font size=6 color="orange">[Funções]</font>**


* ### Funções possuem tipos:

    * ### **Void:**

        #### São funções sem retorno

        ```typescript
        function showMessages(message: string): void {
            console.log(message)
        }
        ```

        > #### Note-se também que, pela inferência de tipos, ao declarar-se uma função sem retorno, esta passa a ser do tipo Void.

        ***
    
    * ### **Declaração do tipo do RETORNO**

        ```typescript
        function sum(a: number, b: number): number {
            return a + b
        }
        ```

        * #### Leia-se: uma função de parâmetros a e b, ambos do tipo number, cujo retorno também é do tipo number.

***

## **<font size=6 color="orange">[Union]</font>**


* ### Trata-se de um operador do TypeScript para definir mais de um tipo para uma variável.

* ### É representado pelo símbolo de **pipe " | "**, trazendo o valor lógico **OU**

    ```typescript
    function printUserId(id: number | string) {
        console.log(`O ID do usuário é ${id}.`)
    }
    printUserId(101) // O ID do usuário é 101.
    
    printUserId("284") // O ID do usuário é 284.
    ```

    > #### Neste caso, o parâmetro **"id"** pode receber valores dos tipos number **OU** string.

***

## **<font size=6 color="orange">[Generics]</font>**


* ### Trata-se de uma outra forma de deixar a tipagem flexível, assim como o **Union**, possibilitando um padrão.

* ### A diferença está no fato de que com o Generic, a tipagem que vai prevalecer é a da chamada.

* ### Existem algumas chaves convencionais utilizadas para definir esta forma tipagem:

    * ### **S** => State

    * ### **T** => Type

    * ### **K** => Key

    * ### **V** => Value

    * ### **E** => Element

* ### **Exemplo**:

    ```typescript
    function useState<T extends string | number>() {
        let state: T

        function get() {
            return state
        }

        function set(newValue: T) {
            state = newValue
        }

        return { get, set }
    }

    let newState = useState<string>()
    newState.get()
    newState.set("Kaik")
    newState.set(123)
    ```

    > ### Note-se que na definição do tipo flexível **"T"** foi usada a estrutura "extends", que define uma tipagem caso nenhuma seja definida.

***

## **<font size=6 color="orange">[Type]</font>**

* ### É possível reaproveitar tipos em TypeScript, utilizando a keyword **_type_**:

    * #### Ao invés de fazer isso:

        ```typescript
        let userId: string | number | undefined
        let adminId: string | number | undefined
        ```

    * #### Faz-se isso:

        ```typescript
        type IdType = string | number | undefined

        let userId: IdType
        let adminId: IdType
        ```

***

## **<font size=6 color="orange">[Type Assertions]</font>**

* ### É um recurso para utilizar quando o TypeScript não sabe determinar o tipo de um elemento e deseja-se **afirmar** o tipo do mesmo.

* ### **Exemplo de uso**:

    * #### Receber os dados de uma API e **AFIRMAR** os tipos de dados presentes na resposta:

        ```typescript
        type UserResponse = {
            ui: number;
            name: string;
            avatar: string;
        }

        let userResponse = {} as UserResponse
        ```

        > #### Note-se que foi usada a keyword **_<font size=5 color=cyan>as</font>_** no objeto para atribuir a ele os tipos de UserResponse

***

## **<font size=6 color="orange">[Tipagem para Objetos]</font>**

* ### **Exemplo prático**:

    #### A função recebe como parâmetro um objeto, cujo tipo é definido por "Point"

    ```typescript
    type Point = {
        x: number,
        y: number,
    }

    function printCoord(points: Point) {
        console.log(`O eixo X vale ${points.x}.`)
        console.log(`O eixo Y vale ${points.y}.`)
    }

    printCoord({x: 101, y: 50})
    // O eixo X vale 101.
    // O eixo Y vale 50.
    ```

    ***

    ## **<font size=5 color="orange">[Opcional]</font>**

    * ### Alguns tipos podem receber elementos facultativos, ou seja, não-obrigatórios. Para isso, adiciona-se um sinal de interrogação após o nome do elemento opcional deste objeto:

        ```typescript
        type User = {
            name: string
            email: string
            age: number,
            isAdmin?: boolean
        }

        let newUser: User = {
            name: "Jocivaldo",
            email: "Jocivaldo@email.com",
            age: 18
        }
        ```

        > #### Como vê-se, o objeto newUser não aponta o "erro" de não possuir o elemento isAdmin, uma vez que este é opcional.

***

## **<font size=6 color="orange">[Intersecção de Tipos]</font>**

* ### Trata-se de quando é necessário utilizar mais de uma tipagem para um único elemento.

* ### Para isso, cria-se uma nova tipagem, que reúne as características das duas tipagens que se deseja unir.

* ### **Exemplo**:

    ```typescript
    type User = {
        id: number,
        name: string,
    }

    type Char = {
        nickname: string,
        level: number,
    }

    type PlayerInfo = User & Char

    let kaik: PlayerInfo = {
        id: 123,
        name: "Kaik",
        nickname: "Parallax",
        level: 37
    }
    ``` 

    > #### No exemplo, deseja-se unir as tipagens **_User_** e **_Char_**. Para isso, cria-se uma nova tipagem chamada **_PlayerInfo_**, utilizada pelo objeto **_kaik_**.

***

# <center><font size=7 color=cyan>Explorando mais funcionalidades</font> 
