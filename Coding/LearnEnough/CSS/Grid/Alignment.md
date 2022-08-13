### Properties on the grid container
#### Applicable to grid items
- *justify-items* aligns grid **items** horizontally within their 
   cells.
- *align-items* aligns grid **items** vertically within their cells.
- *place-items* combines **align-items** and **justify-items** in one property. 
	- `place-items: <align-dir> <justify-dir>`
    - `place-items: center stretch;` 
	- `place-items: center;` is equivalent to `place-items: center center;`
#### Applicable to grid tracks(made up of grid cells)
Note that in order for these properties to work the grid tracks total size in either the horizontal or vertical direction has to be smaller than the grid itself.
- *justify-content* aligns the **grid tracks** horizontally.
- *align-content* aligns the **grid tracks** vertically.
- *place-content* acombines **align-content** and **justify-content** in one property.
	- `place-content: <align-dir> <justify-dir>`
	- `place-content: end space-between;`
	- `place-content: center;` is equivalent to `place-content: center center;`

### Properties on the grid items
- *justify-self* aligns the **grid** item horizontally within its cell.
- *align-self* aligns the **grid** item vertically within its cell.
- *place-self* combines **align-self** and **justify-self**. 
