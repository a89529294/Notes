- The original draggable should be stationery, i.e. do not apply `transform` styles on it.
- The original draggable should have no styling, instead it should take in the same component passed to `<DragOverlay>`.
- The `<DragOverlay>` component provides a way to render a draggable overlay that is removed from the normal document flow and is positioned relative to the viewport. 
- `<DragOverlay>` should remain mounted at all times.