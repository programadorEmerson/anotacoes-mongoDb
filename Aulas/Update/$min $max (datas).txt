Comparando datas
Você pode utilizar os operadores $min e $max para comparar valores do tipo Date .
Considere o seguinte documento da coleção tags :

use conteudo_trybe;
db.tags.insertOne(
  {
    _id: 1,
    desc: "crafts",
    dateEntered: ISODate("2019-10-01T05:00:00Z"),
    dateExpired: ISODate("2019-10-01T16:38:16Z")
  }
);

A operação abaixo utiliza o operador $min para comparar o valor do campo dateEntered e altera seu valor porque 25/09/2019 é uma data menor (anterior) do que o valor atual, ao mesmo tempo em que o operador $max também é usado para comparar o valor do campo dateExpired e altera esse valor porque 02/10/2019 é uma data maior (posterior) do que o valor atual:

db.tags.update(
  { _id: 1 },
  {
min: { dateEntered: new Date("2019-09-25") },
max: { dateExpired: new Date("2019-10-02") }
  }
);