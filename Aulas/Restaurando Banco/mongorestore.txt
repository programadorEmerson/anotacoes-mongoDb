Um banco de dados no servidor usando o comando mongodump e o dump é armazenado no arquivo .bson. Para importar no servidor local usando o comando mongorestore.

É muito simples importar: <br><br>

mongorestore -d db_name -c collection_name file.bson<br>
Caso apenas para uma coleção única Tente isto:<br>

mongorestore --drop -d db_name -c collection_name file.bson<br>
Para restaurar a pasta completa exportada por mongodump:<br><br>

mongorestore -d db_name /path/<br>