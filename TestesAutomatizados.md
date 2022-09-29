# **<center><font size="10" color="lightblue">Testes Automatizados</font></center>**

## O que são testes e por que testar?
  
  - ### Objetivo dos testes: checar se a aplicação se comporta como esperado.

  - ### **Protege contra comportamento indesejado quando mudanças são realizadas na aplicação**.

  - ### Automatizam o processo de validar uma aplicação, e portanto são eficientes no longo-prazo.

    ---

## O quê testar?

  1. ### Features de alta importância

  2. ### **`"Edge cases"`** em features de alta importância

  3. ### Coisas que são fáceis de serem quebradas, ou seja, de pararem de funcionar.

      ---

## Testes automatizados são baseados em ***<font color=gold>asserções</font>***, ou seja, afirmações, relacionadas à aplicação, onde é possível atrelar uma funcionalidade a um resultado esperado. 

  - ### Caso a funcionalidade retorne o resultado esperado, pode-se dizer que a asserção é verdadeira e, portanto, o teste foi bem-sucedido.


  ---

## Para ilustração, será usado como linguagem **<font color=gold>JavaScript</font>** e, para isso, a biblioteca ***<font color=gold>Jest</font>***.

  ---

## O Jest possui uma sintaxe simples, onde, por meio de ***<font color=gold>asserções</font>***, é possível gerar testes práticos para uma aplicação.

- ## Uma vez instalado o Jest, <br><kbd>npm install --save-dev jest</kbd>,<br> eis um exemplo simples:

  ### <center> Arquivo: <font color=cyan>sum.js</font> (função a ser testada)

  ```js
  function sum(a, b) {
    return a + b;
  }
  module.exports = sum;
  ```

  ### <center> 1.  É esperado que a função "sum" retorne a soma dos dois valores passados como argumentos

  ### <center> 2. Repare que a exportação é feita da maneira node.js (module.exports = ...), e não da forma introduzida pelo es6 (import ... / export default)

  <br>

  ### <center> Arquivo: <font color=cyan>sum.test.js</font> (arquivo do teste em si)

  ```js
  const sum = require('./sum');

  test('soma 1 + 2 igual a 3', () => {
    expect(sum(1, 2)).toBe(3);
  });
  ```

  - ### **test**: é a função que **introduz** o teste, sendo seu primeiro argumento uma string contendo o nome do teste, e seu segundo uma função anônima contendo as asserções

  - ### **expect**: é a parte do teste que indica o que será feito

  - ### **toBe**: é a função que representa a ***<font color=gold>asserção</font>*** do teste, ou seja, o valor que é esperado para o resultado do que é passado no `expect`

  - ### **Resultado do teste:** ***<font color=lime>PASSOU!</font>***, pois realmente a função sum, recebendo 1 e 2 como argumentos, retorna 3.