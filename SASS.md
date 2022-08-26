# **<center><font size=10 color="lightblue">SASS</font></center>**

## <center> [Documentação SASS](https://sass-lang.com/documentation/)

## O que é o SASS?

* ## **Syntactically Awesome StyleSheets**

* ## Um pré-processador CSS que irá dar poder aos estilos

* ## Compila estrutura de código _**<kbd><font color="cyan">.scss</font></kbd>**_ ou </font>_**<kbd><font color="cyan">.sass</font></kbd>**_ para _**<kbd><font color="cyan">.css</font></kbd>**_

***

## Para que serve o SASS?

* ## Simplificar e organizar CSS

* ## Manutenção

* ## Rapidez e reuso de código

* ## Maior compatibilidade com múltiplos navegadores

* ## Programar: Variáveis, Funções, Repetições, IF/Else...

***

## Utilização:

* ## Para começar a utilizar o SASS, basta criar um arquivo com a extensão ".scss". Este arquivo gerará um outro arquivo, desta vez de extensão ".css", o qual deverá ser importado pela página HTML.

***

# <center>**_<font color="orange">Importação de arquivos usando SASS</font>_**

* ## Qual é a utilidade de importar arquivos de StyleSheets?

    * ### Componentização das folhas de estilo.

    * ### Redução de comprimento de arquivos únicos

    * ### Uma vez que cada arquivo .scss corresponde a uma parte do estilo geral, a manutenção se torna mais fácil e tangível.

* ## Para um arquivo </font>_**<kbd><font color="cyan">.scss</font></kbd>**_ ser importado, seu nome deve seguir o seguinte modelo:

    > ### _exemplo.scss

* ## Agora, para importar este arquivo, usa-se a seguinte sintaxe no arquivo </font>_**<kbd><font color="cyan">.scss</font></kbd>**_ principal:

    ```scss
    @use 'exemplo'
    ```

    * ### Note-se que o nome do arquivo importado é utilizado sem a underline ( _ ) e também sem sua extensão (.scss).

***

# <center>**_<font color="orange">Encadeamento/Indentação</font>_**

* ## Em arquivos SASS, é possível encadear seletores, gerando escopos.

* ## Exemplo: Um container que possui texto branco, porém cujos parágrafos possuam texto azul.

    * ### Em CSS
  
        ```css
        .container {
            color: white;
        }

        .container p {
            color: blue;
        }
        ```

    * ### Com o SASS (.scss)

        ```scss
        .container {
            color: white;

            p {
                color: blue;
            }
        }
        ```

    ### Note-se que o arquivo .scss gerará o exato mesmo resultado do exemplo .css, porém podendo ser escrito de forma mais lúdica.

    ***

***

# <center>**_<font color="orange">Variáveis</font>_**

* ## O SASS declara variáveis da mesma forma que o CSS tradicional, iniciado por um sinal de "$".

    ```scss
    $text-color: #ccc;

    body {
        color: $text-color;
    }
    ```

* ## Também podem ser criadas variáveis compostas, como no javascript, utilizando parênteses. Os itens podem (lista/array) ou não (objeto) ter chaves para seus valores.

    ```scss
    //exemplo sem chaves para os valores
    $colors: blue, red, yellow

    //exemplo com chaves para os valores
    $colors: (color1: blue, color2: red, color3: yellow);
    ```

* ## A indentação de arquivos </font>_**<kbd><font color="cyan">.scss</font></kbd>**_ gera escopos, ou seja, variáveis criadas dentro de um escopo não podem ser usadas num escopo acima do dele.

    * ## Exemplo correto:

        ```scss
        .container {
            $bgColor: #1d1e20;
            background: $bgColor;
        }
        ```
    
    * ## Exemplo incorreto:

        ```scss
        .container {
            $bgColor: #1d1e20;
        }

        body {
            background: $bgColor;
        }
        ```

*** 

# <center>**_<font color="orange">Mixins: @mixin/@include</font>_**

* ## Trata-se de uma estrutura que permite guardar um trecho de código que poderá ser reutilizado, como uma função.

* ## Sua estrutura é semelhante à de uma função em javascript [ **_função( ) {  }_** ]

* ## Utiliza-se a keyword **_@mixin_** para definir o mixin e a keyword **_@include_** para utilizá-lo.

* ## Exemplo: 

    ```scss 
    @mixin box-shadow() {
        $color: rgba(0, 0, 0, 0.6);
        box-shadow: 2px 2px 4px -2px $color
    }

    .container {
        @include box-shadow();
        background-color: white;
        width: 100px;
        height: 200px;
    }
    ```

* ## Os mixins também podem receber parâmetros:

    ```scss
    @mixin box-shadow($color) {

        box-shadow: 2px 2px 4px -2px $color
    }

    .container {
        @include box-shadow( rgba(0, 0, 0, 0.6) );
        background-color: white;
        width: 100px;
        height: 200px;
    }
    ```

***

# <center>**_<font color="orange">Condicionais: @IF/@ELSE</font>_**

* ## Permite criar trechos de código que somente serão aproveitados caso satisfaçam uma determinada condição.

* ## Sua sintaxe é muito semelhante à do JavaScript, porém as condições não necessitam estar entre parênteses.

* ## Usam-se, para a construção de condicionais e retorno de valores booleanos (true/false), as keywords **_@IF</font>_**, **_@ELSE</font>_** e **_@ELSE IF</font>_**

    > ## Exemplos de uso:

    *   ```scss
        @mixin make-bold($bool) {
            @if $bool == true {
                font-weight: bold;
            }
        }
        ```

    *   ```scss
        @mixin text-effect($val) {
            @if $val == danger {
                color: red;
            } 
            @else if $val == alert {
                color: yellow;
            } 
            @else {
                color: green;
            }
        }
        ```

***

# <center>**_<font color="orange">Repetições: @FOR @EACH</font>_**

* ## Permite criar repetições para, por exemplo, aplicações de estilos em diferentes classes numeradas.

* ## Utilizam-se as keywords **@for** e **@each**

* ## **Exemplos**: 

    * ## 1. @for: Aplicar um estilo para diversas classes sequenciadas

        ```scss
        @for $i from 1 to 6 {
            .text-#{$i} {
                font-size: 15px * $i
            }
        }
        ```

      * ### Note-se: para inserir num seletor o nome de uma variável, não basta colocar apenas o $ seguido do nome da variável, mas sim colocar isso dentro de um "#{}"

          ```scss
          .caixa-$numero_da_caixa        // errado

          .caixa-#{$numero_da_caixa}    // certo
          ```

      * ### Note-se também: a estrutura "**$i from 1 to 6**" é semelhante ao "**while (i < 6)**" do javascript: o código será executado de 1 a 5, ou seja, excluindo o 6.

    ***

    * ## 2. @for each

        * ### Utilizado para gerar uma repetição direcionada a uma coleção de itens.

        ```scss
        $colors: blue, red, yellow;

        @each $color in $colors {
            .#{$color}-text {
                color: $color;
            }
        }
        ```

        > ### Leia-se: **_Para cada $cor em $colors, faça isso..._**

***

# <center>**_<font color="orange">Funções</font>_**

* ## Permite adicionar a uma variável uma funcionalidade 

* ## Sintaxe semelhante à do JavaScript

    > ## Obs.: Funções podem returnar um valor com o uso da keyword **_@return_**

* ## **Exemplo:**

    ```scss
    @function set-inverse-color($color) {
        @if $color == "white" {
            @return black;
        } @else if $color == "black" {
            @return white;
        }
    }
    ```

***

# <center>**_<font color="orange">Herança</font>_**

* ## Trata-se da capacidade de um seletor herdar as características já atribuidas a outro seletor e, então, receber outras.

* ## **Exemplo:**

    ```scss
    .flex {
        display: flex;
        align-items: center;
        justify-content: center;
    }

    body {
        @extend .flex;
        flex-direction: column;
        height: 100%;
    }
    ```

***

# <center>**_<font color="orange">Referrencing</font>_**

* ## Trata-se da possibilidade de referência a um pseudoelemento ou pseudoclasse, como o hover de um parágrafo.

    ```scss
    // Ao invés disso:
    p {
        color: red 
    }
    p:hover { 
        color:blue 
    }

    // Escreve-se isso:

    p {
        color: red;

        &:hover {
            color: blue;
        }
    }
    ```

***