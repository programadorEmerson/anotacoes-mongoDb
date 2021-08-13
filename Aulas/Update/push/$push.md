O operador $push adiciona um valor a um array . Se o campo não existir no documento, um novo array com o valor em um elemento será adicionado.
Sintaxe:<br>
{ $push: { <campo1>: <valor1>, ... } }
<br>
Em conjunto com o $push , você pode utilizar o que chamamos de modificadores . Cada um desses modificadores tem funções específicas.<br>
$each : Adiciona múltiplos valores a um array ;<br>
$slice : Limita o número de elementos do array . Requer o uso do modificador $each ;<br>
$sort : Ordena os elementos do array . Requer o uso do modificador $each ;<br>
$position : Especifica a posição do elemento que está sendo inserido no array . Também requer o modificador $each . Sem o modificador $position , o operador $push adiciona o elemento no final do array .
<br>
Adicionando um valor a um array
Considere a coleção supplies , uma coleção vazia. A operação abaixo adiciona um objeto que tem as informações da compra de um produto ao array items do documento em que o _id seja igual a 1 na coleção supplies :
Para não precisarmos escrever uma query só para fazer o insert do documento, vamos usar a opção upsert: true para já adicionar o elemento ao mesmo tempo que usamos o operador $push . É importante ficar nítido que a condição upsert não influencia a forma como o $push funciona.
<br>
use sales;
db.supplies.updateOne(
  { _id: 1 },
  {
push: {
      items: {
        "name": "notepad",
        "price":  35.29,
        "quantity": 2,
      },
    },
  },
  { upsert: true },
);