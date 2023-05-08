- grid container (the element with `display: grid;`)
- grid tracks (rows & columns)
- grid items (the elements in the grid container)

## inline direction
- `justify-content` applies to the grid structure, changing the columns widths. Defaults to *stretch*.
- `justify-items` applies to the child elements within each cell, without affecting the shape of the grid. Defaults to *stretch*.
- `justify-self` applies to one child element.

## block direction
- `align-content` applies to the grid structure, changing the rows height. Defaults to *stretch*.
- `align-items` applies to the child elements within each cell, without affecting the shape of the grid. Defaults to *stretch*.
- `align-self` applies to one child element.

## both directions
- `place-content` combines `align-content` and `justify-content`.
- `place-items` combines `align-items` and `justify-items`.
- `place-self` combines `align-self` and `justify-self`.