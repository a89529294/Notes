```css
@keyframes spin {
    from {
      transform: rotate(0turn);
    }
    to {
      transform: rotate(1turn);
    }
  }
  
  .spinner {
    animation: spin 1000ms;
    animation-timing-function: linear;
    animation-iteration-count: infinite;
  }
```
- As with `transition`, `animation` requries at least two values, `name` and `duration.
- We can also specify more than two steps using percentages
```css
@keyframes multi-step-spin {
    0% {
      transform: rotate(0turn);
    }
    25% {
      transform: rotate(0.25turn);
    }
    50% {
      transform: rotate(0.5turn);
    }
    75% {
      transform: rotate(0.75turn);
    }
    100% {
      transform: rotate(1turn);
    }
  }
```
- Importantly, _the timing function applies to each step_. We don't get a single ease for the entire animation. 
- We can use `animation-direction` to control the order
```css
@keyframes grow-and-shrink {
    0% {
      transform: scale(1);
    }
    100% {
      transform: scale(1.5);
    }
  }

  .box {
    animation: grow-and-shrink 2000ms;
    animation-timing-function: ease-in-out;
    animation-iteration-count: infinite;
    animation-direction: alternate;
  }
```
- `animation-direction` takes three possible values
	1. `normal` goes from `0` to `100`
	2. `reverse` goes from `100` to `0`
	3. `alternate` ping pongs between `normal` and `reverse`.

## Fill Mode
- The declarations in the `from` and `to` blocks only apply _while the animation is running_. 
- `animation-fill-mode: forwards;`
- Four values (assuming `animation-direction:normal`)
	1. `none` default
	2. `forwards` applies styles in `to/100%` after animation ends
	3. `backwards` applies styles in `from/0%` before animation starts
	4. `both` combies `forwards` & `backwards`
