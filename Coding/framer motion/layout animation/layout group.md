`layoutGroup` has two use cases:
- Name spacing `layoutId` which allows us to build reusable components that leverage shared layout animation and use those components within the same page
- Grouping together sibling components that perform distinct layout animations that may impact the overall layout on the page so they can adapt gracefully to the new updated layout.

For the second case, this can be fixed by wrapping each sibling components in a `motion` component with the `layout` set to `true` (if the siblings were not `motion` components themselves already), and wrapping all the components we wish to perform a smooth transition when the overall layout changes in a `LayoutGroup`.

## name spacing layoutId
```jsx
const ComponentsWithSharedLayoutAnimation = () => {
  //...

  return (
    //...
    <motion.div layoutId="shared-layout-animation" />
    //...
  );
};

const App = () => (
  <>
    <LayoutGroup id="1">
      <ComponentsWithSharedLayoutAnimation />
    </LayoutGroup>
    <LayoutGroup id="2">
      <ComponentsWithSharedLayoutAnimation />
    </LayoutGroup>
  </>
);
```