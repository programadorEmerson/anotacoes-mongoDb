Com o operador $inc , você pode incrementar ou decrementar valores em um campo específico, utilizando tanto valores positivos quanto negativos.
Esse operador é bastante útil para fazer alterações em campos numéricos sem a necessidade prévia de uma consulta para retornar o valor atual do campo. Com o $inc , em uma única operação isso é possível!
Considere que você tenha o seguinte documento na coleção increment :

db.increment.insertOne(
  {
    _id: 1,
    sku: "abc123",
    quantity: 10,
    metrics: {
      orders: 2,
      ratings: 3.5
    }
  }
)

Na operação de update a seguir, o operador $inc é utilizado para decrementar o valor do campo qty em 2 (incrementa em -2 ) e incrementar o valor do campo metrics.orders em 1 :

db.increment.update(
  { sku: "abc123" },
  { $inc: { quantity: -2, "metrics.orders": 1 } }
);

O documento alterado ficará assim:

{
  "_id": 1,
  "sku": "abc123",
  "quantity": 8,
  "metrics": {
    "orders": 3,
    "ratings": 3.5
  }
}

Note que, em uma única chamada ao operador $inc , você consegue aumentar e diminuir os valores de campos diferentes.