Uma maneira simples de remover o primeiro ou o último elemento de um array é utilizar o operador $pop . Passando o valor -1 ao operador $pop você removerá o primeiro elemento. Já ao passar o valor 1 , você removerá o último elemento do array . Simples, não é?!
Dado o seguinte documento na coleção supplies :
<br>
{
  _id: 1,
  items: [
    {
      "name" : "notepad",
      "price" : 35.29,
      "quantity" : 2,
    },
    {
      "name": "envelopes",
      "price": 19.95,
      "quantity": 8,
    },
    {
      "name": "pens",
      "price": 56.12,
      "quantity": 5,
    },
  ],
}
<br>
Removendo o primeiro item de um array
Para remover o primeiro elemento do array items , utilize a seguinte operação:
db.supplies.updateOne({ _id: 1 }, { $pop: { items: -1 } });
<br>
{
  _id: 1,
  items: [
    {
      "name": "envelopes",
      "price": 19.95,
      "quantity": 8,
    },
    {
      "name": "pens",
      "price": 56.12,
      "quantity": 5,
    },
  ],
}
<br>
Obs. $pop -1 remove o primeiro item e o $pop 1 remove o último
<br>
Removendo o último item de um array
Para remover o último elemento do array items , utilize a seguinte operação:
db.supplies.updateOne({ _id: 1 }, { $pop: { items: 1 } });
<br>
Executando essa operação, é removido o último elemento do array items , e o documento ficará assim:
<br>
{
  _id: 1,
  items: [
    {
      "name" : "notepad",
      "price" : 35.29,
      "quantity" : 2,
    },
    {
      "name": "envelopes",
      "price": 19.95,
      "quantity": 8,
    },
  ],
}