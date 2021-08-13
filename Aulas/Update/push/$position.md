O $position modificador especifica o local no array em que o $push operador insere elementos. Sem o $position modificador, o $push operador insere elementos no final do array. 
<p>
Para usar o $position modificador, ele deve aparecer com o $each modificador.
<p>
{
  $push: {
    <field>: {
       $each: [ <value1>, <value2>, ... ],
       $position: <num>
    }
  }
}
<p>
<num> indica a posição no array, com base em um índice baseado em zero:
<p>
Um número não negativo corresponde à posição no array, começando do início do array. Se o valor de <num> for maior ou igual ao comprimento do array, o $positio nmodificador não tem efeito e $push adiciona elementos ao final do array.
Um número negativo corresponde à posição no array, contando (mas não incluindo) o último elemento do array. Por exemplo, -1 indica a posição imediatamente antes do último elemento no array. Se você especificar vários elementos na $each matriz, o último elemento adicionado estará na posição especificada a partir do final. Se o valor absoluto de <num> for maior ou igual ao comprimento do array, o $push adiciona elementos ao início do array.
<p>
Exemplos 
Adicionar elementos no início do array
<p>
{ "_id" : 1, "scores" : [ 100 ] }
<p>
A operação a seguir atualiza o campo scores para adicionar os elementos 50, 60 e 70 para o início do array:
<p>
db.students.update(
   { _id: 1 },
   {
     $push: {
        scores: {
           $each: [ 50, 60, 70 ],
           $position: 0
        }
     }
   }
)
<p>
A operação resulta no seguinte documento atualizado:
{ "_id" : 1, "scores" : [  50,  60,  70,  100 ] }
<p>
Adicionar elementos ao meio do array 
Considere uma coleção students que contém o seguinte documento:
<p>
{ "_id" : 1, "scores" : [  50,  60,  70,  100 ] }
<p>
A operação a seguir atualiza o campo scores para adicionar os elementos 20 e 30 no índice 2 do array:
<p>
db.students.update(
   { _id: 1 },
   {
     $push: {
        scores: {
           $each: [ 20, 30 ],
           $position: 2
        }
     }
   }
)
<p>
A operação resulta no seguinte documento atualizado:
{ "_id" : 1, "scores" : [  50,  60,  20,  30,  70,  100 ] }
<p>
$position pode aceitar um valor de índice de array negativo para indicar a posição começando do final, contando a partir (mas não incluindo) o último elemento do array. Por exemplo, -1 indica a posição imediatamente antes do último elemento na matriz.
<p>
Considere uma coleção students que contém o seguinte documento:
<p>
{ "_id" : 1, "scores" : [  50,  60,  20,  30,  70,  100 ] }
<p>
A operação a seguir especifica -2 para $position adicionar 90 na posição dois lugares antes do último elemento e, 80 a seguir, na posição dois lugares antes do último elemento.
<p>
Com uma posição de índice negativa, se você especificar vários elementos na $eachmatriz, o último elemento adicionado estará na posição especificada a partir do final.
<p>
db.students.update(
   { _id: 1 },
   {
     $push: {
        scores: {
           $each: [ 90, 80 ],
           $position: -2
        }
     }
   }
)
<p>
A operação resulta no seguinte documento atualizado:
<p>
{ "_id" : 1, "scores" : [ 50, 60, 20, 30, 90, 80, 70, 100 ] }