# **<center><font size="10" color="lightblue">Programação Orientada a Objetos (POO) </font>**

**<font color=orange size=5>Object-Oriented Programming (OOP) </font></center>**

## Para este assunto, usar-se-á como base a linguagem <font size=6 color=lime>**_Python_**</font>.

*** 

## **O que é orientação a objetos?**

* ### A POO é um paradigma de programação que se propõe a abordar o design de um sistema em termos de entidades, os objetos, e relacionamentos entre essas entidades. 

## **Como funciona?**

* ### Este paradigma funciona à partir de classes e objetos. As classes são como um molde, uma fábrica para os objetos, que por sua vez são os produtos.

***

## <center><font size=8 color=orange>**Classes**</font>

## Classes são estruturas de dados que permitem com que se criem novos tipos de dados. São como um diagrama, um molde para a construção de objetos.

.

## Através das classes, é possível passar características comuns aos objetos construídos por ela. 

* ### **Exemplo:** uma classe "carro" pode ter um atributo de possuir 4 rodas, e esse atributo será **herdada** por todos os objetos (carros) criados à partir desta classe.

* ### As classes podem receber parâmetros, dinamizando a criação de novas **instâncias** da mesma.

* ### Além disso, classes podem possuir não somente atributos, mas também métodos, ou seja, **funções**.

***

## **SINTAXE**

### Para a sintaxe, usar-se-á a linguagem python como referência, mas o paradigma de orientação a objetos é pertinente a muitas linguagens.

### Em python, a sintaxe para a criação de uma classe é a seguinte:

```python
class Carro:          
    # define uma classe chamada Carro

    def __init__(self, modelo_do_carro, ano_do_carro): 
        # toda classe em python se inicia com um método "__init__", que recebe PELO MENOS o parâmetro "self"

        self.modelo = modelo_do_carro
        self.ano = ano_do_carro
```

> ### O parâmetro **self** refere-se ao próprio objeto que está sendo criado nesta instância da classe e deve ser passado como parâmetro para todos os métodos da classe.
> ### Para atribuir o valor do parâmetro "modelo_do_carro" para o atributo "modelo" desta instância da classe, é preciso utilizar o self.

```python
celta = Carro("Chevrolet Celta", "2000")
# aqui cria-se uma INSTÂNCIA da classe Carro, onde é passado como parâmetro o modelo_do_carro e o ano_do_carro.

print(celta.modelo) 
# -> Chevrolet Celta

print(celta.ano) 
# -> 2000
```

> Por convenção, as classes geralmente começam em letra maíuscula.

***

## <center><font size=8 color=orange>**Objetos**</font>

## Objetos, no paradigma de orientação a objetos, são instâncias de uma classe. Ou seja, se a classe é um molde, o objeto é o produto criado à partir desta classe.

### Estes objetos podem ser instânciados com parâmetros, o que gera a diferença entre um ou outro objeto.

```python
class Estudante:
    def __init__(self, nome, idade):
        self.nome = nome
        self.idade = idade

bruno = Estudante(nome="Bruno Ferreira", idade=5)
# Dessa forma, é possível criar uma instância da classe Estudante, onde os parâmetros passados para nome e idade são, respectivamente, Bruno Ferreira e 5.

print(bruno.nome)
# -> Bruno Ferreira
print(bruno.idade)
# -> 5
```

***

## <center><font size=7 color=orange>**Properties, Getters e Setters**</font>

* ## **<font size=6 color=cyan>[Properties]</font>**:

    * ### Tratam-se de atributos de uma classe, com uma camada extra de segurança, controle e estabilidade.

    * ### Para isso, em python é usada uma keyword chamada **_<font color=yellow>@property</font>_**, que corresponde a uma função em python.

        * #### Funções com **_<font color=yellow>@</font>_** na frente em Python correspondem a um tipo de função chamado de **_<font color=yellow>decorators</font>_**, que servem para modificar o funcionamento de outras funções.

    ***

## **<font size=6 color=cyan>[Getters & Setters]</font>**:

* ### A estrutura de Getters & Setters permite que haja mais controle na manipulação de um atributo da instância da classe.

* ### Uma vez definindo o design de Getters & Setters, é possível realizar a validação de um atributo durante a definição (set) do mesmo.

    ### **<font size=5 color=yellow>[Getters]</font>**:
 
    * ### Tratam-se de funções em uma classe cuja responsabilidade é pegar um atributo da mesma.

    * ### Para definir um **getter**, adiciona-se logo acima da sua definição, um **_<font color=yellow>decorator</font>_** chamado  **_<font color=red>@property</font>_** 

    * ### **Exemplo:**

        ```python
        # Getter para atributo nome
        @property
        def nome(self):
            return self._nome
        ```
        ***

    ### **<font size=5 color=yellow>[Setters]</font>**:

    * ### Tratam-se de funções em uma classe cuja responsabilidade é definir um valor para um atributo da mesma.

    * ### Para definir um **setter**, adiciona-se logo acima da sua definição, um **_<font color=yellow>decorator</font>_** com a seguinte sintaxe: **<font color=red>@{nome_do_getter}.setter</font>**

        * #### Se o getter é **nome**, o setter seria **<font color=yellow>@nome.setter</font>**

    * ### **Exemplo:** setando um atributo "name" validando se ele está numa lista pré-definida.

        ```python
        # Getter para atributo nome
        @property
        def nome(self):
            return self._nome

        # Setter para atributo nome
        @nome.setter
        def nome(self, nome):
            if nome not in ["Kaik", "Malu", "Millena"]:
                raise ValueError("Nome inválido!")
            self._nome = nome
        ```

        ***

    * ### Assim, a estrutura, com validação, ficaria da seguinte forma:

        ```python
        class Pessoa: 
            # criação da classe
            def __init__(self, nome, idade):
                # criação do objeto (instância da classe)
                self.nome = nome
                self.idade = idade

            # Getter 
            @property
            def nome(self):
                return self._nome

            # Setter para nome 
            @house.setter
            def nome(self, nome):
                if nome not in ["Kaik", "Malu", "Millena"]:
                    raise ValueError("Nome inválido!")
                    # Validação

                self._nome = nome
        ```

    * ### Dessa forma, caso alguém tente atribuir um valor a um atributo do objeto, a classe redirecionará para o método setter, testando a validez do valor.

    * ### Uma vez que um atributo seja uma property, ou seja, tenha um controle (validação) de dados por meio de um getter e um setter, não é possível atribuir um valor inválido externamente.

    * ### Exemplo:

        ```python
        Kaik = Pessoa(nome="Kaik", idade="16")
        # criação do objeto Kaik instanciando a classe Pessoa, com os atributos nome e idade respectivamente iguais a Kaik e 16.

        Kaik.nome = "Kaik" 
        # reatribuição que passará pelo setter, validando-a
        # -> válido!

        Kaik.nome = "José"
        # reatribuição que passará pelo setter, validando-a
        # -> inválido!
        ```

    * > ### Há de notar-se que: ao usar getters e setters, o nome das funções não podem ser iguais ao nome da variável.

        * #### Exemplo: se o getter para nome é "nome(self)", o atributo nome não poderá ser chamado ("self.nome").

***

## <center><font size=6 color=orange>**Class Methods / Métodos de classe**</font>

* ## Consistem em **funções que não possuem acesso ao parâmetro self**, ou seja, ao objeto sendo criado na instância da classe. Dessa forma, a funcionalidade é pertinente à classe em si.

* ## Ao definir um método de classe, **esta função estará presente em todos os objetos instanciados à partir desta classe**.

    ***

* ## Para definir um método de classe, utiliza-se um **decorator** chamado **<font color=yellow>@classmethod</font>** logo acima da definição do método. Essa função/método também sempre receberá um parâmetro chamado "cls", referente à classe.

    ```python	
    import random
    class Moeda:
        # criação da classe Moeda

        girosPossíveis = ["Cara", "Coroa"]
        # criação da variável de classe (class variable) "girosPossíveis"

        @classmethod # decorator
        def girarMoeda(cls):
            # definição do método de classe "girarMoeda"

            print(f"O giro da moeda foi {cls.girosPossíveis}")
            # printando o giro da moeda, que está na classe, referenciada pelo parâmetro cls.

        
        Moeda.girarMoeda() # acessando o método direto da classe
        #-> O giro da moeda foi Cara | Coroa
    ```

    * ### Note-se que para acessar um método de classe, não é necessário instanciá-la, mas sim é possível acessar o método diretamente pelo nome da classe.

***

## <center><font size=7 color=orange>**Inheritance / Herança**</font>

## **O que é herança em orientação a objetos?**

* ### Trata-se de quando uma classe deriva de outra classe. A classe filha, também chamada **subclasse**, **herda** todas as propriedades e métodos da classe mãe, também chamada **superclasse**. Ademais, a subclasse pode ter suas próprias propriedades e métodos únicos. 

***

