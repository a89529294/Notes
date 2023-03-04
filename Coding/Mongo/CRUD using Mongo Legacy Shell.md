## Find Collections to Search
Once in a `db` run `show collections`

### Create
- `db.collectionName.insertOne({...})` 
	- If *collectionName* does not exist, one will be created
	- `{...}` is just a JavaScript object
- There is also a [insertMany](https://www.mongodb.com/docs/manual/reference/method/db.collection.insertMany/#mongodb-method-db.collection.insertMany) method

### Read
- `db.collectionName.find()` find all documents in *collectionName* 
- `db.collectionName.find({...})` find all documents matching certain criteria
- `db.collectionName.findOne({...})` find the first document that matches the criteria
- `find` & `findOne` actually return different things. `find` returns a cursor; `fintOne` returns one document or null
- **cursor**: A pointer to the result set of a [query](https://www.mongodb.com/docs/manual/reference/glossary/#std-term-query). Clients can iterate through a cursor to retrieve results.

### Update
- `db.collectionName.updateOne(<filter>,<update>)` [more info](https://www.mongodb.com/docs/manual/tutorial/update-documents/) 
	- `db.dogs.updateOne({name:'Dobby'},{$set:{age:7}})`

### Delete
`db.collectionName.deleteOne({...})` [more info](https://www.mongodb.com/docs/manual/tutorial/remove-documents/)

### Misc.
- Access nested properties use `db.dogs.find({'personality.childFriendly':true})`
- [Operators](https://www.mongodb.com/docs/manual/reference/operator/)
	- `db.dogs.find({age:{$gte:8}})`
	

	