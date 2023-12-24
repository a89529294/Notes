## make table container scrollable horizontally
## collapse less important columns on smaller screen sizes
## stacking columns
	This is a continuation of the last option. Essentially we add the missing data into another cell.
```jsx
<td className='max-w-0 w-full sm:max-w-none sm:w-auto'>
	{person.name}
	{/* display by default, hide above sm */} 
	<dl className='sm:hidden'>
		<dt className='sr-only'>email</dt>
		<dd className='truncate'>{person.email}</dd>
	</dl>
</td>
```

### notes
The mixture of `display: table-cell`, `max-width: 0`, and `width:100%` on _td_ makes it take up as much space as possible without increasing width of the table when content in that _td_ is too long horizontally. We also need _truncate_ on the content container to add ellipsis instead of letting it overflow.

## choose another layout at smaller screen sizes
For example use double columns at tablet and single column at mobile.