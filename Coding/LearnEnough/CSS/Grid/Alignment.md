## Properties on the grid container

#### Applicable to grid items
- *justify-items* 
	- aligns grid **items** horizontally within their cells. 
	- `justify-items: stretch;` is the **default**.
- *align-items* 
	- aligns grid **items** vertically within their cells. 
	- `align-items: stretch;` is the **default**.
- *place-items* combines **align-items** and **justify-items** in one property. 
	- `place-items: <align-dir> <justify-dir>`
	- `place-items: center stretch;` 
	- `place-items: center;` is equivalent to `place-items: center center;`

#### Applicable to grid tracks(made up of grid cells)
Note that in order for these properties to work the grid tracks total size in either the horizontal or vertical direction has to be smaller than the grid itself.
- *justify-content* 
	- aligns the **grid tracks** horizontally. 
	- `justify-content: stretch;` is the **default**.
- *align-content* 
	- aligns the **grid tracks** vertically. 
	- `align-content: start;` is the **default**.
- *place-content* acombines **align-content** and **justify-content** in one property.
	- `place-content: <align-dir> <justify-dir>`
	- `place-content: end space-between;`
	- `place-content: center;` is equivalent to `place-content: center center;`

## Properties on the grid items
- *justify-self* 
	- aligns the **grid** item horizontally within its cell. 
	- `justify-self: auto;` is the **default**, which inherits the parents `justify-items` property's value.
- *align-self* 
	- aligns the **grid** item vertically within its cell. 
	- `align-self: auto;` is the **default**, which inherits the parents `align-items` property's value.
- *place-self* combines **align-self** and **justify-self**. 
