## multipart/form-data
```js
fetch('example.com', {
	method:'POST',
	body: new FormData(form) // form is the form element
})

// content-type is automatically multipart/form-data
```

## x-www-form-urlencoded
this just means it's a string of this form 'key1=val1&key2=val2'

```js
fetch('example.com', {
	method:'POST',
	body: new URLSearchParams(new FormData(form))
})

// content-type is automatically x-www-form-urlencoded
```

```html
<form action='example.com' method="post" >
</form>

<!-- enctype/content-type by default is 'x-www-form-urlencoded' -->
```
