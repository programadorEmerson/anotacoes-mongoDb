$min : altera o valor do campo para o valor especificado se esse valor especificado é menor do que o atual valor do campo, podem comparar valores de diferentes tipos, utilizando sempre a ordem de comparação BSON.

Considere um cenário em que temos uma collection com três documentos, cada documento possui um atributo id e um atributo campo que é um número inteiro :

db.collection.find();

Resultado:
[
  { _id: 1, campo: 25 },
  { _id: 2, campo: 50 },
  { _id: 3, campo: 100 }
]

vamos aplicar um update utilizando o operador $max . Nosso intuito é atingir todos os documentos com o atributo campo que possuem um valor de no máximo 75 . Nesse caso, o operador não só define o escopo máximo, como também o conteúdo que o campo deve passar a ter :

db.collection.updateMany({}, { $max: { campo: 75 } });
// Atualizando todos os valores do atributo "campo"
// para 75 caso sejam menores

db.collection.find();

Resultado:
[
  { _id: 1, campo: 75 }, // valor anterior: 25
  { _id: 2, campo: 75 }, // valor anterior: 50
  { _id: 3, campo: 100 }, // não encontrou no escopo
]
Portanto, teremos os ids 1 e 2 atingidos, alterando o atributo campo para 75.