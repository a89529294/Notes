1. Only *vertical margins* collapse. Technically block-direction margin. We can change this by setting `writing-mode: vertical-lr`, now block-direction becomes horizontal.
2. Margin collapses *only in Flow layout*.
3. Only *adjacent* elements collapse.
4. The *bigger* margin wins.
5. *Nesting doesn't prevent collapsing*. Margin is meant to increase the distance between siblings. It is _not_ meant to increase the gap between a child and its parent's bounding box; that's what padding is for.
	- Margin will always try and increase distance between siblings, **even if it means _transferring_ margin to the parent element**. We can *stop the transferring* by one element having a border/padding, or one element being a scroll container, etc.
	- Margins must be *touching* in order for them to collapse. 
6. Margin can collapse in the same direction.
7. Same rules apply to negative margins, just remember a *bigger* negative margin uses the absolute value.