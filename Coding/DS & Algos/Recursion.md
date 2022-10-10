Three parts of recursion
1. pre
2. recurse
3. post

```js
function sum(n){
	if (n === 1) return n
	const out = n + sum(n-1)
	console.log(n)
	return out
}

sum(5)
```

We will actually see the following logged out
```js
2
3
4
5
```

*pre* part is line 2
*recursion* part is line 3
*post* part is line 4