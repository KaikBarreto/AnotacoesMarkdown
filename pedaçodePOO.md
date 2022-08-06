## <center><font size=7 color=orange>**Operator Overloading**</font>

* ## Trata-se da ressignificação de um operador, como "+" ou "*", para uma classe.

* ### Para ressignificar um operador para uma classe em python, é necessário utilizar métodos especiais correspondentes a cada operador e designar uma função para o mesmo.

* ### **Exemplo:** atribuir uma função à soma de duas instâncias de uma classe (objetos).

    ```python
    class Família:
        def __init__(self, número_de_integrantes):
            self.número_de_integrantes = número_de_integrantes 
        
        def __add__(self, other):
            novo_número_de_integrantes = self.número_de_integrantes + other.número_de_integrantes

            return Familia(novo_número_de_integrantes)

    silva = Familia(5) # 5 integrantes
    moreira = Familia(15) # 15 integrantes
    silvaMoreira = silva + moreira # 20 integrantes (silva + moreira / 5 + 15)

    ```

    1. ### Neste exemplo, é gerada uma classe Família, cuja instância recebe um número de integrantes.

    2. ### Assim, cada objeto instanciado a partir da classe Família possui seu próprio número de integrantes

    3. ### Porém, ao somar dois objetos da classe Família, é chamado o método **add**, que recebe como parâmetros os dois objetos somados e então retorna uma nova instância da classe Família, cujo número de integrantes é a soma do número de integrantes das duas famílias