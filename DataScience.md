# **<center><font size="10" color="lightblue">Data Science (Ciência de Dados)</font></center>**

## Trata-se do conjunto de ferramentas, metodologias e estratégias para **transformar dados em informação**.

> #### <font color=tomato>**Para este estudo, far-se-á uso da linguagem Python para a sintaxe.**</font>

***

* ## <font color=orange>[Abrindo arquivos com python]</font>

    * ### Para ler, assim como escrever arquivos em python utiliza-se uma função chamada <font color=cyan>**open( )**</font>, que recebe pelo menos dois argumentos: 
     
        1. O **caminho do arquivo a ser aberto**

        1. O **modo de abertura**, ou seja, se é para ler, escrever ou adicionar algo a um arquivo.

        * ### Os argumentos para **ler**, **escrever**, ou **adicionar** a um documento são, respectivamente, **"r"**; **"w"**; **"a"**.

    * ### **Exemplo:**

        ```python
        with open("arquivos/arquivo.txt", "a") as arquivo:
            ...
        ```

    ***

* ## <font color=orange>[Lendo arquivos com python]</font>

    * ### É como **extraem-se** os dados do arquivo.

    * ### **Exemplo:**

        ```python	
        with open("text.txt", "r") as arquivo:
            conteudo = arquivo.read()
            print(conteudo)

        ```

    * ### Comumente são usados **laços de repetição (loops)** para ler múltiplas linhas de um arquivo

        * #### **Ex.:**

            ```python
            with open("text.txt", "r") as arquivo:
                for linha in arquivo:
                    print(linha)

                # OU 

                linhas = arquivo.readlines()
                for linha in linhas:
                    print(linha)
            ```

    ***

* ## <font color=orange>[Escrevendo arquivos com python]</font>

    * ### Abrir arquivos no modo "writing" ou "w" sugere que o conteúdo do arquivo será **SUBSTITUÍDO** pelo que for escrito em seu lugar.

    * ### **Ex.:**

        ```python
        with open("text.txt", "w") as file:
            file.write("Anotações de Kaik Barreto")
            # escrever uma string no arquivo
        ```

    * ### Também é possível utilizar **laços de repetição (loops)** para escrever em um arquivo

        * #### **Ex.:**

            ```python
            numeros = ["1", "2", "3", "4"]
            with open("text.txt", "w") as file:
                for numero in numeros:
                    file.write(numero)
            ```

    * ### Utilizando o modo de abertura **"appending"**, abreviado com **"a""** é possível escrever num arquivo sem sobrepor o que já estava escrito.

        * ### **Ex.:**

            ```python
            with open("text.txt", "a") as file:
                proximoNumero = "5"
                file.write(numero)
            ```

            > Seguindo o exemplo anterior, o próximo valor do arquivo seria 5, e para adicionar este número sem sobrepor os já existentes, é preciso abrir no modo "appending".

***

* ## Combinando alguns destes conceitos, é possível, por exemplo, copiar um arquivo para outro.

    ```python
    with open("copiado.txt", "r") as copiado:
        
        with open("cópia.txt", "w") as cópia:
            for linha in copiado:
                cópia.write(linha)
    ```

***

## Utilizando algumas bibliotecas como a **Pandas**, podem-se interpretar dados de uma forma mais eficaz

***

## <center><font color=Orange size=8>**Pandas**</font>

## <center> [Documentação Pandas](https://pandas.pydata.org/docs/)

* ## Pandas é uma biblioteca python muito popular para análise de dados que já possui em si diversas funções para facilitar a leitura consistente de arquivos de dados.

    ***

* ## A biblioteca também funciona à partir de DF's (dataframes), estruturas compostas por **linhas e colunas**, como uma planilha.

* ### **Ex.:**

    ```python
    import pandas

    caminhoDoArquivo = "./arquivo.csv"
    arquivoCSV = pandas.read_csv(caminhoDoArquivo)
    # Neste caso, "arquivoCSV" se torna um dataframe

    print(arquivoCSV.head())
    # Dataframes pandas possuem o método head(), que é usado para examinar as primeiras 5 linhas do arquivo/dataframe.
    ```

* ### Suponhamos um dicionário com informações sobre músicas:

    ```python
    músicas = {
        "Nome da música": ["Fly me to the Moon", "Thriller", "Despacito", "Gangnam Style"], 
        "Cantor": ["Frank Sinatra", "Michael Jackson", "Luis Fonsi", "Psy"], 
        "Ano de lançamento": [1964, 1982, 2017, 2012]
    }

* ### Com pandas, pode-se criar um dataframe à partir de um dicionário:

    ```python
    músicasDF = pandas.DataFrame(músicas)
    ```

    |   Nome da música   |      Cantor     | Ano de lançamento |
    |:------------------:|:---------------:|:-----------------:|
    | Fly me to the Moon |  Frank Sinatra  |        1964       |
    |      Thriller      | Michael Jackson |        1982       |
    |      Despacito     |    Luis Fonsi   |        2017       |
    |    Gangnam Style   |       Psy       |        2012       |

    ***

* ### Utilizando pandas, é possível, por exemplo, buscar pelo valor de uma coluna específica, utilizando colchetes duplos.

    * #### **Ex.:**


        * #### Ex1
  
            ```python
            datasDeLançamento = músicasDF[["Ano de lançamento"]]
            ```

            > ### Resultado: um novo dataframe composto pela coluna especificada do dataframe original

            
            |   Ano de lançamento   |
            |:------------------:|
            |       1964         |
            |       1982         |
            |       2017         |
            |       2012         |

        * #### Ex2

            ```python
            músicasEDatas = músicasDF[["Nome da música","Ano de lançamento"]]
            ```

            > ### Resultado: um novo dataframe composto pelas colunas especificadas do dataframe original.

            |   Nome da música   | Ano de lançamento |
            |:------------------:|:-----------------:|
            | Fly me to the Moon |        1964       |
            |      Thriller      |        1982       |
            |      Despacito     |        2017       |
            |    Gangnam Style   |        2012       |

    ***

* ### Aplicando filtros:

    ```python
    maisRecentesQueAno2000 = músicasDF[músicasDF["Ano de lançamento"] > 2000]
    ```

    > ### Resultado: Todas as músicas cujo ano de lançamento seja maior do que 2000.

    | Nome da música |   Cantor   | Ano de lançamento |
    |:--------------:|:----------:|:-----------------:|
    |    Despacito   | Luis Fonsi |        2017       |
    |  Gangnam Style |     Psy    |        2012       |


***

## <center><font color=yellow size=6>[Trabalhando com e salvando dados com Pandas]</font>

* ### Com pandas, é possível exportar um dataframe criado para, por exemplo, um arquivo csv.

    * #### **Ex.:**

        ```python
        dataFrameASerExportado.to_csv("dataFrameExportado.csv")
        ```

* ### Existem outros formatos para salvar dataframes pandas.

***

## <center><font color=Orange size=8>**NumPy**</font>

## <center> [Documentação NumPy](https://numpy.org/doc/)

* ## Ao analisar uma grande quantidade de dados, iterações sobre uma lista começam a se tornar cada vez mais lentas e consomem muita memória.

* ## Para combater este problema, existem bibliotecas, como a **NumPy**, que possuem **classes** construídas para abrigar e aplicar métodos a coleções de dados de forma mais eficiente.

* ### **Import:**

    ```python
    import numpy as np
    ```

    ***

## <center><font color=Orange size=7>**NumPy Unidimensional (1D)**</font>

## A biblioteca NumPy possui uma classe específica para abrigar listas e torná-las mais eficientes: a classe array. 

## Geralmente, em grandes coleções de dados, a estrutura utilizada possui somente elementos do mesmo **tipo** (int, float, etc.).

## **Exemplo:**

### <center>Abrigar uma lista na classe **array** da lib **NumPy**

*
    ```python
    import numpy as np

    array = np.array([0,1,2,3,4])
    ```

    ***

### Assim como numa lista python convencional, é possível acessar os elementos de um array numpy via **índices**:

*
    ```python
    array[0] #  0

    array[1] # 1

    array[-1] # 4

    array[0:4] # [0 1 2 3]
    ```

    ***

## Arrays numpy possuem diversos atributos pré-moldados, como, por exemplo:

*
    ```python
    array.size # número de elementos: 5

    array.ndim # número de dimensões: 1

    array.shape # formato do array, em suas diferentes dimensões: (5,)
    ```

    ***

## Assim como numa lista convencional, é possível sobrescrever valores específicos de um array:

* 
    ```python
    outroArray = np.array([20, 1, 2, 3, 4])
    # [20, 1, 2, 3, 4]

    outroArray[0] = 100
    # [100, 1, 2, 3, 4]

    outroArray[4] = 0
    # [100, 1, 2, 3, 0]
    ```

    ***

## Como listas e tuplas, estes arrays podem ser fatiados:

*
    ```python
    array1 = np.array([0,1,2,3])
    # [0, 1, 2, 3]

    array2 = array1[1:4]
    # [1, 2, 3]

    array2[2:4] = 20, 50
    # [1, 20, 50]
    ```

    ***

## **NumPy** facilita muitas operações básicas realizadas em **Ciência de Dados**.

## <center><font color=Orange size=6>**Operações Básicas**</font>

## <font color=pink size=5>**Soma**</font>

* ## <center><font color=red>Pior</font>: Soma de listas comuns com laço de repetição:

    ```python
    x = [1, 0]
    y = [0, 1]
    z = []

    for n, m in zip(x, y):
        z.append(n + m)
    ```

    ***

* ## <center><font color=lime>Melhor</font>: Soma de arrays em uma linha com NumPy:

    ```python
    x = np.array([1, 2])
    # [1, 2]

    y = np.array([4, 3])
    # [4, 3]

    z = x + y
    # [5, 5]
    ```

    > ## <font color=cyan>**z[0] == (x[0] + y[0]) == 5**
    
    > ## **z[1] == (x[1] + y[1]) == 5**</font>

    ### A classe array da lib numpy permite que a operação soma entre dois arrays retorne um novo array com a soma dos valores de mesmo índice em cada array somado.

    ***

***

## <font color=pink size=5>**Subtração**</font>

* ## <center><font color=red>Pior</font>: Subtração de listas comuns com laço de repetição:

    ```python
    x = [1, 0]
    y = [0, 1]
    z = []

    for n, m in zip(x, y):
        z.append(n - m)
    ```

    ***

* ## <center><font color=lime>Melhor</font>: Subtração de arrays em uma linha com NumPy:

    ```python
    x = np.array([4, 5])
    # [4, 5]

    y = np.array([2, 3])
    # [2, 13]

    z = x - y
    # [2, 2]
    ```

    > ## <font color=cyan>**z[0] == (x[0] - y[0]) == 2**
    
    > ## **z[1] == (x[1] - y[1]) == 2**</font>

    ### A classe array da lib numpy permite que a operação subtração entre dois arrays retorne um novo array com a diferença dos valores de mesmo índice em cada array somado.

***

## <font color=pink size=5>**Multiplicação**</font>

* ## <center> Multiplicação por um fator

    ```python
    x = np.array([10, 20])
    fator = 2

    z = x * fator
    # [20, 40]
    ```

    > ## <font color=cyan>**z[0] == x[0] * fator == 20**

    > ## **z[1] == x[1] * fator == 40**</font>


    ***

* ## <center> Multiplicação de arrays

    ```python
    x = np.array([10, 20])
    y = np.array([5, 3])

    z = x * y
    # [50, 60]
    ```

    > ## <font color=cyan>**z[0] == x[0] * y[0] == 10 * 5 == 50**

    > ## **z[1] == x[1] * y[1] == 20 * 3 == 60**</font>

***

## <center><font color=Orange size=6>**Broadcasting**</font>

* ## Consiste em, de forma rápida e concisa, somar constantemente a um Array numpy

* ## **Exemplo:**

    ### <center> **De um Array1 de int's, retirar um outro Array2 com os sucessores dos elementos do primeiro**

    *
        ```python
        Array1 = np.array([1, 2, 3])
        # [1, 2, 3]

        Array2 = Array1 + 1
        # [2, 3, 4]
        ```

        > ### **`1, 2, 3, 1`** -> **`1+1, 2+1, 3+1`** -> **`2, 3, 4`**

***
 
## <center><font color=Orange size=6>**Universal Functions**</font>

* ## Tratam-se de funções que são operadas em Arrays NumPy, muito úteis para a visualização de dados em larga escala.

* ## Existem diversos métodos embutidos em classes NumPy, como o **Array**, desenhados para facilitar a obtenção de informações sobre os dados.

    ***

## <font color=pink size=5>**Média**</font>

* ### Para calcular a média de um array, utiliza-se o método **`mean()`**:

    ```python
    array = np.array([10, 20, 30])

    média_array = array.mean()
    # (10 + 20 + 30) / 3 = 20
    ```

    ### <center> **`o método mean() retorna o valor médio de todos os valores do array.`**

    ***

## <font color=pink size=5>**Valor máximo**</font>

* ### Para calcular o maior valor (valor máximo) de um array, utiliza-se o método **`max()`**:

    ```python
    array = np.array([50, 70, 300])

    média_array = array.max()
    # 300 porque 300 > 70 > 50
    ```

    ### <center> **`o método max() retorna o valor máximo de todos os valores do array.`**

    ***

## <center><font color=pink size=5>**Entre outros... (vide docs)**</font>

***
## <center><font color=Orange size=7>**NumPy Bidimensional (2D)**</font>

* ## Podemos criar Arrays NumPy com mais de uma dimensão, como, por exemplo, um **Array Bidimensional (2D)**.

    * ### **Exemplo:**

        ```python
        import numpy as np

        array = np.array([
            [11, 12, 13], 
            [21, 22, 23], 
            [31, 32, 33]
        ])

        array.ndim # número de dimensões do array: 2

        array.shape # formato do Array/matriz: (3, 3) ~~ 3 listas com 3 elementos cada ~~

        array.size # número de elementos individuais: 9 (3x3)
        ```

        * ### Neste exemplo, caso deseje-se acessar um elemento específico do **Array/Matriz**, é necessário especificar o índice dos dois eixos:

            ```python
            array[0][0] # 11
            ```

        ### **`É comum pensar em matrizes/arrays bidimensionais como um modelo retangular, como uma tabela, onde há um eixo X (horizontal) e um eixo Y (vertical).`**

        ***

        ### <center> **Assim, o elemento `array[0][0]` poderia ser interpretado como o valor da <font color=lime>primeira coluna da primeira linha</font>**

        ```python
        array = np.array([
            [11, 12, 13], 
            [21, 22, 23], 
            [31, 32, 33]
        ])
        ```

        |        | coluna1 | coluna2 | coluna3 |
        |:------:|:-------:|:-------:|:-------:|
        | linha1 |    11   |    12   |    13   |
        | linha2 |    21   |    22   |    23   |
        | linha3 |    31   |    32   |    33   |

        ### **`Sendo assim, pode-se dizer que o primeiro colchete representa a linha e o segundo a coluna.`**

        *
            ```python
            array[linha, coluna] # == elemento
            ```

    ***

## <font color=pink size=5>**Fatiando arrays 2D/matrizes**</font>

*
    ```python
    A = np.array([
            [11, 12, 13], 
            [21, 22, 23], 
            [31, 32, 33]
        ])

    # 1. diferentes linhas, mesma coluna

    A[0:2, 2] # [13, 23]
    # terceiro elemento das linhas 1 e 2

    # 2. diferentes colunas, mesma linha.

    A[1, 0:3] # [21, 22, 23]
    ```

***

## <font color=pink size=5>**Operações com matrizes**</font>

* ## As operações funcionam praticamente da mesma forma, porém os efeitos são aplicados nos elementos de mesmo índice em cada matriz, em todas as suas dimensões.

* ## **Exemplos:**

    ## <center><font color=orange size=6>**Soma**</font>


    ```python
    X = np.array([
        [1, 3],
        [5, 7]
    ])
    # [[1, 3, [5, 7]]

    Y = np.array([
        [2, 4],
        [6, 8]
    ])
    # [[2, 4], [6, 8]]

    Z = X + Y
    # [[3, 7], [11, 15]]
    ```

    ***

    ### **`A soma das duas matrizes (X e Y) retorna uma nova matriz (Z) cujos elementos correspondem à soma dos elementos de mesma posição em X e Y. `**

    ***

    ## <center> X: 

    <center><font color="cyan">

    | 1 | 3 |
    |:-:|:-:|
    | 5 | 7 |

    </center></font>

    ***

    ## <center> Y: 

    <center><font color="cyan">

    | 2 | 4 |
    |:-:|:-:|
    | 6 | 8 |

    </center></font>
    
    ***

    ## <center> Z: 

    <center><font color="cyan">

    | 3 | 7 |
    |:-:|:-:|
    | 11 | 15 |

    </center></font>
    
    ***

## <font color=pink>**Subtração, multiplicação etc. funcionarão da mesma forma, aplicando a regra para cada elemento de mesma posição dentro da matriz.**</font>

***

