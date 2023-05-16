- mongoose entry file
```js


// Import the mongoose module
const mongoose = require("mongoose");

// Set `strictQuery: false` to globally opt into filtering by properties that aren't in the schema
// Included because it removes preparatory warnings for Mongoose 7.
// See: https://mongoosejs.com/docs/migrating_to_6.html#strictquery-is-removed-and-replaced-by-strict
mongoose.set("strictQuery", false);

// Define the database URL to connect to.
const mongoDB = "mongodb://127.0.0.1/my_database";

// Wait for database to connect, logging an error if there is a problem
main().catch((err) => console.log(err));
async function main() {
  await mongoose.connect(mongoDB);
}

```
- mongoose schema & model
```js
// Require Mongoose
const mongoose = require("mongoose");

// Define a schema
const Schema = mongoose.Schema;

const SomeModelSchema = new Schema({
  a_string: String,
  a_date: Date,
});

// The first argument is the singular name of the collection that will be created for your model, and the second argument is the schema you want to use in creating the model.
const SomeModel = mongoose.model("SomeModel", SomeModelSchema);
```
- *virtual properties*: Virtual properties are document properties that you can get and set but that *do not get persisted to MongoDB*. The getters are useful for formatting or combining fields, while setters are useful for de-composing a single value into multiple values for storage.
- *model*: a collection of documents in the database that you can search. It is comparable to a *table* in RDB.
- *model's instance*: individual document that you can save and retrieve.
- *working with models*:
```js
// Create an instance of model SomeModel
const awesome_instance = new SomeModel({ name: "awesome" });

// Save the new model instance asynchronously
await awesome_instance.save();

// you can also do it in one step
await SomeModel.create({ name: "also_awesome" });

```
- _working with related documents_:
```js
const mongoose = require("mongoose");

const Schema = mongoose.Schema;

// The `ref` property tells the schema which model can be assigned to this field.
const authorSchema = Schema({
  name: String,
  stories: [{ type: Schema.Types.ObjectId, ref: "Story" }],
});

const storySchema = Schema({
  author: { type: Schema.Types.ObjectId, ref: "Author" },
  title: String,
});

const Story = mongoose.model("Story", storySchema);
const Author = mongoose.model("Author", authorSchema);

// now we use Story & Author
const bob = new Author({ name: "Bob Smith" });

await bob.save();

// Bob now exists, so lets create a story
const story = new Story({
  title: "Bob goes sledding",
  author: bob._id, // assign the _id from our author Bob. This ID is created by default!
});

await story.save();

// Our story document now has an author referenced by the author document's ID. In order to get the author information in the story results we use populate()
Story.findOne({ title: "Bob goes sledding" })
  .populate("author") // Replace the author id with actual author information in results
  .exec();

```
