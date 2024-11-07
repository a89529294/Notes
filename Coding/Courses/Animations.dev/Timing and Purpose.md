- The average human reaction time to a visual change is 215ms. Thus, we can say that a *duration between 200 and 300ms* should be the sweet spot for most animations.
- *Hover transitions should be faster than other animations*, as we are focused on the element already. Additionally, our eyes are quite sensitive to color changes, so we can use *even shorter duration for color and opacity transitions*.
- Generally, the larger the animation, the longer transition duration.

## modals
- Typically, animations consist of simple enter and exit transitions, for which an *`ease-out` animation with a duration of 200ms is suitable*.

## popovers
- `ease-out` animation with a duration of 150ms

## hover
- I use 150ms for hover transitions.

## purpose
It's easy to start adding animations everywhere. The user then becomes overwhelmed and animations lose their impact. We need to pace them through the experience and add them in places where they enrich the information on the page.
   
*The purpose of most animations should be to add context.*
   
To check whether an animation adds context you can try to describe what benefit it provides to the whole experience. The easier this task is, the more context your animation provides.

## When not to animate
*Users can get annoyed by frequent animations*. That's why, when you think about adding an animation, you should consider how often the user will see it.

Same with *keyboard interactions* which feel more mechanical, animating this type of interactions can make your ui feel slow and disconnected from the user.
