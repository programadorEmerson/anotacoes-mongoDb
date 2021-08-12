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

db.movies.findMany(
    { "title" : "Forrest Gump" },
    { "title" : 1, "imdb_rating" : 1 }
)

Para trazer somente um atributo ex:
db.colection.findMany({}, { name: 1 }) // 1 true, 0 false

utilize comparadores ex: 
db.collection.findMany( { chave: { $compador: valor } } )

comparadores: 
$lt ( less than , menor que, <)<br>
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
