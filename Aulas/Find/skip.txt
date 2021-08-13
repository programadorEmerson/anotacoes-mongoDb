Acione o método skip() para controlar a partir de que ponto o MongoDB começará a retornar os resultados. Essa abordagem pode ser bastante útil para realizar paginação dos resultados.

O método skip() precisa de um parâmetro numérico que determinará quantos documentos serão "pulados" antes de começar a retornar.
O exemplo abaixo na coleção bios pulará os dois primeiros documentos e retornará o cursor a partir daí:
db.colection.find().skip(2)


Você pode combinar os métodos limit() e skip() criando, assim, uma paginação:
db.collection.find( { chave: { $compador: valor } } ).limit(5).skip(5)

comparadores: <br>
$lt ( less than , menor que, <)<br>
$lte ( less than or equal , menor ou igual a, <=)<br>
$gt ( greater than , maior que, >)<br>
$gte ( greater than or equal , maior ou igual a, >=)<br>
$eq ( equal , igual a, =)<br>
$ne ( not equal , diferente de, !=, <>)<br>
$in ( in , dentro de)<br>
$nin ( not in , não está dentro de)<br>
$and ( and , se todas as condições forem verdadeiras retorna true )<br>
$or ( or , se apenas uma condição for verdadeira retorna true )<br>
$not ( not , inverte o resultado da expressão)<br>
$nor ( not or , semelhante ao or , porém trabalha com a condição false )<br>
$exists ( exists , verifica a existência de um atributo)<br>