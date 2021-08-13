Quando o <boolean> é verdadeiro ( true ), o operador $exists encontra os documentos que contêm o atributo , incluindo os documentos em que o valor do atributo é igual a null . Se o <boolean> é falso ( false ), a consulta retorna somente os documentos que não contêm o atributo.
Veja o exemplo abaixo:

db.inventory.find({ qty: { $exists: true } })
Essa consulta retorna todos os documentos da coleção inventory em que o atributo qty existe.
Você também pode combinar operadores, como no exemplo abaixo:

db.inventory.find({ qty: { $exists: true, $nin: [ 5, 15 ] } })
Essa consulta seleciona todos os documentos da coleção inventory em que o atributo qty existe E seu valor é diferente de 5 e 15 .