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

Exemplo 2: Alterando campos em documentos embedados
Para alterar campos dentro de subdocumentos, você deve utilizar o mesmo conceito de dot notation visto durante as operações de find() .
A operação abaixo altera o valor do campo make dentro do subdocumento details em que o campo _id seja igual a 100 :

db.products.update(
  { _id: 100 },
  { $set: { "details.make": "zzz" } }
);