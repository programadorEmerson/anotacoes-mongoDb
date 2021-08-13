O $set altera o valor de um campo específico.
Se o campo não existir, o operador $set adiciona um novo campo com o valor especificado. Se você especificar campos com dot notation , os documentos embedados necessários serão criados para suprir o caminho do campo.
Você pode especificar múltiplos pares de campos-valores que o operador $set alterará ou criará cada um desses campos.
Veja alguns exemplos considerando a coleção products com o seguinte documento:

use conteudo_trybe;
db.products.insertOne({
  _id: 100,
  sku: "abc123",
  quantity: 250,
  instock: true,
  reorder: false,
  details: { model: "14Q2", make: "xyz" },
  tags: [ "apparel", "clothing" ],
  ratings: [ { by: "ijk", rating: 4 } ]
})

Exemplo 1: Alterando campos no primeiro nível (top-level)
Para o documento que corresponder ao critério de filtro em que o campo _id seja igual a 100 , a operação a seguir altera o valor dos campos quantity , details e tags :

db.products.update(
  { _id: 100 },
  { $set: {
      quantity: 500,
      details: { model: "14Q3", make: "xyz" },
      tags: [ "coats", "outerwear", "clothing" ]
    }
  }
);

A operação acima altera o valor de quantity para 500 , details para um novo documento embedado e tags para um novo array .
No exemplo acima, vários campos foram agrupados e, com isso, são alterados em um mesmo comando! Assim, você pode alterar vários campos de uma única vez.