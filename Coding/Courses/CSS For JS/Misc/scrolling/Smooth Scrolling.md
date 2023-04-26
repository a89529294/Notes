The simplest way is to set `scroll-behavior: smooth;` for all elements
```css
html {
	scroll-behavior: smooth;
}
```
However, for *client-side rendering* this *causes a scroll issue when the user nagivates to another page*. For instance, when the user is halfway down page 1, and clicks on a link to page 2, the browser will scroll slowly to top of page 2.

In order to prevent this, its better to *not enable global smooth scrolling*, and use `scroll-behavior: smooth;` on a case by case basis using:
```js
function SmoothScrollTo({ id, children }) {

function handleClick(ev) {

// Disable the default anchor-clicking behavior
// of scrolling to the element
ev.preventDefault();

const target = document.querySelector(`#${id}`);

target?.scrollIntoView({

behavior: 'smooth',

});

}

return (

<a

href={`#${id}`}

onClick={handleClick}

>

{children}

</a>

)

}
```