Imagine que você precisa de documentos que tenham apenas um valor que está dentro de um array de objetos, estranho, não é? Mas vamos ver um exemplo:
<p>
db.recipes.insertMany([
  {
    title: "Panqueca Simples",
    ingredients: [
      { name: "Farinha", quantity: 2},
      { name: "Oleo", quantity: 4 },
      { name: "Leite", quantity: 1 },
    ],
  },
  {
    title: "Bolo de Cenoura",
    ingredients: [
      { name: "Farinha", quantity: 2},
      { name: "Oleo", quantity: 1, unit: "xícara" },
      { name: "Ovo", quantity: 3},
      { name: "Cenoura", quantity: 3},
      { name: "Fermento", quantity: 1},
    ],
  },
]);
<p>
Caso você saiba o index exato do elemento em que deseja-se alterar alguma propriedade, pode-se fazer algo como:
<p>
db.recipes.updateOne( { title: "Panqueca Simples" }, { $set: { "ingredients.1.unit": "xícara" } } );
Mas, e se você não soubesse qual posição do array que gostaria de alterar um objeto? Ou melhor, e se quisesse alterar dinamicamente todas as receitas que usam farinha, para usarem farinha integral e que a unit seja xícara? Vamos incrementando alguns exemplos até responder esta última suposição usando o Array Filters .
<p>
db.recipes.updateOne(
  { title: "Panqueca Simples" },
  {
    $set : {
      "ingredients.$[elemento].name": "Farinha Integral",
    },
  },
  { arrayFilters: [ { "elemento.name": "Farinha" } ] },
);
Achamos um documento com title igual a "Panqueca Simples" e atualizamos o objeto com propriedade name igual a "Farinha" do array ingredients , alterando o valor do campo name para "Farinha Integral" .
Agora, vamos adicionar "xícara" ao campo unit do objeto com name igual a "Farinha Integral" !
<p>
db.recipes.updateOne(
  { title: "Panqueca Simples" },
  {
    $set : {
      "ingredients.$[elemento].unit": "xícara",
    },
  },
  { arrayFilters: [ { "elemento.name": "Farinha Integral" } ] },
);
<p>
Precisamos mudar o arrayFilter de "Farinha" para "Farinha Integral" , pois na query anterior alteramos o name desse ingrediente.
Se quiséssemos trocar todos os ingredientes da coleção que são "Farinha" por "Farinha Integral" e colocar "xícara" como valor de unit , poderíamos seguir o seguinte exemplo:
<p>
db.recipes.updateMany( // Passamos de updateOne para updateMany.
  {}, // Retiramos a restrição do título.
  {
    $set : {
      "ingredients.$[elemento].unit": "xícara", // Setamos `unit` como "xícara",
      "ingredients.$[elemento].name": "Farinha Integral", // `name` como "Farinha Integral".
    },
  },
  { arrayFilters: [ { "elemento.name": "Farinha" } ] }, // Filtramos os arrays que o valor da propriedade `name` seja "Farinha".
);
