In CSS, every HTML element has a *containing block*. A containing block is a rectangle that forms the *bounds of the element's container*.

In *Flow layout*, elements are contained by their parents. The size and shape of the parent element's _content box_.

**Absolute elements** can only be contained by _other_ elements using **Positioned layout**. If it cannot find one, the element will be positioned according to the **“initial containing block”**. This is a box the size of the viewport, right at the top of the document.
Unlike in *flow layout*, the padding of the *cotaining block* is ignored by absolutely positioned elements. 

*Positioned elements* are ones with `position` set to one of `relative`, `absolute`, `sticky`, `fixed`. 












