The `background-position` property in CSS allows you to move a *background image* (or gradient) around within its container.

It has three types of values:
1. Length values (100px 5px)
2. Percentages (100% 5%)
3. Keywords (top right)

**IMPORTANT** the top left of the container and the image is the `(0,0)` point

## length values
`background-position: 100px 5px` means
1. the distance between the *left borders* of the image and the container is *100px*
2. the distance between the *top borders* of the image and the container is *5px*

## Percentages
`background-position: 100% 5%` means
1. the *horizontal 100%* point of the image will be aligned with the *horizontal 100%* point of the container. i.e. the right borders will line up.
2. the *vertical 5%* point of the image will be aligned with the  *vertical 5%* point of the container.

## Keywords
keywords are just shortcuts for percentages. 
*top right* is the same as *100% 0%* (although for the pertentage one horizontal has to be specified first)




