O operador $eq seleciona os documentos em que o valor do atributo filtrado é igual ao valor especificado. Esse operador é equivalente ao filtro { campo: <valor> } e não tem nenhuma diferença de performance.
db.inventory.find({ qty: { $eq: 20 } })

A operação acima é exatamente equivalente a:
db.inventory.find({ qty: 20 })