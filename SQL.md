# **<center><font size="10"  color="lightblue">SQL e Banco de dados</font></center>**

## <center> [Documentação SQL](https://docs.microsoft.com/pt-br/sql/?view=sql-server-ver16)

## **<center>O que é um banco de dados?</center>**
    Um banco de dados nada mais é do que um Repositório sistêmico de informações
    Guarda informações de forma organizada

### Existem muitos serviços de bancos de dados, como:

* SQLite
* MySQL
* PostgreSQL
* OracleDB
* mongoDB

#### **Os dados são organizados em tabelas.**

* ###  Essas tabelas possuem campos, que receberão informações (valores).

#### Exemplo de tabela:

---
1.  Nome | Nome de usuário | Descrição | id
    :---: | :---: | :------: | :--:
    Josefina | @jose_demais | As dancinhas mais originais | 1
    Mariano | @marianoano | oh no no no no no no no | 2

#### _**Neste caso, "nome", "nome de usuário" e "descrição" são campos, enquanto os outros items são informações atreladas a estes campos.**_
---
2.  Nome de usuário | Post | video | id_usuario
    :--: | :--: | :--: | :--:
    @jose_demais | #bancodedadosetudo #organizacao | video.mp4 | 1
    @marianoano | Olha esse video kkk #bancodedados | video.mp4 | 2
    @jose_demais | esse é um post maneiro | foto.jpg | 1




***

### <center>**É possível relacionar informações entre tabelas**</center>


* ### <font color="cyan">As informações do campo "id" [1ª tabela] se relacionam com o campo "id_usuário" [2ª tabela].</font>

## Exemplo real:

## **<center>Escola Guerreiros do Amanhã</center>**

## <center>**Alunos**</center>

| id_aluno | Nome | Cpf | Responsável |
:-: | :-: | :-: | :-: |
2 | Jakeliny Gracielly | 12345678945 | Josefina Gracielly |
0202 | Mariano Garcia | 45678945645 | Márcio Garcia
1 | João Castro | 45645345687 | José Castro

***

## <center>**Professores**</center>

| id_professor | nome | cpf | materia | 
:-: | :-: | :-: | :-: |
1 | Mayk Brito | 45678945612 | JavaScript
2 | Josefina Gracielly | 45612345678 | NodeJS
3 | Olavo Silva | 45678945612 | Banco de Dados

## <center>**Aulas**</center>

|id_professor | id_aluno |
| :-: | :-: |
1 | 2
1 | 0202
1 | 1
2 | 0202
2 | 1
3 | 2
3 | 1

***

## **<center>Tipos de Campos</center>**

## 1. **Text**

* ### Podem ter caracteres especiais (!@#$%&*, etc.) e números (0-10)

    * ### Ex.: <font color="cyan">O padeiro confeccionou 59 pães!</font>

## 2. **Number**

* ### **Apenas números**

    * ### Ex.: <font color="cyan">21970117921</font>

## 3. **Datatime**

* ### **Data e Hora**

    * ### Ex.: <font color="cyan">01-04-2020-09-30-22 (01 de abril de 2020 às 09:30:22)</font>

## 4. **Primary Key**

* ### **Identificador**

    * ### Não pode se repetir

    * ### Ex.: <font color="cyan">id_user: [1]</font>

## 5. **Foreign Key**

* ### A **Foreign Key** nada mais é do que uma **Primary Key** referenciada, estabelecendo uma conexão entre tabelas do banco de dados.

* ### Pode se repetir.

* ### Também chamada de <font color="#F9DC5C">Chave Estrangeira</font>

    * ### Ex.: <font color="cyan">id_user: [1]</font> referenciada em outra tabela.

## 6. **Unique**

* ### Comando que faz com que um campo não possa se repetir

    * ### Ex.: <font color="cyan">nome de usuário: TEXT UNIQUE (é um texto e não pode ser repetido)</font>

### **<center>Campos podem ser de mais de um tipo</center>**

    Ex.: Um Primary Key [identificador] pode ser, também, um number ou text.

***

### <center><font color="orange">Regras para escrever nome de tabelas e de campos</font></center>

    1 - Deve começar por uma letra do alfabeto

    2 - Os caracteres seguintes não são permitidos:
                () + - / * " ; = & | # > < ^ ' {} %

    3 - Não pode conter espaços

    4 - Não pode conter acentuação

***

# <center>**Comandos e operadores SQL**</center>

## 1. **_Comando Select_**

* ###2 Responsável por buscar e mostrar informações de uma entidade (tabela)

* ## Sintaxe:

    ## 1. Todos os campos: 

    ```SQL 
        SELECT * FROM aluno 
    ```

    * ### Retorno/Saída: Toda a entidade aluno, com seus campos e informações
        
    ***

    ## 2. Campos específicos: 

    ```SQL 
        SELECT campo1, campo2, campo3 FROM aluno 
    ```

    * ### Retorno/Saída: Os campos 1, 2 e 3 e suas respectivas informações
    
    ***

    ## 3. SELECT com WHERE:
    
    ### Estabelece condição para as informações mostradas

    ```SQL 
        SELECT * FROM aluno WHERE idade = 18
    ```
    
    * ### Leia-se: <font color="cyan">SELECIONE todos os campos DE aluno EM QUE idade seja 18</font>

    * ### Retorno/Saída: As informações de todos os alunos cuja idade seja igual a 18 (condição).

    ***

    ## 4. Plus: 
    ### Retornar as informações dos alunos cujo nome se inicia com J

    ```SQL 
    SELECT * FROM aluno WHERE nome LIKE 'j%'
    ```

***

## **_Operadores relacionais_**
***

## [**=**]

* ### Expressa igualdade entre os operandos (geralmente numéricos)

    * ### Alunos cuja idade seja igual a 18

        ```SQL 
        SELECT * FROM aluno WHERE idade = 18        
        ```
***

## [**LIKE**]
    
* ###  Também expressa igualdade, porém para texto.
    
    * ### Professores cujo nome seja semelhante João
    
        ```SQL
        SELECT * FROM professores WHERE nome LIKE 'joao'
        ```

* ### Além de igualdade, pode expressar semelhança ou pertencimento.

    * ### Professores cujo nome se inicie com J

        ```SQL
        SELECT * FROM professores WHERE nome LIKE 'j%'
        ```

    * ### Professores cujo  se encerre com A

        ```SQL
        SELECT * FROM professores WHERE nome LIKE '%a'
        ```

    * ### Professores que, em seu nome completo, possuam Souza

        ```SQL
        SELECT * FROM professores WHERE nome LIKE '%souza%'
        ```

        ### Detalhe: em SQL toda referência a textos deve vir entre aspas. As '%' são usadas para se referir a elementos desconhecidos.
***

## [**>**]

* ### Maior que

    * ### Alunos cuja idade seja maior que 16

        ```SQL
        SELECT * FROM alunos WHERE idade > 16
        ```
***

## [**>=**]

* ### Maior ou igual 

    * ### Alunos cuja idade seja maior ou igual a 18 (adultos)

        ```SQL
        SELECT * FROM alunos WHERE idade >= 18
        ```
***

## [**<**]

* ### Menor que

    * ### Alunos cuja idade seja menor que 10
    
        ```SQL
        SELECT * FROM alunos WHERE idade < 10
        ```
***

## [**<=**]

* ### Menor ou igual

    * ### Professores cuja idade seja menor ou igual a 40

        ```SQL
        SELECT * FROM professores WHERE idade <= 40 
        ```
***

## [**<>**]

* ### Caráter de 

* ### Não igual a

    * ### Alunos cuja turma nao seja a 1211

        ```SQL
        SELECT * FROM alunos WHERE turma <> 1211  
        ```
***

## [**!=**]

* ### Diferente de

    * ### Alunos cuja matrícula seja diferente de 3

        ```SQL
        SELECT * FROM alunos WHERE matricula != 3 
        ```

***

## **_Operadores Matemáticos_**

### <center><font color="cyan">Em SQL, também podemos utilizar operadores matemáticos como adição (+) , subtração (-) , multiplicação (*) , divisão (/) e módulo (%)</font></center>

#### **Exemplo**:
    
```SQL
Adição
SELECT * FROM aluno WHERE matricula = 1+1

Subtração
SELECT * FROM aluno WHERE matricula = 4-3

Multiplicação
SELECT * FROM aluno WHERE matricula = 2*2

Divisão
SELECT * FROM aluno WHERE matricula = 4/2

Módulo
SELECT * FROM aluno WHERE matricula = 4%3
```

***

## **_Operadores Lógicos_**
***

## [**AND**]

* ### Valor lógico de adição (E &&)

    * ### **Exemplo**:

        * ### Jogadores de um time de futebol, cujos nomes se iniciam por "J" e sua idade seja inferior a 30 anos.

            ```SQL
            SELECT * FROM time_de_futebol WHERE nome LIKE 'j%' AND idade < 30 
            ```
***

## [**OR**]

* ### Valor lógico de alternativa ( OU || )

    * ### **Exemplo**:

        * ### Alunos cuja matrícula seja maior do que 1 ou cujo nome se inicie com J

            ```SQL
            SELECT * FROM aluno WHERE matricula > 1 OR nome LIKE 'j%'
            ```
***

## [**BETWEEN**]

* ### Valor lógico de intervalo

    * ### **Exemplo**:
        
        * ### **_Buscar intervalo [<font color="orange">between</font>]_**: Todos os funcionários cujo id_funcionario esteja entre 4 e 7

            ```SQL
            SELECT * FROM funcionarios WHERE id_funcionario BETWEEN 4 AND 7
            ```

            ### Leia-se: <font color="cyan">Selecionar tudo dos funcionarios cujo id_funcionario esteja entre 4 e 7</font>

        * ### **_Ignorar intervalo [<font color="orange">not between</font>]_**: Todos os funcionários cujo id_funcionario NÃO esteja entre 15 e 54

            ```SQL
            SELECT * FROM funcionarios WHERE id_funcionario NOT BETWEEN 15 AND 54
            ```

            ### Leia-se: <font color="yellow">Selecionar tudo dos funcionarios cujo id_funcionario NÃO esteja entre 15 e 54</font>
***

## [**IN**]

* ### Retorna elementos da entidade (tabela) que, em determinado campo, possui um valor a ser especificado entre parênteses

    * **Exemplo**:

        * ### **_Selecionar departamentos [<font color="orange">IN</font>]_**: Funcionários que sejam dos departamentos 2 e 5

            ```SQL
            SELECT * FROM funcionarios WHERE departamento IN (2, 5)
            ```

            ### Retorno: <font color="skyblue">Todos elementos dentro da entidade funcionários cujo campo departamento possui valor 2 ou 5.</font>
        
        * ### **_Ignorar departamentos [<font color="orange">NOT IN</font>]_**: Todos os funcionários, exceto os que sejam dos departamentos 1, 3 e 4

            ```SQL
            SELECT * FROM funcionarios WHERE departamento NOT IN (1, 3, 4)
            ```
***

## [**IS NULL**]

* ### O operador IS verifica se o campo é (NULL), ou seja, vazio.

    * **Exemplo**:

        * **_Selecionar nulos [<font color="orange">IS NULL</font>]_**:

            * ### Todos os funcionários da empresa que NÃO tem departamento, ou seja, NULOS.

                ```SQL
                SELECT * FROM funcionarios WHERE departamento IS NULL
                ```
        
        * **_Selecionar não-nulos [<font color="orange">IS NOT NULL</font>]_**:

            * ### Todos os funcionários de uma empresa, exceto os que não possuem departamento [NULOS].

                ```SQL
                SELECT * FROM funcionarios WHERE departamento IS NOT NULL
                ```

***

# **_<font color="Orange"><center>Outros Comandos</center></font>_**

## [**INSERT INTO**]

* ### Responsável por inserir um novo elemento em uma entidade (tabela)

* ### **Exemplo**:

    ## Inserindo o aluno Kaik na lista de alunos

    ```SQL
    INSERT INTO alunos (nome, cpf, responsavel) VALUES ('Kaik Barreto', 12345678900, 'Luciana Barreto')
    
    leia-se:

    Inserir em [entidade] (campo1, campo2, campo3) os valores (valor1, valor2, valor3)
    ```
***

## [**UPDATE**]

* ### Responsável por alterar/atualizar um dado que já foi inserido na tabela. 

* ### **Exemplo**:

    * ### Alterar o nome de Kaik para Maria Luiza e o nome do responsavel para Michel 

        ```SQL
        UPDATE aluno SET nome="Maria Luiza Barreto", responsavel="Michel Martins" WHERE matricula = 2
        ```

    * ### Leia-se: <font color="yellow">Atualizar a tabela aluno definindo o nome como Maria Luiza Barreto e o nome do responsável como Michel Martins no elemento cuja matrícula [ Primary Key/Identificador ] é 2.</font>
***

## [**DELETE**]

* ### Permite apagar um elemento da entidade

* ### Necessita, <font color="Red">SEMPRE</font>, do WHERE.

* ### **Exemplo**:

    * ### Excluir o aluno João Castro do banco de dados de alunos

        ```SQL
        DELETE FROM alunos WHERE matricula = 3
        ```
    
    * ### Leia-se: <font color="yellow">Apagar da tabela alunos o elemento cuja matrícula [ Primary Key/Identificador ] é 3.</font>
***

## [**JOIN**]

* ### Permite unir tabelas (entidades) e mostrar, em um único **SELECT**, informações correlacionadas entre as tabelas, como a ligação de uma **Primary Key** e uma **Foreign Key**.

* ### **Exemplo**:

    * ### Mostrar a tabela de funcionarios e sua respectiva relação com a tabela de departamentos

        ```SQL
        SELECT * 
        FROM funcionarios 
        JOIN departamentos 
        ON departamentos.id_dept = funcionarios.id_departamento
        ```

        * ### Leia-se: <font color="cyan">Selecionar todos os dados da tabela funcionários e unir com os dados da tabela departamentos, onde o ID do departamento [respectivamente <font color="yellow">**Primary Key** e **Foreign Key**</font>] seja igual. </font>

* ### **JOIN com WHERE**

    * ### Buscar apenas os funcionários cujo departamento seja o de TI

        ```SQL
        SELECT * 
        FROM funcionarios 
        JOIN departamentos 
        ON departamentos.departamento = funcionarios.departamento 
        WHERE funcionarios.departamento LIKE 'ti'
        ```

* ### **JOIN especificando campos**

    * ### Buscar somente o nome, o CPF e o departamento dos funcionários.

        ```SQL
        SELECT funcionarios.nome, funcionarios.cpf, departamentos.descricao
        FROM funcionarios 
        JOIN departamentos
        ON funcionarios.id_departamento = departamentos.id_dept
        ```

            Nota-se que, uma vez que serão buscadas informações de diferentes entidades, é importante especificar qual é a entidade do campo que será buscado.
***

## [**ALIAS**]

* ## Comando AS:
    
    * ### Define um nome temporário para o escopo do SELECT, em função de tornar mais fácil a identificação

    * ### **Exemplo**:

        ```SQL
        SELECT func.nome AS 'NOMEZAO', func.cpf AS 'CPFzinho', dept.descricao AS 'Departamento'
        FROM funcionarios AS func
        JOIN departamentos AS dept
        ON func.id_departamento = dpt.id_dept
        ```

    * ## RETORNO:

        | NOMEZAO | CPFzinho | Departamento
        | :-: | :-: | :-: |
        |Jaqueline|14420559218|RH|
        |Kaik|19616035720|TI|

    * ### <font color="yellow">Resultado: O nome das entidades e dos campos não foi alterado, apenas foram apelidados dentro do escopo do comando, podendo ser utilizado pelo apelido.</font>
***

## [**LEFT OUTER JOIN**]

* ### Permite trazer para a seleção elementos que não tenham o relacionamento especificado

    * ### **Exemplo**:

        * ### Trazer todos os elementos da entidade ainda que algum deles não se relacione com a outra entidade correlata.

            ```SQL
            SELECT * FROM funcionarios 
            LEFT OUTER JOIN departamentos
            ON funcionarios.id_departamento = departamentos.id_dept
            ```

    * ### Leia-se: <font color="yellow">Mostre todo o conteúdo da tabela funcionários, mesmo que algum elemento não possua o relacionamento especificado</font>

    * ## RETORNO:

        | nome | cpf | id_departamento | id_dept | descricao
        | :-: | :-: | :-: | :-: | :-: |
        |Cristiano|14458794520|2|2|TI|
        |Jaqueline|14420559218|(NULL)|(NULL)|(NULL)|

        * ### <font color="lightgreen">Ou seja, Jaqueline foi listada, ainda que não possua um departamento.</font>
***

## [**ORDER BY**]

* ### Permite ordenar os dados requisitados baseado em um campo.

    * ### **Caso o campo seja do tipo TEXT, a ordem será alfabética, se for do tipo NUMBER será por ordem numérica etc.**

    * ### **Exemplo**:

        ```SQL
        SELECT * FROM aluno ORDER BY nome
        ```

        ### Retorno: *Todos os dados da entidade aluno, em ordem do campo nome.*

* ### **DESC**

    * ### *Faz com que a ordenação seja feita na ordem inversa, ou seja, decrescente (descending)*

        ```SQL
        SELECT * FROM aluno ORDER by matricula DESC
        ```

        ### Retorno: *Todos os dados da entidade aluno, em ordem descendente do campo matrícula.*
***

## [**LIMIT**]

* ### Possibilita limitar o número de elementos (linhas) mostrados.

    * ### Mostrar os primeiros 5 alunos, em ordem alfabética do nome.

        ```SQL
        SELECT * FROM aluno ORDER BY nome LIMIT 5
        ```
***

## [**OFFSET**]

* ### **Permite definir um ponto de partida para a requisição das informações de uma entidade, ignorando tantos elementos quanto forem especificados com o OFFSET e começando no próximo.**

    * ### Mostrar os primeiros 5 elementos de uma tabela, começando a partir do terceiro.

        ```SQL
        SELECT * FROM funcionarios LIMIT 5 OFFSET 2
        ```

        * Leia-se: <font color="cyan">Selecionar todos os campos da entidade funcionarios com o limite de 5 elementos, **ignorando os 2 primeiros.**</font>

***

## [**COUNT**]

* ### Permite **CONTAR** quantos elementos hão em um determinado campo de uma entidade(tabela)

    * ### **Exemplo**:

        * ### <font color="cyan">Selecionar a contagem de elementos no campo nome da entidade funcionarios</font>

            ```SQL
            SELECT COUNT(nome) FROM funcionarios
            ```

***

## [**GROUP BY**]

* ### Permite **AGRUPAR** elementos de acordo com um valor do campo que é comum a esses elementos.

    * ### **Exemplo**:

        * ### Contar quantos alunos há em cada turma

            ```SQL
            SELECT turma, COUNT(turma.alunos) 
            FROM alunos 
            GROUP BY turma
            ```
        * Leia-se: <font color="cyan">Mostrar a turma e o número de pessoas desta turma, agrupando por turmas.</font>

***

## <center>**_[JOIN_, _GROUP BY_ e _COUNT_ juntos]**</center>

* ### Uso: Reunir todos as turmas e uma contagem de alunos por turma.

    ```SQL
    SELECT COUNT(turma.alunos)
    FROM alunos
    JOIN turmas
    ON turmas.numero_da_turma = alunos.turma
    GROUP BY turmas.numero_da_turma
    ```

* ### **Exemplo de Retorno:**

|Turma|Qtd. de Alunos na turma|
|:-: | :-: |
|1001|37|
|1101|15|
|1203|28|

***

## [**HAVING**]

* ### Estendendo o uso do **GROUP BY**, o **HAVING** é uma forma de estabelecer uma condição para a impressão dos dados agrupados.

    * ### **Exemplo de uso**:

        * ### Reunir **APENAS** as turmas que **POSSUAM** mais de 20 alunos e uma contagem de alunos por turma.

            ```SQL
            SELECT COUNT(turma.alunos)
            FROM alunos
            JOIN turmas
            ON turmas.numero_da_turma = alunos.turma
            GROUP BY turmas.numero_da_turma
            HAVING COUNT(turma.alunos) > 20
            ```

* ### **Retorno:**

|Turma|Qtd. de Alunos na turma|
|:-: | :-: |
|1001|37|
|1203|28|

***

# **_<font color="Orange"><center>Comandos de tabelas</center></font>_**

## [**CREATE TABLE**]

* ### Permite a **CRIAÇÃO** de novas **TABELAS**

* ### Sintaxe:

    * ### CREATE TABLE nome_da_tabela (campo_da_tabela TIPO_DO_CAMPO)

* ### **Exemplo**:

    ```SQL
    CREATE TABLE alunos (
        matricula INTEGER PRIMARY KEY AUTOINCREMENT,
        nome TEXT,
        cpf INTEGER UNIQUE,
        responsavel TEXT
    )

    CREATE TABLE professores (
        id_professor INTEGER PRIMARY KEY AUTOINCREMENT,
        nome TEXT,
        cpf INTEGER UNIQUE,
        materia TEXT
    )

    CREATE TABLE aulas (
        id_professor INTEGER FOREIGN KEY,
        matricula,
        FOREIGN KEY(id_professor) REFERENCES professores(id_professor)
        FOREIGN KEY(matricula) REFERENCES alunos(matricula)
    )
    ```

* ### Elementos: 
    
    * ### Integer - Número Inteiro
    
    * ### PRIMARY KEY - Não pode ser repetido

    * ### FOREIGN KEY - Refere-se a uma PRIMARY KEY de outra tabela 

    * ### AUTOINCREMENT - Ao adicionar um elemento num campo com **incremento automático**, o campo automáticamente recebe um valor, na ordem dos já presentes no campo.

    * ### TEXT - Texto

    * ### Unique - Não podem haver iguais no mesmo campo

***

## [**ALTER TABLE**]

* ### Comando responsável por fazer alterações em tabelas já existentes.

* ### **Exemplo**:

    * ### **Alterar Tabelas**: Mudar o nome da tabela [aluno] para [alunos]

        ```SQL
        ALTER TABLE aluno RENAME TO alunos
        ```
    
        ### Leia-se: <font color="cyan">ALTERAR A TABELA aluno RENOMEAR PARA alunos</font>

        ***

    * ### **Alterar Campos**: Mudar o nome do campo [id_aluno] para [matricula_aluno]

        ```SQL
        ALTER TABLE aulas RENAME COLUMN id_aluno TO matricula_aluno
        ```
    
        ### Leia-se: <font color="cyan">ALTERAR TABELA aulas RENOMEAR COLUNA id_aluno PARA matricula_aluno</font>

***

## [**DROP TABLE**]

* ### Permite apagar uma tabela/entidade

* ### **Exemplo**:

    * ### Remover a tabela alunos

        ```SQL
        DROP TABLE alunos
        ```

***

# <center><font color="orange">Fim :D</font></font>