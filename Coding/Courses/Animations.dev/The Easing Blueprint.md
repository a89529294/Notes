## ease-out
This is the curve I use the most in my UI work. It's great for user-initiated interactions like opening a modal as the acceleration at the beginning gives the user a feeling of responsiveness. *I apply this easing for most enter and exit animations.*

## ease-in-out
Starts slowly, speeds up and then slows down towards the end, like a car. This is the most satisfying curve to look at in my opinion. *I use it for anything that is already on the screen and needs to move to a new position, or morph into a new form.*

## ease-in
It's the opposite of `ease-out`, it starts slowly and ends fast. Due to its slow start, *it should generally be avoided as it can make interfaces feel sluggish and less responsive.*

## linear
The only time I would use linear is for a *loading spinner or other continuous animations where there are no interactions*.

## resources
https://easings.co/

## understanding cubic bezier
![[cubic-bezier.png]]
1. p1 is fixed at (0,0), p4 is fixed at (1,1)
2. x-axis represents time, y-axis represents displacement
3. (p2-x, p2-y,p3-x,p3-y)
4. p2 and p3 x coord is restricted between 0 and 1, y coord has no such restriction
5. (0,500,1,500) creates a parabolic curve, (0.5,500,0.5,-500) creates a sinusoidal curve.
6. https://css-tricks.com/advanced-css-animation-using-cubic-bezier/
## custom easing
```css
:root { 
--ease-in-quad: cubic-bezier(.55, .085, .68, .53); 
--ease-in-cubic: cubic-bezier(.550, .055, .675, .19); 
--ease-in-quart: cubic-bezier(.895, .03, .685, .22); 
--ease-in-quint: cubic-bezier(.755, .05, .855, .06); 
--ease-in-expo: cubic-bezier(.95, .05, .795, .035); 
--ease-in-circ: cubic-bezier(.6, .04, .98, .335); 

--ease-out-quad: cubic-bezier(.25, .46, .45, .94); 
--ease-out-cubic: cubic-bezier(.215, .61, .355, 1); 
--ease-out-quart: cubic-bezier(.165, .84, .44, 1); 
--ease-out-quint: cubic-bezier(.23, 1, .32, 1); 
--ease-out-expo: cubic-bezier(.19, 1, .22, 1); 
--ease-out-circ: cubic-bezier(.075, .82, .165, 1); 

--ease-in-out-quad: cubic-bezier(.455, .03, .515, .955); 
--ease-in-out-cubic: cubic-bezier(.645, .045, .355, 1); 
--ease-in-out-quart: cubic-bezier(.77, 0, .175, 1); 
--ease-in-out-quint: cubic-bezier(.86, 0, .07, 1); 
--ease-in-out-expo: cubic-bezier(1, 0, 0, 1); 
--ease-in-out-circ: cubic-bezier(.785, .135, .15, .86);
}
```