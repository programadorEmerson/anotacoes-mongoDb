O operador $pull remove de um array existente todos os elementos com um ou mais valores que atendam à condição especificada.
Removendo todos os itens iguais a um valor especificado
Vamos considerar os seguintes documentos na coleção supplies :
<p>
{
  _id: 1,
  items: [
    {
      "name" : "notepad",
      "price" : 35.29,
      "quantity" : 2,
    },
    {
      "name": "envelopes",
      "price": 19.95,
      "quantity": 8,
    },
    {
      "name": "pens",
      "price": 56.12,
      "quantity": 5,
    },
  ],
},
{
  _id: 2,
  items: [
    {
      "name" : "pencil",
      "price" : 5.29,
      "quantity" : 2,
    },
    {
      "name": "envelopes",
      "price": 19.95,
      "quantity": 8,
    },
    {
      "name": "backpack",
      "price": 80.12,
      "quantity": 1,
    },
    {
      "name": "pens",
      "price": 56.12,
      "quantity": 5,
    },
  ],
}
<p>
Digamos que você queira remover do array items os elementos pens e envelopes :
<p>
db.supplies.updateMany(
  {},
  {
pull: {
      items: {
        name: { $in: ["pens", "envelopes"] },
      },
    },
  },
);
<p>
Na atualização acima, foi utilizado o operador $pull combinado com o operador $in para alterar o array items :
<p>
{
  _id : 1,
  items : [
    {
      "name" : "notepad",
      "price" : 35.29,
      "quantity" : 2,
    },
  ],
},
{
  _id : 2,
  items : [
    {
      "name" : "pencil",
      "price" : 5.29,
      "quantity" : 2,
    },
    {
      "name" : "backpack",
      "price" : 80.12,
      "quantity" : 1,
    },
  ],
}
<p>
Removendo todos os itens que atendem a uma condição diretamente no $pull
Você pode especificar uma condição de remoção diretamente no $pull . Essa condição pode ser, por exemplo, um operador de comparação.
Tendo o seguinte documento na coleção profiles :
<p>
{ _id: 1, votes: [3, 5, 6, 7, 7, 8] }
<p>
db.profiles.updateOne(
  { _id: 1 },
  {
pull: {
      votes: { $gte: 6 },
    },
  },
);
<p>
Depois dessa operação, o documento ficará apenas com valores menores do que 6 no array votes :
<p>
{ _id: 1, votes: [3,  5] }
<p>
Removendo itens em um array de Documentos
Veja a coleção survey com os seguintes documentos:
<p>
{
  _id: 1,
  results: [
    { item: "A", score: 5 },
    { item: "B", score: 8, comment: "Strongly agree" },
  ],
},
{
  _id: 2,
  results: [
    { item: "C", score: 8, comment: "Strongly agree" },
    { item: "B", score: 4 },
  ],
}
<p>
Os documentos têm um array chamado results que armazena documentos.
Com a operação abaixo, você consegue remover do array results todos os elementos que contenham o campo score igual a 8 e o campo item igual a "B" . Ou seja, o documento deve atender a ambas as condições.
<p>
db.survey.updateMany(
  {},
  {
pull: {
      results: { score: 8 , item: "B" },
    },
  },
);
<p>
A expressão do operador $pull aplica as condições a cada elemento do array results como se estivesse no primeiro nível, isso porque os documentos dentro do array results não contêm outros campos com mais arrays . Se isso acontecer, você deve utilizar uma outra abordagem, que será detalhada mais à frente.
Após essa operação, os documentos ficarão assim:
<p>
{
  _id: 1,
  results: [ { "item": "A", "score": 5 } ],
},
{
  _id: 2,
  results: [
    { "item": "C", "score": 8, "comment": "Strongly agree" },
    { "item": "B", "score": 4 },
  ],
}