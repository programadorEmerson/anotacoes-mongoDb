Esse método remove todos os documentos que satisfaçam o critério de seleção.
O exemplo abaixo remove todos os documentos da coleção inventory em que o atributo status é igual a A :

db.inventory.deleteMany({ status : "A" })
Para remover todos os documentos da coleção, basta não passar nenhum parâmetro para o método deleteMany() :

db.inventory.deleteMany({})