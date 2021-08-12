O operador $not executa uma operação lógica de NEGAÇÃO no < operador ou expressão > especificado e seleciona os documentos que não correspondam ao < operador ou expressão > . Isso também inclui os documentos que não contêm o atributo .
db.inventory.find({ price: { $not: { $gt: 1.99 } } })

Essa consulta seleciona todos os documentos na coleção inventory em que o valor do atributo price é menor ou igual a 1.99 (em outras palavras, não é maior que 1.99 ), ou em que o atributo price não exista.
É importante destacar que a expressão { $not: { $gt: 1.99 } } retorna um resultado diferente do operador $lte . Ao utilizar { $lte: 1.99 } , os documentos retornados serão somente aqueles em que o campo price existe e cujo valor é menor ou igual a 1.99 .