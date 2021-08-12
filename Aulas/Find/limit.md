Você pode limitar o número de documentos retornados por uma consulta utilizando o método limit() . Esse método é semelhante à declaração LIMIT em um banco de dados que utiliza SQL .
Uma utilização comum do limit() é para maximizar a performance e evitar que o MongoDB retorne mais resultados do que o necessário para o processamento.
O método limit() é utilizado da seguinte forma:

db.colection.find().limit(5)

utilize comparadores ex: 
db.collection.find( { chave: { $compador: valor } } ).limit(5)

comparadores: 
$lt ( less than , menor que, <)
$lte ( less than or equal , menor ou igual a, <=)
$gt ( greater than , maior que, >)
$gte ( greater than or equal , maior ou igual a, >=)
$eq ( equal , igual a, =)
$ne ( not equal , diferente de, !=, <>)
$in ( in , dentro de)
$nin ( not in , não está dentro de)
$and ( and , se todas as condições forem verdadeiras retorna true )
$or ( or , se apenas uma condição for verdadeira retorna true )
$not ( not , inverte o resultado da expressão)
$nor ( not or , semelhante ao or , porém trabalha com a condição false )
$exists ( exists , verifica a existência de um atributo)