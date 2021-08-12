Para remover um ou mais campos de um documento, utilize o operador $unset .
Considerando o documento abaixo na coleção fruits :

{
  _id: 100,
  productName: "Banana",
  quantity: 100,
  inStock: true
}

A operação abaixo remove o campo quantity do documento em que o valor do campo productName seja igual a Banana :

db.fruits.updateMany(
  { productName: "Banana" },
  { $unset: { quantity: "" } }
);

E, como resultado, o documento ficará assim:

{
  _id: 100,
  productName: "Banana",
  inStock: true
}