in `calendar.tsx` add the following to `<DayPicker>`
```
captionLayout="dropdown"
fromYear={1900}
toYear={2025}
```
then in `index.css` add
```css
.rdp [aria-hidden="true"] {
	@apply hidden;
}

.rdp-vhidden {
	@apply hidden;
}

select::-webkit-scrollbar {
	display: none;
}
```
