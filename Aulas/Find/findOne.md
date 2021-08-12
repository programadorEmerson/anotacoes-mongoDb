O método find() serve para selecionar os documentos de uma coleção e retorna um cursor com esses documentos.
Esse método recebe dois parâmetros:
db.collection.find(query, projection)
query (opcional):
Tipo: documento;
Descrição: especifica os filtros da seleção usando os query operators . Para retornar todos os documentos da coleção, é só omitir esse parâmetro ou passar um documento vazio ({}).
projection (opcional):
Tipo: documento;
Descrição: especifica quais atributos serão retornados nos documentos selecionados pelo parâmetro query . Para retornar todos os atributos desses documentos, é só omitir esse parâmetro.
Esse método retorna um cursor para os documentos que correspondem aos critérios de consulta.

db.colection.findOne(); Retorna tudo na coleção, sem filtros

db.colection.findOne(
    { "title" : "Forrest Gump" },
    { "title" : 1, "imdb_rating" : 1 }
)

utilize comparadores ex: 
db.collection.find( { chave: { $compador: valor } } )

Para trazer somente um atributo ex:
db.colection.find({}, { name: 1 }) // 1 true, 0 false

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