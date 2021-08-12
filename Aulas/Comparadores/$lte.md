O operador $lte seleciona os documentos em que o valor do atributo filtrado é menor ou igual (<=) ao valor especificado.
db.inventory.find({ qty: { $lte: 20 } })

Essa query selecionará todos os documentos na coleção inventory cujo valor do atributo qty é menor ou igual a 20 .