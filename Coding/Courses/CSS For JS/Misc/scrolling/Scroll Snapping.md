There are two primary scroll-snap properties:
- `scroll-snap-type` — this controls the direction and precision of the scroll snapping.  
- `scroll-snap-align` — this controls which part of the child we want to snap.
```css
.parent {
    scroll-snap-type: x mandatory; /* x or y, mandatory or proximity. proximity creates a dead zone where it doesn't snap at all */
  }
.child {
    scroll-snap-align: start; /* start or center or end. Lines up the start/center/end of the child and parent. */
  }
```