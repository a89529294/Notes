Assuming we are using shadcn's implementation of tanstack table
## Set a few columns to be a certain width while leaving others to be auto
```tsx 
// data-table.tsx
declare module "@tanstack/react-table" {
	interface ColumnMeta<TData extends RowData, TValue> {
		width: string | number;
	}
}

// or th if not using shadcn
<Tablehead
...
style={{
	width: header.column.columnDef.meta?.width
	? header.column.columnDef.meta?.width
	: "auto",
	}}
>
```
```tsx
// columns.tsx
export const emailsColumns: ColumnDef<(typeof fakeData)[number]>[] = [
	{
		accessorKey: "date",
		header: "發送時間",
		meta: { width: 245 },
	},
	{
		accessorKey: "email",
		header: "信箱",
	},
]
```
Now email column will be auto sized while date column will be set to 245px

## How to make table widen with more columns
```tsx
// min-w-full is to make sure the table spans the parent when the table itself is empty
<table className='w-max min-w-full' />
```

## how to make gap between columns consistent
```tsx
// columns.tsx
export const emailsColumns: ColumnDef<(typeof fakeData)[number]>[] = [
	{
		accessorKey: "date",
		header: ()=><div className='pr-4'>發送時間</div>,
		cell: ()=><div className='pr-4'>...</div>
	}
]
```


## make last cell take up all remaining space
```tsx
<td className='last-of-type:w-full'>...</td>
```