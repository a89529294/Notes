![[scrollbar.svg]]
```css
@media (min-width: 500px) {
html {
  --track-bg-color: hsl(210deg, 15%, 6.25%);
  --thumb-bg-color: hsl(210deg, 10%, 40%);

  /* Official styles (Firefox) */
  scrollbar-color:
    var(--thumb-bg-color)
    var(--track-bg-color);
  scrollbar-width: thin;
}

::-webkit-scrollbar {
  width: 10px;
  background-color: var(--track-bg-color);
}
::-webkit-scrollbar-thumb {
  border-radius: 1000px;
  background-color: var(--thumb-bg-color);
  border: 2px solid var(--track-bg-color);
  /* We can't use `padding` to increase the space around the thumb, but we can fake it with a border that matches the track color */
}
}
```
Note we are *wrapping the scrollbar styles* in a media query *targeting non mobile devices*. Mobile scrollbars are unobtrusive and you can't style IOS mobile scrollbars anyway. 

## Misc
`scrollbar-gutter` controls wherether to reserve space for potential scrollbars. 
```css
* {
	scrollbar-gutter: stable; /* reserve space */
	scrollbar-gutter: auto; /* default, no space reserved */
}
```