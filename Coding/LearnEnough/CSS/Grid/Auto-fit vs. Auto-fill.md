# Auto-fit vs. Auto-fill

## Setup
```css
.grid-container {
	display:grid;
	grid-template-columns: repeat(auto-fit, minmax(200px,1fr));
							 /*or auto-fill */
}
```
- assuming *grid-container* is about *1100px* wide and there are two *grid items*.

## Common Steps
1. Browser put in as many *columns* as it can, in this case 5.
2. Each column gets an extra *20px* (1100-200 * 5)/5, at this point they are each *220px* wide.

## Auto-fit
3. Because there is less *items*(2) then *columns*(5) the extra 3 columns get collapsed.
4. The two *items* stretch to fit the whole container giving them *550px* width each.

## Auto-fill
3. The extra 3 columns remain, so each column retain their *220px* width.

## Note
The difference between *auto-fit* & *auto-fill* only shows up if there are *less* items then columns.
