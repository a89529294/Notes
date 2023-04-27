The simplest way is to set `scroll-behavior: smooth;` for all elements
```css
html {
	scroll-behavior: smooth;
}
```
However, for *client-side rendering* this *causes a scroll issue when the user nagivates to another page*. For instance, when the user is halfway down page 1, and clicks on a link to page 2, the browser will scroll slowly to top of page 2.

In order to prevent this, its better to *not enable global smooth scrolling*, and use `scroll-behavior: smooth;` on a case by case basis using:
```tsx
function SmoothScrollTo({ id, children }: { id: string; children: React.ReactNode }) {

function handleClick(ev: React.MouseEvent<HTMLAnchorElement, MouseEvent>) {

// Disable the default anchor-clicking behavior
// of scrolling to the element

ev.preventDefault()

const target = document.querySelector(`#${id}`)

target?.scrollIntoView({

behavior: 'smooth',

})

}

return (

<a href={`#${id}`} onClick={handleClick}>

{children}

</a>

)

}
```
By default this will *scroll to* the element with the targeted id, putting it right at the *top of the viewport*. We can tweak how far away from the viewport by setting `scroll-margin-top: 20px;` on the target element.
