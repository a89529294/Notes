- `@media(max-width: 500px){}` targets screens less than 500px wide.
- `@media(prefers-color-scheme: dark)` 
- ![[Screenshot 2023-04-04 at 3.10.48 PM.png]]
```css
{/* target devices that uses mouse */}
@media (hover:hover) and (pointer:fine){}

{/* target touchscreens */}
@media (hover:none) and (pointer:coarse){}

{/* target keyboard navigation */}
@media (hover:none) and (pointer:none){}
```
One thing to note you can just use the first part `(hover:hover)` to differentiate between *mouse/touch* devices.