Você pode querer renomear um determinado atributo de um ou mais documentos. Para isso, utilize o operador $rename .
Esse operador recebe um documento contendo o nome atual do campo e o novo nome. Pode ser utilizado com os métodos updateOne() ou updateMany() , e também pode receber um critério de seleção de documentos.
Considerando o seguinte documento da coleção fruits :

use conteudo_trybe;
db.fruits.insertOne(
  { _id: 100, name: "Banana", quantity: 100, inStock: true }
);

A operação a seguir altera o nome do campo name para productName no documento em que o valor do campo name seja igual a Banana :

db.fruits.updateOne(
  { name: "Banana" },
  { $rename: {
      "name": "productName"
    }
  }
);

Agora o documento tem a seguinte estrutura:

{ _id: 100, quantity: 100, inStock: true, productName: 'Banana' }