Esse operador é o contrário do anterior. Ao utilizar o $ne , o MongoDB seleciona os documentos em que o valor do atributo filtrado não é igual ao valor especificado.
db.inventory.find({ qty: { $ne: 20 } })

A query acima retorna os documentos da coleção inventory cujo valor do atributo qty é diferente de 20 , incluindo os documentos em que o atributo qty não existe.