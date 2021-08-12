Esse método remove apenas um documento, que deve satisfazer o critério de seleção, mesmo que muitos outros documentos também se enquadrem no critério de seleção. Se nenhum valor for passado como parâmetro, a operação removerá o primeiro documento da coleção.
O exemplo abaixo remove o primeiro documento da coleção inventory em que o atributo status é igual a D :
db.inventory.deleteOne({ status: "D" })

