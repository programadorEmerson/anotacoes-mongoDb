Adicionando múltiplos valores a um array
Se você quiser adicionar múltiplos valores a um array , isso também é possível utilizando o operador $push , mas dessa vez será necessário adicionar o modificador $each .
A operação abaixo adicionará mais dois produtos ao array items do primeiro documento na coleção supplies :
<p>
db.supplies.updateOne(
  {},
  {
push: {
  items: {
    each: [
          {
            "name": "pens",
            "price": 56.12,
            "quantity": 5,
          },
          {
            "name": "envelopes",
            "price": 19.95,
            "quantity": 8,
          },
        ],
      },
    },
  },
  { upsert: true },
);
<p>
Resultado:
<br>
{
  _id : 1,
  items : [
      {
          "name" : "notepad",
          "price" : 35.29,
          "quantity" : 2,
      },
      {
          "name" : "pens",
          "price" : 56.12,
          "quantity" : 5,
      },
      {
          "name" : "envelopes",
          "price" : 19.95,
          "quantity" : 8,
      },
  ],
}