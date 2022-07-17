## Instance Methods
- We can define custom methods on documents/instances of Model class
- `productSchema.methods.greet = function(){...}`
- Now on every product object we can do `myProduct.greet()`
```js
 productSchema.methods.greet = function(){
	  console.log('hi')
  }
  const Product = mongoose.model("Product", productSchema);
  const myProduct = new Product({...});
  myProduct.greet();
```
- A few things to keep in mind:
	1. Attach the custom method before associating schema with model
	2. The custom method must be defined using traditional *function* keyword to ensure *this* points to the document object
	3. [mongoose instance methods doc](https://mongoosejs.com/docs/guide.html#methods)
## Static Methods
- We can define custom static methods on collection/Model class itself
- `productSchema.statics.greet = function(){...}`
- Now the model class associated with productSchema will have *greet* method
```js
 productSchema.statics.greet = function(){
	  console.log('hi')
  }
  const Product = mongoose.model("Product", productSchema);
  Product.greet()
```
- In this case *this* keyword in the custome static function points towards the *model class* itself, in our case *Product*
- [mongoose static methods doc](https://mongoosejs.com/docs/guide.html#statics)