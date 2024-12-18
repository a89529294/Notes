## How does browser know when to line break?
- The browser groups characters into *words*. A word, in this case, is a collection of *characters that can't be broken up*. “https://www.google.com” is a word. So is “kool_kat_99”.
- Words are separated by *breaking characters*. The CSS specification refers to them as *soft wrap opportunities*. Each *whitespace* character is a soft wrap opportunity. So is the *dash* character (`-`).
- What if we want a *non breaking space*? `&nbsp;` What happens is the word to the left of `&nbsp;` will join the word on the right, essentially becoming a new word.

## Dealing with long words
- If a *single word* is too long to fit it a container, it will overflow. Remember the definition, a *word* is a collection of *characters that can't be broken up*.
- This can be overridden using `overflow-wrap: break-word;`.
- The browser algo for breaking words:
	1. line break on the closet *soft wrap opportunity* to the left.
	2. If none exists, text will overflow unless
	3. If `overflow-wrap: break-word` is applied then break on the nearest character to avoid overflowing the container.
- We can tell the browser to add `-` to broken up words by adding `hyphens: auto;` 
- `hyphens: auto` only works if the `lang` attribute is set on the `<html>` tag (and it mainly only works in English).
```css
p {
	overflow-wrap: break-word;
	hyphens: auto;
	/* prefix for safari */
	-webkit-hyphens: auto;
}
```
- Instead of breaking a word up we can also just *truncate* it.
```css
p {
	overflow: hidden;
	text-overflow: ellipsis;
}
```
- If there is a word that cannot fit the container it will be truncated by `overflow: hidden;`. `text-overflow: ellipsis;` adds `...` to indicate that a word has been cut off.
- **IMPORTANT**, in contrast to [`word-break`](https://developer.mozilla.org/en-US/docs/Web/CSS/word-break), `overflow-wrap` will only create a break if an entire word cannot be placed on its own line without overflowing.

## Single line ellipsis
```css
p {
	overflow: hidden;
	text-overflow: ellipsis;
	white-space: nowrap;
}
```
- The reason we need to add `white-space: nowrap;` is browser wraps at *soft wrap opportunities* first then deals with overflow. By setting *nowrap* we tell the browser to deal with overflow right away.

## Multi line ellipsis
```css
p {
    overflow: hidden;
    display: -webkit-box;
    -webkit-box-orient: vertical;
    -webkit-line-clamp: 3;
  }
```
- If the p is a *flex/grid* child make sure to wrap it in a `div` to prevent layout issues.

## Summary
```css
 word-break: break-all;
 hyphens: auto; 
 overflow-wrap: break-word; 
```
- `overflow-wrap` only applies if there is a *single word* that is too long for its container.
- often `word-break` & `hyphens` do the same thing, the only difference is whether the broken up word is denoted by a `-`.