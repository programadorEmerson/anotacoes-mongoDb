O operador $gt seleciona os documentos em que o valor do atributo filtrado é maior do que (>) o valor especificado.
db.inventory.find({ qty: { $gt: 20 } })

Essa query selecionará todos os documentos na coleção inventory cujo valor do atributo qty é maior do que 20 