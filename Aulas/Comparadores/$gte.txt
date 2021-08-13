O operador $gte seleciona os documentos em que o valor do atributo filtrado é maior ou igual (>=) ao valor especificado.
db.inventory.find({ qty: { $gte: 20 } })

Essa query selecionará todos os documentos na coleção inventory cujo valor do atributo qty é maior ou igual a 20 .