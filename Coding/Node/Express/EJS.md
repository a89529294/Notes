# Setting up express app to use ejs
- plain *ejs*
```js
app.set("view engine", "ejs");
app.set("views", path.join(__dirname, "views"));
```
- If you want to use *ejs-mate* with *ejs* 
```js
const ejsMate = require("ejs-mate");

app.engine("ejs", ejsMate);
app.set("view engine", "ejs");
app.set("views", path.join(__dirname, "views"));
```

## For a complete example see YelpCamp
