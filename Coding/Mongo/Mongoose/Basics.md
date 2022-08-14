- **ODM** (Object Document Mapper) for Mongo (a document database)
- **ODM** is the equivalent of a **ORM**, which is for SQL databases
- It takes documents from the dababase and transform them into JavaScript objects. On the other hand, it also let us turn JavaScript objects into database documents.
- It's an abstraction on top of Mongo Nodejs driver.

### What is a Schema?
- Everything in Mongoose starts with a **Schema**. Each schema maps to a MongoDB collection and defines the shape of the documents within that collection.
- You can think of a Mongoose *schema* as the **configuration object** for a Mongoose *model*.

### What is a Model?
- A mongoose *model* is just a JavaScipt class that mongoose uses to map to a *collection*.
- `const Movie = mongoose.model("Movie", movieSchema);` here we give the *Movie* model the string 'Movie' as the key, mongoose will lowercase and pluralize it to 'movies' and use it as the collection name.
