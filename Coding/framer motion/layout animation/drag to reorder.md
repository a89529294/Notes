- `Reorder.Group` where we pass our list of items, the direction of the reorder (horizontal or vertical), and the `onReorder` callback which will return the latest order of the list
- `Reorder.Item` where we pass the value of an item in the list

```jsx
const MyList = () => {
  const [items, setItems] = React.useState(['Item 1', 'Item 2', 'Item 3']);

  return (
    <Reorder.Group
      // Specify the direction of the list (x for horizontal, y for vertical)
      axis="y"
      // Specify the full set of items within your reorder group
      values={items}
      // Callback that passes the newly reordered list of item
      // Note: simply passing a useState setter here is equivalent to
      // doing `(reordereditems) => setItmes(reordereditems)`
      onReorder={setItems}
    >
      {items.map((item) => (
        // /!\ don't forget the value prop!
        <Reorder.Item key={item} value={item}>
          {item}
        </Reorder.Item>
      ))}
    </Reorder.Group>
  );
};
```

### notes
1. If you notice that the item being dragged sometimes get overlapped by its siblings, simply add `position:relative` to each instance of `Reorder.Item`.