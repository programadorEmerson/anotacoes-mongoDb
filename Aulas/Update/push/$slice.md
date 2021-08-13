O operador $slice especifica o número de elementos em um array para retornar no resultado da consulta.
<p>
O $slice tem uma das seguintes formas de sintaxe:
<p>
db.collection.find(
   <query>,
   { <arrayField>: { $slice: número } }
);
<p>
ou
<p>
db.collection.find(
   <query>,
   { <arrayField>: { $slice: [ número, número ] } }
);
<p>
Especifique um número positivo para retornar os primeiros itens do array de elementos.
Especifique um número negativo para retornar os últimos itens do array de elementos.
Se número for maior que o número de elementos do array, a consulta retornará todos os elementos do array.

$slice: [ número para pular, número de retorno ]
Especifica o número de elementos a serem retornados do array após pular o número especificado de elementos começando do primeiro elemento. Você deve especificar os dois elementos.
<p>
Para o número para pular:
<p>
Especifique um número positivo para pular elementos do início do array; ou seja, 0 posição do índice. Com base em um índice do array baseado em zero, 1 indica a posição inicial do segundo elemento, etc. Se n for maior que o número de elementos do array, a consulta retorna umo array vazia para o array.
Especifique um número negativo n para pular os n elementos anteriores do início do array; ou seja, posição de índice 0 Com base em um índice do array baseado em zero (ou seja, o primeiro elemento está no índice 0), -1 indica a posição inicial do último elemento, etc. Se o valor absoluto do número negativo for maior que o número de elementos do array , a posição inicial é o início do array.
Para o número de retorno, você deve especificar um número positivo para retornar os próximos elementos, começando após pular o número especificado.
<p>
Por exemplo, considere uma coleção inventory com documentos que contêm:
<p>
{ 
  item: "socks",
   qty: 100, 
   details: { 
     colors: 
      [ 
        "blue", 
        "red" 
      ], 
      sizes: 
        [ 
          "S", 
          "M", 
          "L"
        ]
    }
}
<p>
a query a seguir retorna o _idcampo (por padrão), o qty campo e o details campo apenas com o $slice especificado da colors array:
<p>
db.inventory.find( { }, 
  { 
    qty: 1, 
    "details.colors": {
      $slice: 1 // primeiro item do array, se fosse -1 retornaria o ultimo
    } 
  } 
)
<p>
Ou seja, a query retorna o seguinte documento:
<p>
{ 
  "_id" : ObjectId("5ee92a6ec644acb6d13eedb1"), 
  "qty" : 100, 
  "details" : { 
    "colors" : 
    [
      "blue" 
    ] 
  } 
}
<p>
Retornando determinada quantidade de itens do array.
<p>
Considere:
<p>
db.posts.insertMany([
   {
     _id: 1,
     title: "Bagels are not croissants.",
     comments: [ { comment: "0. true" }, { comment: "1. croissants aren't bagels."} ]
   },
   {
     _id: 2,
     title: "Coffee please.",
     comments: [ { comment: "0. fooey" }, { comment: "1. tea please" }, { comment: "2. iced coffee" }, { comment: "3. cappuccino" }, { comment: "4. whatever" } ]
   }
])
<p>
Retorna um Array com seus 3 primeiros elementos 
A query a seguir usa o operador $slice em comments para retornar o array com seus três primeiros elementos. Se o array tiver menos de três elementos, todos os elementos serão retornados.
<p>
db.posts.find( {}, { comments: { $slice: 3 } } )
<p>
{
   "_id" : 1,
   "title" : "Bagels are not croissants.",
   "comments" : [ { "comment" : "0. true" }, { "comment" : "1. croissants aren't bagels." } ]
}
{
   "_id" : 2,
   "title" : "Coffee please.",
   "comments" : [ { "comment" : "0. fooey" }, { "comment" : "1. tea please" }, { "comment" : "2. iced coffee" } ]
}
<p>
Retornando um Array com seus últimos 3 elementos.
<p>
A query a seguir usa o operador $slice na query em comments array para retornar o array com seus três últimos elementos. Se o array tiver menos de três elementos, todos os elementos do array serão retornados.
<p>
db.posts.find( {}, { comments: { $slice: -3 } } )
<p>
{
   "_id" : 1,
   "title" : "Bagels are not croissants.",
   "comments" : [ { "comment" : "0. true" }, { "comment" : "1. croissants aren't bagels." } ]
}
{
   "_id" : 2,
   "title" : "Coffee please.",
   "comments" : [ { "comment" : "2. iced coffee" }, { "comment" : "3. cappuccino" }, { "comment" : "4. whatever" } ]
}
<p>
Retorne um Array com 3 Elementos após pular o primeiro.
<p>
A query a seguir usa o $slice no array comments:
<p>
Ignore o primeiro elemento de forma que o segundo elemento seja o ponto de partida.
Em seguida, retorne três elementos do ponto inicial.
Se o array tiver menos de três elementos após pular, todos os elementos restantes serão retornados.
<p>
db.posts.find( {}, { comments: { $slice: [ 1, 3 ] } } )
<p>
A query retorna os seguintes documentos:
<p>
{
   "_id" : 1,
   "title" : "Bagels are not croissants.",
   "comments" : [ { "comment" : "1. croissants aren't bagels." } ]
}<p>
{
   "_id" : 2,
   "title" : "Coffee please.",
   "comments" : [ { "comment" : "1. tea please" }, { "comment" : "2. iced coffee" }, { "comment" : "3. cappuccino" } ]
}
<p>
Retorne um Array com 3 Elementos após pular o último.
A query a seguir usa o $slice no array comments;
<p>
Pule para trás a partir do primeiro elemento de forma que o último elemento seja o ponto de partida.
Em seguida, retorne três elementos do ponto inicial.
Se o array tiver menos de três elementos após pular, todos os elementos restantes no array serão retornados.
<p>
db.posts.find( {}, { comments: { $slice: [ -1, 3 ] } } )
<p>
A query retorna os seguintes documentos:
<p>
{
   "_id" : 1,
   "title" : "Bagels are not croissants.",
   "comments" : [ { "comment" : "1. croissants aren't bagels." } ]
}
{
   "_id" : 2,
   "title" : "Coffee please.",
   "comments" : [ { "comment" : "4. whatever" } ]
}