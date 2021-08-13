O operador $nin seleciona os documentos em que o valor do atributo filtrado não é igual ao especificado no array , ou o campo não existe.
db.inventory.find( { qty: { $nin: [ 5, 15 ] } } )

Essa consulta seleciona todos os documentos da coleção inventory em que o valor do atributo qty é diferente de 5 e 15 . Esse resultado também inclui os documentos em que o atributo qty não existe.