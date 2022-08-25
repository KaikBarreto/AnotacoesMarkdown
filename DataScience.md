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

## <center><font color=yellow size=6>[Carregando dados com Pandas]</font>

* ## Pandas é uma biblioteca python muito popular para análise de dados que já possui em si diversas funções para facilitar a leitura consistente de arquivos de dados.

    ***

* ## A biblioteca também funciona à partir de DF's (dataframes), estruturas compostas por **linhas e colunas**.

* ### **Ex.:**

    ```python
    import pandas

    caminhoDoArquivo = "./arquivo.csv"
    arquivoCSV = pandas.read_csv(caminhoDoArquivo)
    # Neste caso, "arquivoCSV" se torna um dataframe

    arquivoCSV.head()
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
            músicasEDatas = músicasDF[["Ano de lançamento","Ano de lançamento"]]
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