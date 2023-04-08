Simply returns a *unique and stable string for a component instance*.
It always start as `:r0:` and increments to `:r1:`.
If there are 5 components using *useId()* you will get `:r0:` to `:r4:`.
