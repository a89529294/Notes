- `docker run --name test-mongo -dit -p 27017:27017 -v mongodbdata:/data/db --rm mongo:latest`
- `docker exec -it test-mongo mongosh`
- `show dbs`
- `use adoption` create and cd into a _database named adoption_
- once inside a database, `db.pets.insertOne({...})` inserts a JavaScript object into a _collection called pets_. 
- `db.pets.help` see commands you can run on pets collection
- `db.help` see command you can run on db

## indexing
- `db.pets.find({name:"Luna"}).explina()` take note of the `queryPlanner.winningPlan` object. If you see _COLLSPAN_, this means the query is done on every document in the collection. _Index_ this if you run this query often.
- `db.pets.createIndex({name:1})` _create index_ on name
- `db.pets.getIndexes`
- _unique index_: `db.members.createIndex( { "user_id": 1 }, { unique: true } )` this makes `user_id` field unique, it cannot contain duplicate values.
- _text index_: `db.pets.createIndex({breed:'text', name:'text'})`, now you can search across breed and name fields. A collection can only have *one text index*, but that index can cover multiple fields. 
- _search text index_:`db.pets.find({$text:{$search: "dog Havanese Luna"}})`. MongoDB performs a logical `OR` search of the terms unless specified as a [phrase](https://www.mongodb.com/docs/manual/reference/operator/query/text/#std-label-text-operator-phrases).
- _ranking text index search_:`db.articles.find( { $text: { $search: "cake" } }).sort( { score: { $meta: "textScore" } } )`

## aggregation
```javascript
db.pets.aggregate([
  {
    $match: {
      type: "dog",
    },
  },
  {
    $bucket: {
      groupBy: "$age",
      boundaries: [0, 3, 9, 15],
      default: "very senior",
      output: {
        count: { $sum: 1 },
      },
    },
  },
  {
    $sort: {
      count: -1,
    },
  },
]);
```
output:
```javascript
[
  { _id: 3, count: 834 },
  { _id: 9, count: 833 },
  { _id: 'very senior', count: 555 },
  { _id: 0, count: 278 }
]
```
