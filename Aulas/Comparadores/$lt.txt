O operador $lt seleciona os documentos em que o valor do atributo filtrado é menor do que (<) o 
db.inventory.find({ qty: { $lt: 20 } })

Essa consulta selecionará todos os documentos na coleção inventory cujo valor do atributo qty é menor do que 20 