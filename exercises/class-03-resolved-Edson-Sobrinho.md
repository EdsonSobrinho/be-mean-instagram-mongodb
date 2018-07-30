# MongoDB - Aula 03 - Exercício
Autor: Edson Sobrinho

## Liste todos Pokemons com a altura **menor que** 0.5;
> var query = {height: {$lt:0.5}}
> query
{ "height" : { "$lt" : 0.5 } }
> db.pokemons.findOne(query)
{
        "_id" : ObjectId("5b4fce81e4354131765d7973"),
        "name" : "Rattata",
        "description" : "Rato boladão",
        "attack" : 25,
        "defense" : 35,
        "height" : 0.3
}

## Liste todos Pokemons com a altura **maior ou igual que** 0.5;

> var query = {height: {$gte:0.5}}
> query
{ "height" : { "$gte" : 0.5 } }
> db.pokemons.find(query)
{ "_id" : ObjectId("5b4fce81e4354131765d796f"), "name" : "Charmeleon", "description" : "Um mini dragão com rabo pegando fogo", "attack" : 80, "defense" : 65, "height" : 1.7 }
{ "_id" : ObjectId("5b4fce81e4354131765d7970"), "name" : "Pikachu", "description" : "Ele é bixão doido e elétrico", "attack" : 50, "defense" : 50, "height" : 1.1 }
{ "_id" : ObjectId("5b4fce81e4354131765d7971"), "name" : "Ivysaur", "description" : "Com dente e uma planta loca na costa", "attack" : 80, "defense" : 80, "height" : 2.5 }
{ "_id" : ObjectId("5b4fce81e4354131765d7972"), "name" : "Blastoise", "description" : "Parece ser uma tartaruga com casco vida loka", "attack" : 85, "defense" : 105, "height" : 1.6 }

## Liste todos Pokemons com a altura **meno ou igual que** 0.5 **E** do tipo grama
> var query = {$and: [{height: {$lte:0.5}}, {type:/grama/}]}
> query
{
        "$and" : [
                {
                        "height" : {
                                "$lte" : 0.5
                        }
                },
                {
                        "type" : /grama/
                }
        ]
}
>  db.pokemons.find(query)
>

## Liste todos Pokemons com a altura **meno ou igual que** 0.5 **ou** name Pikachu

> var query = {$or: [{attack: {$lte:0.5}}, {name:/Pikachu/i}]}
> query
{
        "$or" : [
                {
                        "attack" : {
                                "$lte" : 0.5
                        }
                },
                {
                        "name" : /Pikachu/i
                }
        ]
}
> db.pokemons.find(query)
{ "_id" : ObjectId("5b4fce81e4354131765d7970"), "name" : "Pikachu", "description" : "Ele é bixão doido e elétrico", "attack" : 50, "defense" : 50, "height" : 1.1 }
>

## Liste todos os Pokemons com o attack **MAIOR OU IGUAL QUE **48** **E** com height **MENOR OU IGUAL QUE** 0.5

> var query = {$and: [{attack: {$gte:48}}, {height:{$lte:0.5}}]}
> query
{
        "$and" : [
                {
                        "attack" : {
                                "$gte" : 48
                        }
                },
                {
                        "height" : {
                                "$lte" : 0.5
                        }
                }
        ]
}
> db.pokemons.find(query)
>