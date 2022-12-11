# z-index



```typescript
const makeZIndexes = layers =>
  layers.reduce((agg, layerName, index) => {
    const valueName = `z-index-${layerName}`;
    agg[valueName] = index * 100;

    return agg;
  }, {});

const zIndexes = makeZIndexes(["menu", "modal", "error"]);

// {
//   'z-index-menu': 100,
//   'z-index-modal': 200,
//   'z-index-error': 300,
// }
```
