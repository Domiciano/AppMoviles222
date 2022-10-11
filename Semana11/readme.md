# Queries en Firestore


```
data class City(var id:String, var country:String, var city:String, var population:Int)
```

Use estos datos de entrada
```
        Firebase.firestore
            .collection("cities")
            .document("db8608bc")
            .set(
               City("db8608bc", "USA", "San Francisco", 860000)
            )

        Firebase.firestore
            .collection("cities")
            .document("5c5b8399")
            .set(
               City("5c5b8399","USA", "Los Angeles", 3900000)
            )

        Firebase.firestore
            .collection("cities")
            .document("26c1a9c7")
            .set(
               City("26c1a9c7","USA", "Washington, D.C", 680000)
            )

        Firebase.firestore
            .collection("cities")
            .document("26c1a9c7")
            .set(
               City("26c1a9c7","Japan", "Tokio", 9000000)
            )

        Firebase.firestore
            .collection("cities")
            .document("e9df2cb8")
            .set(
               City("e9df2cb8","Mexico", "Ciudad de México", 8800000)
            )
            
        Firebase.firestore
            .collection("cities")
            .document("306f85d2")
            .set(
               City("306f85d2","China", "Beijing", 21500000)
            )
            
        Firebase.firestore
            .collection("cities")
            .document("43dbe338")
            .set(
               City("43dbe338","Colombia", "Bogotá", 7100000)
            )


        Firebase.firestore
            .collection("cities")
            .document("e9211d10")
            .set(
               City("e9211d10","Colombia", "Cali", 2200000)
            )

        Firebase.firestore
            .collection("cities")
            .document("9c8d8090")
            .set(
               City("9c8d8090","Colombia", "Ibagué", 529000)
            )

        Firebase.firestore
            .collection("cities")
            .document("9fef8768")
            .set(
               City("9fef8768","USA", "New York", 8300000)
            )

        Firebase.firestore
            .collection("cities")
            .document("69da425e")
            .set(
               City("69da425e","Argentina", "Buenos Aires", 15100000)
            )


```

### Tenga en cuenta las siguientes reglas

1. Todos los filtros de no igualdad (!=, <, <=, >, >=) sólo pueden ser aplicados a un solo campo en la misma query.

2. Si se usa un filtro de rango (!=, <, <=, >, >=) a un campo, el orden (orderby) sólo puede ser aplicado al mismo campo

3. No se pueden usar DOS o más ArrayContains

4. Puede hacer 2 o más equalTo (==) para encontrar un dato en la db

5. Yo hacer una consulta con filtro de igual y de rango
