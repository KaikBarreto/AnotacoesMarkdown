# **<center><font size="10" color="lightblue">RegEx</font></center>**

* ## **O que é:**

    * ### **Expressões regulares**, ou **RegEx**, são padrões utilizados para selecionar combinações de caracteres em uma string, comuns para validação de dados.

    * ### É uma ferramenta interessante quando deseja-se limitar a um formato específico o input de um usuário. Ex.: quando deseja-se que o input seja somente um e-mail.

***

## <center><font color=orange size=5>**Símbolos genéricos de expressões regulares**</font>

### Para representar os padrões da RegEx, utilizam-se símbolos combinados entre si.

* ## <font color=orange>**[ . ]**</font>

    ### Significa **_qualquer caracter exceto uma nova linha_**.

    ***

* ## <font color=orange>**[ * ]**</font>

    ### Significa **_0 ou mais repetições_**.

    ***

* ## <font color=orange>**[ + ]**</font>

    ### Significa **_1 ou mais repetições_**.

    ***

* ## <font color=orange>**[ ? ]**</font>

    ### Significa **_0 ou 1 repetição_**.

    ***

* ## <font color=orange>**[ {n} ]**</font>

    ### Significa **_n repetições_**.

    ***

* ## <font color=orange>**[ {m, n} ]**</font>

    ### Significa **_m - n repetições_**, ou seja: um **_intervalo de repetições permitidas_** para um elemento da expressão regular.

    ***

## Por exemplo, utilizando expressões regulares, é possível validar um e-mail, da seguinte forma:

* ### Para isso, far-se-á o uso da linguagem <font color=cyan size=5>**_Python_**</font>.

    ```python
    import re # importando a biblioteca de expressões regulares

    email = input("Qual é o seu e-mail? ").strip() # pegando email do usuário e removendo espaço em branco


    # utilizando o método search para ver se a string email corresponde ao padrão (.+@.+)
    if re.search(".+@.+\.com", email):
        print("Email válido!")
    else:
        print("Email inválido!")
    ```
    
    > ### Apêndice: a contrabarra <font color=orange>**(\\)**</font> presente antes de ".com" é para indicar que o "." presente no final do endereço de e-mail é um ponto literalmente, e não um símbolo das expressões regulares.

    ***

### Porém, dessa forma gera-se um problema: não se sabe onde inicia a string da expressão regular.

***

## <center><font color=orange size=5>**Símbolos de início e final de expressões regulares**</font>

* ## <font color=orange>**[ ^ ]**</font>

    * ### Sinaliza o **_início de uma string da expressão regular_**.

    ***

* ## <font color=orange>**[ $ ]**</font>

    * ### Sinaliza o **_fim de uma string da expressão regular_**.

***

## Então, o código em python ficaria mais como:

```python
import re # importando a biblioteca de expressões regulares

email = input("Qual é o seu e-mail? ").strip() # pegando email do usuário e removendo espaço em branco


# utilizando o método search para ver se a string email corresponde ao padrão (.+@.+)
if re.search("^.+@.+\.com$", email):
    print("Email válido!")
else:
    print("Email inválido!")
```

> ### Assim, fica claramente indicado onde começa e termina a string.

***

## Também é possível definir uma lista de caracteres permitidos em um determinado espaço da string.


### Por exemplo, definir uma RegEx para que a string contenha 1 ou mais vogais:

* ### <font color=cyan>**" [aeiou]+ "**</font> significa "1 ou mais caracteres dentro da lista [aeiou]".

***

## Ou então, é possível restringir o espaço para conter qualquer caracter **EXCETO** o que estiver dentro da lista.

### Por exemplo, definir uma RegEx para que a string contenha 1 ou mais caracteres que **NÃO** sejam vogais:

* ### <font color=cyan>**" [^aeiou]+ "**</font> significa "1 ou mais caracteres exceto os da lista [aeiou].

***

## Também é possível especificar algumas sequencias de caracteres:

* ### <font color=cyan>**" [a-z]+ "**</font> significa "1 ou mais caracteres que estejam entre a e z minúsculos".

* ### <font color=cyan>**" [^A-Z]+ "**</font> significa "1 ou mais caracteres que não estejam entre A e Z maíusculos".

* ### <font color=cyan>**" [0-9]+ "**</font> significa "1 ou mais caracteres que estejam entre 0 e 9".

***

## <center><font color=orange size=5>**Símbolos específicos de expressões regulares**</font>

* ## <font color=orange>**[ \d ]**</font>

    ### Significa **_um dígito decimal [0-9]_**.

    ***

* ## <font color=orange>**[ \D ]**</font>

    ### Significa **_um caractere que não seja um dígito decimal [^0-9]_**.

    ***

* ## <font color=orange>**[ \s ]**</font>

    ### Significa **_caracter vazio (espaço vazio)_**.

    ***

* ## <font color=orange>**[ \S ]**</font>

    ### Significa **_qualquer caractere não vazio_**.

    ***

* ## <font color=orange>**[ \w ]**</font>

    ### Significa **_qualquer caractere de palavra, número ou underline_**.

    * ### caractes de palavra: a-z; A-Z; 0-9; _. 

    ***

* ## <font color=orange>**[ \W ]**</font>

    ### Significa **_qualquer caractere exceto um caractere de palavra_**.

***


## <center><font color=orange size=5>**Símbolos lógicos de expressões regulares**</font>

* ## <font color=orange>**[ A | B | C ]**</font>

    ### Significa **_ou A, ou B ou C._**.

    * ### Exemplo de uso: diferentes terminações:

    * ### "nome@dominio\.(com|net|gov)"

    ***

* ## <font color=orange>**[ (...) ]**</font>

    ### Significa **_um grupo_** (capturado pelo retorno da função).

    ### Serve para agrupar lógica e elementos.

    ### **Ex.:**

    * ## **<font color=orange size=6>"<font color=red>(</font><font color=cyan>[abcd]*</font><font color=red>)?</font>"</font>**

        * ### Leia-se: **<font color=red>0 ou 1 unidade do grupo: </font> <font color=cyan>(0 ou mais caracteres do grupo [abcd])</font>**

    ### Agrupando desta forma, o que estiver dentro dos parênteses será retornado para a função de RegEx. 

    ***

* ## <font color=orange>**[ (?: ...) ]**</font>

    ### **?: Grupo não capturado:** indica um grupo que não constará na lista de grupos capturados.


    ***

* ## <font color=orange>**[ (...)? ]**</font>

    ### Uma sintaxe assim, agrupando conceitos como o de **grupo** e o de **0 ou 1 aparição de um elemento**, permite gerar estruturas mais complexas.

    ### **Exemplo:** representar um site com domínio, subdomínio e TLD. (subdomínio.domínio.tld), onde o subdomínio é opcional.

    * ### **<font color=cyan size=7><font color=lime>(\w+\\.)?</font><font color=red>\w+</font><font color=yellow>\\.</font>\w{3}</font>**

        * <font color=orange>Leia-se: **<font color=lime>(1 ou mais caracter de palavra e um ponto) opcionalmente</font>, <font color=red>um ou mais caracteres de palavra</font>, <font color=yellow>um ponto</font> e <font color=cyan>3 caracteres de palavra</font></font>.**

    ### **Note-se que toda a estrutura de "subdomínio." foi englobada em um operador de lógica (os parênteses) e após isso uma interrogação, permitindo que haja 0 ou 1 aparição do elemento englobado pelos parênteses.**

    ### Note-se também que na última sequência de caracteres, foi especificado que devem ser 3, como é o padrão de TLD (top-level domain) na internet, como o ".com".

    ***




