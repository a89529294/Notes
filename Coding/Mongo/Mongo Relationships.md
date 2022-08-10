## one to few
- Say we have *User* model that can have a few *addresses* associated with each individual *user* document. We can just save the *addresses* in an array in *user*.
```js
const userSchema = new mongoose.Schema({
	first: String,
	last: String,
	address: [
		{
			_id: false,
			street: String,		
			city: String,			
			state: String,			
			country: {			
				type: String,			
				required: true,
			},
		}
	],
});
```
- the `_id:false_` in the *address* is to turn off automatic id generation done by mongoose.

## one to many
- The only difference to the above is we store *ObjectId* in the array instead of the whole thing.
- In this example we have a *farm* that can hold multiple *products*.
```js 
const productSchema = new mongoose.Schema({
	name: String,
	price: Number,
	season: {
	type: String,
	enum: ["Spring", "Summer", "Fall", "Winter"],
	},
});

const farmSchema = new mongoose.Schema({
	name: String,
	city: String,
	products: [{ type: mongoose.Schema.Types.ObjectId, ref: "Product" }],
});

const Product = new mongoose.model("Product", productSchema);
const Farm = new mongoose.model("Farm", farmSchema);

const farm = new Farm({ name: "Full Belly Farms", city: "Guinda, CA" });
const melon = new Product({ name: "Goddess Melon",price:4.99,season:'Summer' });
farm.products.push(melon); 
farm.save();
```
- We can do `farm.products.push(melon)` or `farm.products.push(melon.id)`, mongoose will only save *ObjectId* in the array.
- We can also tell mongoose to *populate* the products array with the whole document instead of just *ObjectId*s.
```js
Farm.findOne({ name: "Full Belly Farms" })
.populate("products")
.then((r) => {
	console.log(r);
});
```

## one to bajilions
- This one is the same as what you would do in a *relational DB*. You save a reference to a parent in the children.
```js
const userSchema = new mongoose.Schema({
	username: String,
	age: Number,
});

const tweetSchema = new mongoose.Schema({
	text: String,
	likes: Number,
	user: { type: mongoose.Schema.Types.ObjectId, ref: "User" },
});

const User = new mongoose.model("User", userSchema);
const Tweet = new mongoose.model("Tweet", tweetSchema);
```