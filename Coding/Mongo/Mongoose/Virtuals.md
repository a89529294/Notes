- [Virtuals](https://mongoosejs.com/docs/api.html#schema_Schema-virtual) are document properties that you can get and set but that do not get persisted to MongoDB.
```javascript
// define a schema
const personSchema = new Schema({
	first: String,
    last: String
});

// compile our model
const Person = mongoose.model('Person', personSchema);

// create a document
const axl = new Person({
  first: 'Axl', 
  last: 'Rose' 
});

personSchema.virtual('fullName').get(function() {
  return this.first + ' ' + this.last;
});

console.log(axl.fullName) // 'Axl Rose'
console.log(axl.first) // 'Axl'
console.log(axl.last) // 'Rose'
```
