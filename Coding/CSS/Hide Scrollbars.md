```css
.container {

overflow-y: scroll;

scrollbar-width: none; /* Firefox */

-ms-overflow-style: none; /* Internet Explorer 10+ */

}

.container::-webkit-scrollbar {

/* WebKit */

width: 0;

height: 0;

}
```

then just apply the *container* class on any element you wish to hide its scrollbar